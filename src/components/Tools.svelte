<script lang="ts">
    import { fade, slide } from "svelte/transition";
    import { Tooltip, Button } from "flowbite-svelte";
    // Variables for Pomodoro Timer
    let timer: ReturnType<typeof setInterval> | null = null; // Timer variable with proper type
    let totalWorkTime = 25; // Total work time in minutes
    let breakStart = 5; // Time to start the break in minutes
    let breakDuration = 5; // Break duration in minutes
    let workTimeLeft = 0; // Remaining work time in seconds
    let breakTimeLeft = 0; // Remaining break time in seconds
    let isActive = false;
    let isBreak = false; // Track if in break mode
    let statusMessage = "";

    // State to manage the quiz
    let questionInput = "";
    let answerInput = "";
    let quiz = [];
    let userAnswers = [];
    let showQuiz = false;
    let currentQuestionIndex = 0;
    let isQuizComplete = false;
    let correctAnswersCount = 0;

    // Leitner management
    let boxes = [
        { name: "Box 1", cards: [] },
        { name: "Box 2", cards: [] },
        { name: "Box 3", cards: [] },
    ];

    let selectedBoxIndex = null;
    let isQuizStarted = false;
    let currentCardIndex = 0;
    let score = 0;
    let flippedCards = {};
    let newCardFront = "";
    let newCardBack = "";
    let answered = false;
    let showNextCardButton = false;
    let randomizedCards = [];
    let quizCompleted = false;

    // Reactive variable for the current active tab
    let activeTab = "pomodoro"; // Default active tab

    function formatTime(seconds: number) {
        const minutes = Math.floor(seconds / 60);
        const remainingSeconds = seconds % 60;
        return `${String(minutes).padStart(2, "0")}:${String(remainingSeconds).padStart(2, "0")}`;
    }

    function startTimer() {
        if (!isActive) {
            isActive = true;
            workTimeLeft = totalWorkTime * 60; // Initialize work time left
            breakTimeLeft = breakDuration * 60; // Initialize break time left
            statusMessage = "Pomodoro in progress...";

            timer = setInterval(() => {
                if (isBreak) {
                    if (breakTimeLeft > 0) {
                        breakTimeLeft--;
                    } else {
                        clearInterval(timer as number);
                        isActive = false;
                        statusMessage = "Break's over! Resume work.";
                        isBreak = false;
                        startTimer(); // Automatically start the work timer
                    }
                } else {
                    if (workTimeLeft > 0) {
                        workTimeLeft--;
                    } else {
                        clearInterval(timer as number);
                        isActive = false;
                        if (!isBreak) {
                            statusMessage = "Time's up! Take a break.";
                            isBreak = true;
                            startTimer(); // Automatically start the break timer
                        }
                    }
                }

                // Check for break start
                if (
                    !isBreak &&
                    totalWorkTime * 60 - workTimeLeft >= breakStart * 60
                ) {
                    clearInterval(timer as number);
                    isActive = false;
                    statusMessage = "Time's up! Take a break.";
                    isBreak = true;
                    startTimer(); // Automatically start the break timer
                }
            }, 1000);
        }
    }

    function resetTimer() {
        clearInterval(timer as number);
        workTimeLeft = 0; // Reset work time
        breakTimeLeft = 0; // Reset break time
        statusMessage = "New Session?";
        isActive = false;
        isBreak = false; // Reset break status
    }

    // Function to add a question to the quiz
    function addQuestion() {
        if (questionInput && answerInput) {
            quiz = [...quiz, { question: questionInput, answer: answerInput }];
            questionInput = "";
            answerInput = "";
        }
    }

    // Function to remove a specific question
    function removeQuestion(index) {
        quiz = quiz.filter((_, i) => i !== index);
    }

    // Function to reset all questions
    function resetAllQuestions() {
        quiz = [];
    }

    // Function to start the quiz
    function startQuiz() {
        if (quiz.length > 0) {
            showQuiz = true;
            userAnswers = Array(quiz.length).fill("");
            currentQuestionIndex = 0;
            isQuizComplete = false;
            correctAnswersCount = 0;
        }
    }

    // Function to handle answer submission for the current question
    function submitAnswer() {
        if (checkAnswer(currentQuestionIndex)) {
            correctAnswersCount++;
        }
        currentQuestionIndex++;
        if (currentQuestionIndex >= quiz.length) {
            isQuizComplete = true;
        }
    }

    // Function to check if the user's answer is correct
    function checkAnswer(index) {
        return (
            quiz[index].answer.trim().toLowerCase() ===
            userAnswers[index].trim().toLowerCase()
        );
    }

    // Function to reset the quiz and return to question creation
    function resetQuiz() {
        currentQuestionIndex = 0;
        isQuizComplete = false;
        showQuiz = false;
        userAnswers = Array(quiz.length).fill("");
    }

    //Leitner Script
    function selectLeitnerBox(boxIndex) {
        selectedBoxIndex = boxIndex;
    }

    // Fixed addCard function to correctly push data into the selected box
    function addLeitnerCard() {
        if (newCardFront.trim() && newCardBack.trim()) {
            const newCard = {
                id: Date.now(),
                front: newCardFront,
                back: newCardBack,
            };
            boxes[selectedBoxIndex].cards = [
                ...boxes[selectedBoxIndex].cards,
                newCard,
            ];
            newCardFront = "";
            newCardBack = "";
        }
    }

    function flipLeitnerCard(cardId) {
        flippedCards[cardId] = !flippedCards[cardId];
    }

    function startLeitnerQuiz() {
        isQuizStarted = true;
        randomizedCards = shuffleLeitner([...boxes[selectedBoxIndex].cards]);
        currentCardIndex = 0;
        score = 0;
        answered = false;
        showNextCardButton = false;
        quizCompleted = false;
    }

    function shuffleLeitner(array) {
        for (let i = array.length - 1; i > 0; i--) {
            const j = Math.floor(Math.random() * (i + 1));
            [array[i], array[j]] = [array[j], array[i]];
        }
        return array;
    }

    function moveLeitnerCard(isCorrect) {
        const currentCard = randomizedCards[currentCardIndex];
        if (isCorrect) {
            if (selectedBoxIndex < boxes.length - 1) {
                boxes[selectedBoxIndex].cards = boxes[
                    selectedBoxIndex
                ].cards.filter((c) => c.id !== currentCard.id);
                boxes[selectedBoxIndex + 1].cards.push(currentCard);
            }
            score++;
        }
        answered = true;
        showNextCardButton = true;
    }

    function nextLeitnerCard() {
        if (currentCardIndex < randomizedCards.length - 1) {
            currentCardIndex++;
            answered = false;
            showNextCardButton = false;
        } else {
            quizCompleted = true;
            isQuizStarted = false;
        }
    }

    function resetLeitnerQuiz() {
        selectedBoxIndex = null;
        currentCardIndex = 0;
        score = 0;
        answered = false;
        showNextCardButton = false;
        randomizedCards = [];
        quizCompleted = false;
    }

    function getLeitnerCardCount(box) {
        return box.cards.length;
    }
