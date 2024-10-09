<script lang="ts">
    let timer: ReturnType<typeof setInterval> | null = null; // Timer variable with proper type
    let totalWorkTime = 25; // Total work time in minutes
    let breakStart = 5; // Time to start the break in minutes
    let breakDuration = 5; // Break duration in minutes
    let workTimeLeft = 0; // Remaining work time in seconds
    let breakTimeLeft = 0; // Remaining break time in seconds
    let isActive = false;
    let isBreak = false; // Track if in break mode
    let statusMessage = "";

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
                    <div
                        class={`pt-4 px-6 py-4 pb-4 bg-white border border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 space-y-4 ${isBreak ? "bg-green-200" : ""}`}
                    >
                        <h1 class="text-4xl font-bold mb-4">Pomodoro Timer</h1>
                        <hr class="bg-gray-500" />

                        <!-- Input for Total Work Time -->
                        <label for="totalWorkTime" class="block mb-2"
                            >Work duration (minutes):</label
                        >
                        <input
                            id="totalWorkTime"
                            type="number"
                            bind:value={totalWorkTime}
                            min="1"
                            class="border rounded p-2 mb-4"
                        />

                        <!-- Input for Break Start Time -->
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

                        <!-- Input for Break Duration -->
                        <label for="breakDuration" class="block mb-2"
                            >Break duration (minutes):</label
                        >
                        <input
                            id="breakDuration"
                            type="number"
                            bind:value={breakDuration}
                            min="1"
                            class="border rounded p-2 mb-4"
                        />

                        <!-- Display Work Time Remaining -->

                        <div class="flex flex-col">
                            <h1 class="text-2xl mb-2">Work Time:</h1>
                            <h1 class="text-2xl text-pink-700">
                                {formatTime(workTimeLeft)}
                            </h1>
                        </div>

                        <!-- Display Break Time Remaining -->
                        <div class="flex flex-col">
                            <h1 class="text-2xl mb-2">Break Time:</h1>
                            <h1 class="text-2xl text-pink-700">
                                {formatTime(breakTimeLeft)}
                            </h1>
                        </div>

                        <!-- Loading Bar -->
                        <div class="w-full bg-white rounded-full h-4 mb-4">
                            <div
                                class="bg-pink-500 h-full rounded-full"
                                style="width: {isActive
                                    ? isBreak
                                        ? (breakTimeLeft /
                                              (breakDuration * 60)) *
                                          100
                                        : (workTimeLeft /
                                              (totalWorkTime * 60)) *
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
                            <button on:click={resetTimer} class="btn btn-gray"
                                >Stop and Reset</button
                            >
                        </div>
                        <div class="mt-4">
                            <p class="text-gray-600">{statusMessage}</p>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