</script>

<div class="flex-1 flex justify-center items-center xl:ml-64">
    <div class="p-4 w-full flex justify-center items-center">
        <!-- Centered wrapper -->
        <div class="mb-4 w-full flex justify-center">
            <!-- Center the content -->
            <div class="relative min-h-screen z-10 w-full">
                <div
                    class="top-4 left-3 flex flex-col items-center space-y-4 w-full"
                >
                    <!-- Tab Navigation -->
                    <div
                        class="mb-4 border-b border-gray-300 dark:border-gray-700"
                    >
                        <ul
                            class="flex flex-wrap -mb-px text-md font-bold text-center"
                            role="tablist"
                        >
                            <li class="me-2" role="presentation">
                                <button
                                    class={`inline-block p-4 border-b-2 rounded-t-lg ${activeTab === "pomodoro" ? "text-pink-500 border-pink-500" : "text-gray-500 border-transparent"}`}
                                    on:click={() => (activeTab = "pomodoro")}
                                >
                                    Pomodoro Timer
                                </button>
                            </li>
                            <li class="me-2" role="presentation">
                                <button
                                    class={`inline-block p-4 border-b-2 rounded-t-lg ${activeTab === "leitner" ? "text-pink-500 border-pink-500" : "text-gray-500 border-transparent"}`}
                                    on:click={() => (activeTab = "leitner")}
                                >
                                    Leitner System
                                </button>
                            </li>
                            <li class="me-2" role="presentation">
                                <button
                                    class={`inline-block p-4 border-b-2 rounded-t-lg ${activeTab === "activeRecall" ? "text-pink-500 border-pink-500" : "text-gray-500 border-transparent"}`}
                                    on:click={() =>
                                        (activeTab = "activeRecall")}
                                >
                                    Active Recall
                                </button>
                            </li>
                        </ul>
                    </div>

                    <!-- Tab Content -->
                    <div id="default-styled-tab-content">
                        <!-- Pomodoro Timer Tab -->
                        {#if activeTab === "pomodoro"}
                            <div class="p-4 rounded-lg">
                                <div
                                    class={` pt-1 px-4 pb-4 w-[380px] md:w-[400px] lg:w-[600px] xl:w-[700px] mx-auto bg-white border border-gray-200 rounded-lg shadow space-y-4 ${isBreak ? "bg-pink-200" : ""}`}
                                >
                                    <div
                                        class="flex justify-between items-center mb-4"
                                    >
                                        <h1 class="text-3xl font-bold">
                                            Pomodoro Timer
                                        </h1>
                                        <Button
                                            class="bg-transparent text-gray-700 hover:bg-transparent focus:ring-0 focus:ring-white "
                                            id="click"
                                            ><svg
                                                xmlns="http://www.w3.org/2000/svg"
                                                fill="none"
                                                viewBox="0 0 24 24"
                                                stroke-width="1.5"
                                                stroke="currentColor"
                                                class="size-6"
                                            >
                                                <path
                                                    stroke-linecap="round"
                                                    stroke-linejoin="round"
                                                    d="M9.879 7.519c1.171-1.025 3.071-1.025 4.242 0 1.172 1.025 1.172 2.687 0 3.712-.203.179-.43.326-.67.442-.745.361-1.45.999-1.45 1.827v.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Zm-9 5.25h.008v.008H12v-.008Z"
                                                />
                                            </svg>
                                        </Button>
                                        <Tooltip
                                            class="mx-2` mr-4 w-full sm:w-40 md:w-80 lg:w-96"
                                            type="dark"
                                            trigger="click"
                                            triggeredBy="#click"
                                            placement="bottom"
                                            >How to use the Pomodoro Technique: <br
                                            />
                                            <hr class="my-2" />
                                            1. Choose a task to focus on.<br />
                                            2. Set a timer for the length of your
                                            work session.<br />
                                            3. Set a timer for when you should take
                                            a break.<br />
                                            4. Start the timer and repeat the work-break-work
                                            session until satisfied.
                                        </Tooltip>
                                    </div>

                                    <hr class="bg-gray-500" />
                                    <!-- Pomodoro Timer content -->
                                    <label
                                        for="totalWorkTime"
                                        class="block mb-2"
                                        >Work duration (minutes):</label
                                    >
                                    <input
                                        id="totalWorkTime"
                                        type="number"
                                        bind:value={totalWorkTime}
                                        min="1"
                                        class="border rounded p-2 mb-4"
                                    />

                                    <label for="breakStart" class="block mb-2"
                                        >Break starts after (minutes):</label
                                    >
                                    <input
                                        id="breakStart"
                                        type="number"
                                        bind:value={breakStart}
                                        min="1"
                                        class="border rounded p-2 mb-4"
                                    />

                                    <label
                                        for="breakDuration"
                                        class="block mb-2"
                                        >Break duration (minutes):</label
                                    >
                                    <input
                                        id="breakDuration"
                                        type="number"
                                        bind:value={breakDuration}
                                        min="1"
                                        class="border rounded p-2 mb-4"
                                    />

                                    <div class="flex flex-col">
                                        <h1 class="text-2xl mb-2">
                                            Work Time:
                                        </h1>
                                        <h1 class="text-2xl text-pink-700">
                                            {formatTime(workTimeLeft)}
                                        </h1>
                                    </div>

                                    <div class="flex flex-col">
                                        <h1 class="text-2xl mb-2">
                                            Break Time:
                                        </h1>
                                        <h1 class="text-2xl text-pink-700">
                                            {formatTime(breakTimeLeft)}
                                        </h1>
                                    </div>

                                    <div
                                        class="w-full bg-white rounded-full h-4 mb-4"
                                    >
                                        <div
                                            class="bg-pink-500 h-full rounded-full"
                                            style="width: {isActive
                                                ? isBreak
                                                    ? (breakTimeLeft /
                                                          (breakDuration *
                                                              60)) *
                                                      100
                                                    : (workTimeLeft /
                                                          (totalWorkTime *
                                                              60)) *
                                                      100
                                                : 0}%"
                                        ></div>
                                    </div>

                                    <div class="flex space-x-4">
                                        <button
                                            on:click={startTimer}
                                            class="btn btn-blue"
                                            disabled={isActive}>Start</button
                                        >
                                        <button
                                            on:click={resetTimer}
                                            class="btn btn-gray"
                                            >Stop and Reset</button
                                        >
                                    </div>

                                    <div class="mt-4">
                                        <p class="text-gray-600">
                                            {statusMessage}
                                        </p>
                                    </div>
                                </div>
                            </div>
                        {/if}

                        <!-- Leitner Box Tab -->
                        {#if activeTab === "leitner"}
                            <div
                                class="pt-1 px-4 pb-4 w-[380px] md:w-[400px] lg:w-[600px] xl:w-[700px] mx-auto bg-white border border-gray-200 rounded-lg shadow space-y-4"
                            >
                                <div
                                    class="flex justify-between items-center mb-4"
                                >
                                    <h1 class="text-3xl font-bold">
                                        Leitner System
                                    </h1>
                                    <Button
                                        class="bg-transparent text-gray-700 hover:bg-transparent focus:ring-0 focus:ring-white "
                                        id="click"
                                        ><svg
                                            xmlns="http://www.w3.org/2000/svg"
                                            fill="none"
                                            viewBox="0 0 24 24"
                                            stroke-width="1.5"
                                            stroke="currentColor"
                                            class="size-6"
                                        >
                                            <path
                                                stroke-linecap="round"
                                                stroke-linejoin="round"
                                                d="M9.879 7.519c1.171-1.025 3.071-1.025 4.242 0 1.172 1.025 1.172 2.687 0 3.712-.203.179-.43.326-.67.442-.745.361-1.45.999-1.45 1.827v.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Zm-9 5.25h.008v.008H12v-.008Z"
                                            />
                                        </svg>
                                    </Button>
                                    <Tooltip
                                        class="mx-2 mr-4 w-full sm:w-40 md:w-80 lg:w-96"
                                        type="dark"
                                        trigger="click"
                                        triggeredBy="#click"
                                        placement="bottom"
                                    >
                                        How to start the Leitner System: <br />
                                        <hr class="my-2" />
                                        1. Choose a topic to study about.<br />
                                        2. Create flashcards with a question and
                                        answer for your topic.<br />
                                        3. Put all of the flashcards in the first
                                        box.<br />
                                        There are 3 boxes:<br />
                                        Box 1: Flashcards that you will answer everyday<br
                                        />
                                        Box 2: Flashcards that you will answer less
                                        often (i.e. every 3 days)<br />
                                        Box 3: Flashcards that you will answer the
                                        least (i.e. once a week) <br />
                                        4. Start the first quiz. <br />
                                        5. Answer the flashcards truthfully.<br
                                        />
                                        6. If you answered a flashcard correctly,
                                        move it to the next box. <br />
                                        7. Once you have placed all the cards in
                                        the third box, answer until you fully get
                                        everything correct.
                                    </Tooltip>
                                </div>
                                <div>
                                    {#if selectedBoxIndex === null}
                                        <div
                                            class="card"
                                            transition:slide={{ duration: 400 }}
                                        >
                                            <h2 class="text-xl mb-2">
                                                Select a Box to Add Cards or
                                                Start a Quiz
                                            </h2>
                                            <div class="button-group">
                                                {#each boxes as box, index}
                                                    <button
                                                        on:click={() =>
                                                            selectLeitnerBox(
                                                                index,
                                                            )}
                                                        class="quiz-button"
                                                    >
                                                        {box.name} ({getLeitnerCardCount(
                                                            box,
                                                        )} cards)
                                                    </button>
                                                {/each}
                                            </div>
                                        </div>
                                    {/if}
                                </div>

                                {#if selectedBoxIndex !== null && !isQuizStarted}
                                    <div
                                        class="card flashcard-input"
                                        transition:slide={{ duration: 400 }}
                                    >
                                        <h2 class="text-xl mb-2">
                                            Add Flashcards to {boxes[
                                                selectedBoxIndex
                                            ].name}
                                        </h2>
                                        <input
                                            type="text"
                                            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-0 focus:border-pink-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white"
                                            placeholder="Question (Front)"
                                            bind:value={newCardFront}
                                        />
                                        <input
                                            type="text"
                                            class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-0 focus:border-pink-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white"
                                            placeholder="Answer (Back)"
                                            bind:value={newCardBack}
                                        />
                                        <button
                                            on:click={addLeitnerCard}
                                            class="quiz-button"
                                            >Add Flashcard</button
                                        >
                                        <p>
                                            Cards in this box: {getLeitnerCardCount(
                                                boxes[selectedBoxIndex],
                                            )}
                                        </p>

                                        {#if getLeitnerCardCount(boxes[selectedBoxIndex]) > 0}
                                            <button
                                                transition:slide={{
                                                    duration: 400,
                                                }}
                                                on:click={startLeitnerQuiz}
                                                class="quiz-button"
                                                >Start Quiz</button
                                            >
                                        {/if}
                                    </div>
                                {/if}

                                {#if isQuizStarted}
                                    <div
                                        class="card quiz-container"
                                        transition:slide={{ duration: 400 }}
                                    >
                                        <h2>
                                            {boxes[selectedBoxIndex].name} Quiz
                                        </h2>
                                        {#if randomizedCards.length > 0}
                                            <div
                                                class="card-container"
                                                transition:slide={{
                                                    duration: 400,
                                                }}
                                            >
                                                <p>
                                                    Flashcard {currentCardIndex +
                                                        1}/{randomizedCards.length}
                                                </p>

                                                <div
                                                    class="flashcard {flippedCards[
                                                        randomizedCards[
                                                            currentCardIndex
                                                        ].id
                                                    ]
                                                        ? 'flipped'
                                                        : ''}"
                                                    on:click={() =>
                                                        flipLeitnerCard(
                                                            randomizedCards[
                                                                currentCardIndex
                                                            ].id,
                                                        )}
                                                >
                                                    <div
                                                        class="flashcard-inner"
                                                    >
                                                        <div
                                                            class="flashcard-front"
                                                        >
                                                            {randomizedCards[
                                                                currentCardIndex
                                                            ].front}
                                                        </div>
                                                        <div
                                                            class="flashcard-back"
                                                        >
                                                            {randomizedCards[
                                                                currentCardIndex
                                                            ].back}
                                                        </div>
                                                    </div>
                                                </div>

                                                {#if !answered}
                                                    <button
                                                        transition:slide={{
                                                            duration: 400,
                                                        }}
                                                        on:click={() =>
                                                            moveLeitnerCard(
                                                                true,
                                                            )}
                                                        class="quiz-button"
                                                    >
                                                        Correct
                                                    </button>
                                                    <button
                                                        transition:slide={{
                                                            duration: 400,
                                                        }}
                                                        on:click={() =>
                                                            moveLeitnerCard(
                                                                false,
                                                            )}
                                                        class="quiz-button"
                                                    >
                                                        Incorrect
                                                    </button>
                                                {/if}

                                                {#if showNextCardButton}
                                                    <button
                                                        transition:slide={{
                                                            duration: 400,
                                                        }}
                                                        on:click={nextLeitnerCard}
                                                        class="quiz-button"
                                                        >Next</button
                                                    >
                                                {/if}
                                            </div>
                                        {/if}
                                    </div>
                                {/if}

                                {#if quizCompleted}
                                    <div
                                        class="card results-container"
                                        transition:slide={{ duration: 400 }}
                                    >
                                        <h2 class="text-xl mb-2">Results</h2>
                                        <p>
                                            You completed the quiz with {score} correct
                                            answers!
                                        </p>
                                        <button
                                            on:click={resetLeitnerQuiz}
                                            class="quiz-button"
                                            >Back to Box Selection</button
                                        >
                                    </div>
                                {/if}
                            </div>
                        {/if}

                        <!-- Active Recall Tab -->
                        {#if activeTab === "activeRecall"}
                            <div class="p-4 rounded-lg">
                                <div
                                    class="pt-1 px-4 pb-4 w-[380px] md:w-[400px] lg:w-[600px] xl:w-[700px] mx-auto bg-white border border-gray-200 rounded-lg shadow space-y-4"
                                >
                                    <!-- Add Questions Section -->
                                    {#if !showQuiz}
                                        <div
                                            transition:slide={{ duration: 200 }}
                                        >
                                            <div
                                                class="flex justify-between items-center mb-4"
                                            >
                                                <h1 class="text-3xl font-bold">
                                                    Active Recall
                                                </h1>
                                                <Button
                                                    class="bg-transparent text-gray-700 hover:bg-transparent focus:ring-0 focus:ring-white "
                                                    id="click"
                                                    ><svg
                                                        xmlns="http://www.w3.org/2000/svg"
                                                        fill="none"
                                                        viewBox="0 0 24 24"
                                                        stroke-width="1.5"
                                                        stroke="currentColor"
                                                        class="size-6"
                                                    >
                                                        <path
                                                            stroke-linecap="round"
                                                            stroke-linejoin="round"
                                                            d="M9.879 7.519c1.171-1.025 3.071-1.025 4.242 0 1.172 1.025 1.172 2.687 0 3.712-.203.179-.43.326-.67.442-.745.361-1.45.999-1.45 1.827v.75M21 12a9 9 0 1 1-18 0 9 9 0 0 1 18 0Zm-9 5.25h.008v.008H12v-.008Z"
                                                        />
                                                    </svg>
                                                </Button>
                                                <Tooltip
                                                    class="mx-2 mr-4 w-full sm:w-40 md:w-80 lg:w-96"
                                                    type="dark"
                                                    trigger="click"
                                                    triggeredBy="#click"
                                                    placement="bottom"
                                                >
                                                    How to use the Active Recall
                                                    Technique: <br />
                                                    <hr class="my-2" />
                                                    1. Choose a topic to study about.<br
                                                    />
                                                    2. Create a mini-quiz with a
                                                    question and answer for your
                                                    topic.<br />
                                                    3. Study your topic and answer
                                                    the quiz while studying truthfully.<br
                                                    />
                                                    4. Repeat until you feel that
                                                    your study session is sufficient.
                                                </Tooltip>
                                            </div>

                                            <input
                                                type="text"
                                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-0 focus:border-pink-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white"
                                                placeholder="Question"
                                                bind:value={questionInput}
                                            />
                                            <input
                                                type="text"
                                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-0 focus:border-pink-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white"
                                                placeholder="Answer"
                                                bind:value={answerInput}
                                            />
                                            <button
                                                type="button"
                                                class="quiz-button text-white bg-pink-500 hover:bg-pink-700 font-medium rounded-full text-sm px-5 py-2.5 text-center me-2 mb-2"
                                                on:click={addQuestion}
                                                >Add Question</button
                                            >
                                            <button
                                                class="quiz-button font-medium rounded-full text-sm px-5 py-2.5 text-center me-2 mb-2"
                                                on:click={startQuiz}
                                                disabled={quiz.length === 0}
                                                >Start Quiz</button
                                            >
                                            <button
                                                class="quiz-button font-medium rounded-full text-sm px-5 py-2.5 text-center me-2 mb-2"
                                                on:click={resetAllQuestions}
                                                disabled={quiz.length === 0}
                                                >Reset All</button
                                            >

                                            <!-- Display the current list of quiz questions -->
                                            <ul>
                                                {#each quiz as { question, answer }, index (index)}
                                                    <li
                                                        transition:slide={{
                                                            duration: 200,
                                                        }}
                                                    >
                                                        Q{index + 1}: {question}
                                                        (Answer: {answer})
                                                        <button
                                                            class="text-white bg-red-500 hover:bg-red-700 font-medium rounded-lg text-sm px-5 py-2.5 text-center ms-2 me-2 mb-2"
                                                            on:click={() =>
                                                                removeQuestion(
                                                                    index,
                                                                )}
                                                            >Remove</button
                                                        >
                                                    </li>
                                                {/each}
                                            </ul>
                                        </div>
                                    {/if}

                                    <!-- Take Quiz Section -->
                                    {#if showQuiz && !isQuizComplete}
                                        <div
                                            transition:slide={{ duration: 200 }}
                                        >
                                            <h1 class="text-3xl font-bold mb-4">
                                                Quiz in Progress
                                            </h1>

                                            <div class="question-section">
                                                <p>
                                                    Q{currentQuestionIndex + 1}: {quiz[
                                                        currentQuestionIndex
                                                    ].question}
                                                </p>
                                                <input
                                                    type="text"
                                                    placeholder="Your answer"
                                                    bind:value={userAnswers[
                                                        currentQuestionIndex
                                                    ]}
                                                />
                                                <button
                                                    class="quiz-button"
                                                    on:click={submitAnswer}
                                                    >Next Question</button
                                                >
                                                <button
                                                    class="quiz-button"
                                                    on:click={resetQuiz}
                                                    >Exit Quiz</button
                                                >
                                            </div>
                                        </div>
                                    {/if}

                                    <!-- Results Section -->
                                    {#if isQuizComplete}
                                        <div
                                            transition:slide={{ duration: 200 }}
                                        >
                                            <h1 class="text-3xl font-bold mb-4">
                                                Quiz Complete!
                                            </h1>
                                            <ul>
                                                {#each quiz as { question, answer }, index}
                                                    <li
                                                        class="mb-2"
                                                        transition:slide={{
                                                            duration: 200,
                                                        }}
                                                    >
                                                        <p class="font-bold">
                                                            Q{index + 1}:
                                                        </p>
                                                        {question} <br />
                                                        <p class="font-bold">
                                                            Your answer:
                                                        </p>
                                                        {userAnswers[index]}
                                                        <br />
                                                        <p class="font-bold">
                                                            Correct answer:
                                                        </p>
                                                        {answer} <br />
                                                        <span
                                                            class={checkAnswer(
                                                                index,
                                                            )
                                                                ? "text-green-500"
                                                                : "text-red-500"}
                                                        >
                                                            {checkAnswer(index)
                                                                ? "Correct"
                                                                : "Incorrect"}
                                                        </span>
                                                    </li>
                                                {/each}
                                            </ul>

                                            <p class="text-2xl font-bold">
                                                Total Score: {correctAnswersCount}
                                                / {quiz.length}
                                            </p>

                                            <button
                                                class="quiz-button"
                                                on:click={resetQuiz}
                                                >Retake Quiz</button
                                            >
                                        </div>
                                    {/if}
                                </div>
                            </div>
                        {/if}
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
