<script>
    import TaskCard from "./TaskCard.svelte";
    export let tasks;
    let task_priority;
    let task_details;
    let task_category;
    let task_deadline;
    function toggleCreate() {
        const modal = document.getElementById("authentication-modal");
        modal.classList.toggle("hidden");
    }
    const createTask = async (event) => {
        event?.preventDefault();
        if (task_priority && task_details && task_category && task_deadline) {
            const url = "https://studyplan-api.onrender.com/api/v1/task";
            const response = await fetch(url, {
                method: "POST",
                headers: {
                    "Content-Type": "application/json",
                    Authorization: `Bearer ${sessionStorage.getItem("access_token")}`,
                },
                body: JSON.stringify({
                    task_details: task_details,
                    task_priority: task_priority,
                    task_category: task_category,
                    task_deadline: task_deadline,
                    is_done: false,
                }),
            });
            if (response.ok) {
                task_priority = "";
                task_details = "";
                task_category = null;
                task_deadline = "";
                toggleCreate();
                window.location.reload();
            } else {
                console.error("Failed to create task");
            }
        } else {
            console.error("Please fill in all required fields");
            console.log(task_category);
            console.log(task_deadline);
            console.log(task_priority);
            console.log(task_details);
        }
    };
</script>

<!--Overall Parent Container-->
<div class="flex-1 flex justify-center items-center xl:ml-64">
    <div class="p-4 w-full">
        <div class="mb-4 w-full">
            <div class="flex items-center justify-center rounded w-full">
                <div class="relative min-h-screen z-10 w-full">
                    <div
                        class="top-4 left-3 flex flex-col items-center space-y-4 w-full"
                    >
                        <!--Searchbar Container-->
                        <div
                            class="pt-4 px-4 pb-4 bg-white border xl:w-4/6 lg:w-5/6 md:w-5/6 w-full border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 space-y-4"
                        >
                            <form class="max-w-lg mx-auto">
                                <div class="flex">
                                    <label
                                        for="search-dropdown"
                                        class="mb-2 text-sm font-medium text-gray-900 sr-only dark:text-white"
                                        >Your Email</label
                                    >
                                    <button
                                        id="dropdown-button"
                                        data-dropdown-toggle="dropdown"
                                        class="flex-shrink-0 z-10 inline-flex items-center py-2.5 px-4 text-sm font-medium text-center text-gray-900 bg-gray-100 border border-gray-300 rounded-s-lg hover:bg-gray-200 focus:ring-4 focus:outline-none focus:ring-gray-100 dark:bg-gray-700 dark:hover:bg-gray-600 dark:focus:ring-gray-700 dark:text-white dark:border-gray-600"
                                        type="button"
                                        >All categories <svg
                                            class="w-2.5 h-2.5 ms-2.5"
                                            aria-hidden="true"
                                            xmlns="http://www.w3.org/2000/svg"
                                            fill="none"
                                            viewBox="0 0 10 6"
                                        >
                                            <path
                                                stroke="currentColor"
                                                stroke-linecap="round"
                                                stroke-linejoin="round"
                                                stroke-width="2"
                                                d="m1 1 4 4 4-4"
                                            />
                                        </svg></button
                                    >
                                    <div
                                        id="dropdown"
                                        class="z-10 hidden bg-white divide-y divide-gray-100 rounded-lg shadow w-44 dark:bg-gray-700"
                                    >
                                        <ul
                                            class="py-2 text-sm text-gray-700 dark:text-gray-200"
                                            aria-labelledby="dropdown-button"
                                        >
                                            <li>
                                                <button
                                                    type="button"
                                                    class="inline-flex w-full px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-600 dark:hover:text-white"
                                                    >School</button
                                                >
                                            </li>
                                            <li>
                                                <button
                                                    type="button"
                                                    class="inline-flex w-full px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-600 dark:hover:text-white"
                                                    >Work</button
                                                >
                                            </li>
                                            <li>
                                                <button
                                                    type="button"
                                                    class="inline-flex w-full px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-600 dark:hover:text-white"
                                                    >Games</button
                                                >
                                            </li>
                                            <li>
                                                <button
                                                    type="button"
                                                    class="inline-flex w-full px-4 py-2 hover:bg-gray-100 dark:hover:bg-gray-600 dark:hover:text-white"
                                                    >Exercise</button
                                                >
                                            </li>
                                        </ul>
                                    </div>
                                    <div class="relative w-full">
                                        <input
                                            type="search"
                                            id="search-dropdown"
                                            class="block p-2.5 w-full z-20 text-sm text-gray-900 bg-gray-50 rounded-e-lg border-s-gray-50 border-s-2 border border-gray-300 focus:ring-blue-500 focus:border-blue-500 dark:bg-gray-700 dark:border-s-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:border-blue-500"
                                            placeholder="Search tasks..."
                                            required
                                        />
                                        <button
                                            type="submit"
                                            class="absolute top-0 end-0 p-2.5 text-sm font-medium h-full text-white bg-pink-500 rounded-e-lg border border-pink-500 hover:bg-pink-700 focus:ring-4 focus:outline-none focus:ring-blue-300 dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
                                        >
                                            <svg
                                                class="w-4 h-4"
                                                aria-hidden="true"
                                                xmlns="http://www.w3.org/2000/svg"
                                                fill="none"
                                                viewBox="0 0 20 20"
                                            >
                                                <path
                                                    stroke="currentColor"
                                                    stroke-linecap="round"
                                                    stroke-linejoin="round"
                                                    stroke-width="2"
                                                    d="m19 19-4-4m0-7A7 7 0 1 1 1 8a7 7 0 0 1 14 0Z"
                                                />
                                            </svg>
                                            <span class="sr-only">Search</span>
                                        </button>
                                    </div>
                                    <div class="flex mx-4">
                                        <button
                                            data-modal-target="authentication-modal"
                                            data-modal-toggle="authentication-modal"
                                            type="button"
                                            on:click={toggleCreate}
                                            class="text-pink-500 border border-pink-500 bg-white hover:bg-pink-500 hover:text-white hover font-bold rounded-full text-sm p-2.5 text-center inline-flex items-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
                                        >
                                            <svg
                                                xmlns="http://www.w3.org/2000/svg"
                                                fill="none"
                                                viewBox="0 0 24 24"
                                                stroke-width="1.5"
                                                stroke="currentColor"
                                                class="size-5"
                                            >
                                                <path
                                                    stroke-linecap="round"
                                                    stroke-linejoin="round"
                                                    d="M12 4.5v15m7.5-7.5h-15"
                                                />
                                            </svg>

                                            <span class="sr-only">Add task</span
                                            >
                                        </button>
                                    </div>
                                </div>
                            </form>
                        </div>
                        <!--Tasks Card Container-->
                        <TaskCard {tasks} />
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>

<!--Add task pop-up-->
<div
    id="authentication-modal"
    tabindex="-1"
    aria-hidden="true"
    class="hidden overflow-y-auto overflow-x-hidden fixed inset-0 z-50 flex justify-center items-center"
>
    <div class="relative w-full max-w-md md:max-w-lg lg:max-w-xl p-4">
        <!-- Modal content -->
        <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">
            <!-- Modal header -->
            <div
                class="flex items-center justify-between p-4 md:p-5 border-b rounded-t dark:border-gray-600"
            >
                <h3 class="text-xl font-semibold text-gray-900 dark:text-white">
                    Create task
                </h3>
                <button
                    type="button"
                    on:click={toggleCreate}
                    class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm w-8 h-8 inline-flex justify-center items-center dark:hover:bg-gray-600 dark:hover:text-white"
                    data-modal-hide="authentication-modal"
                >
                    <svg
                        class="w-3 h-3"
                        aria-hidden="true"
                        xmlns="http://www.w3.org/2000/svg"
                        fill="none"
                        viewBox="0 0 14 14"
                    >
                        <path
                            stroke="currentColor"
                            stroke-linecap="round"
                            stroke-linejoin="round"
                            stroke-width="2"
                            d="m1 1 6 6m0 0 6 6M7 7l6-6M7 7l-6 6"
                        />
                    </svg>
                    <span class="sr-only">Close modal</span>
                </button>
            </div>

            <!-- Modal body -->
            <div class="p-4 md:p-5">
                <form class="space-y-4" action="#" on:submit={createTask}>
                    <div></div>
                    <label
                        aria-label="disabled input 2"
                        for="taskdetails"
                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                        >Task details</label
                    >
                    <textarea
                        id="taskdetails"
                        rows="4"
                        bind:value={task_details}
                        class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-pink-500 focus:border-pink-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                        placeholder="Task details..."
                    ></textarea>
                    <label
                        for="taskprio"
                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                        >Priority</label
                    >
                    <ul
                        class="items-center w-full text-sm font-medium text-gray-900 bg-white border border-gray-200 rounded-lg sm:flex dark:bg-gray-700 dark:border-gray-600 dark:text-white"
                    >
                        <li
                            class="w-full border-b border-gray-200 sm:border-b-0 sm:border-r dark:border-gray-600"
                        >
                            <div class="flex items-center ps-3">
                                <input
                                    id="horizontal-list-radio-license"
                                    type="radio"
                                    value=""
                                    name="list-radio"
                                    on:click={() => {
                                        task_priority = "High";
                                    }}
                                    class="w-4 h-4 text-red-500 bg-gray-100 border-gray-300 focus:ring-pink-500 dark:focus:ring-blue-600 dark:ring-offset-gray-700 dark:focus:ring-offset-gray-700 focus:ring-2 dark:bg-gray-600 dark:border-gray-500"
                                />
                                <label
                                    for="horizontal-list-radio-license"
                                    class="w-full py-3 ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                                    >High
                                </label>
                            </div>
                        </li>
                        <li
                            class="w-full border-b border-gray-200 sm:border-b-0 sm:border-r dark:border-gray-600"
                        >
                            <div class="flex items-center ps-3">
                                <input
                                    id="horizontal-list-radio-military"
                                    type="radio"
                                    value=""
                                    name="list-radio"
                                    on:click={() => {
                                        task_priority = "Normal";
                                    }}
                                    class="w-4 h-4 text-yellow-300 bg-gray-100 border-gray-300 focus:ring-pink-500 dark:focus:ring-blue-600 dark:ring-offset-gray-700 dark:focus:ring-offset-gray-700 focus:ring-2 dark:bg-gray-600 dark:border-gray-500"
                                />
                                <label
                                    for="horizontal-list-radio-military"
                                    class="w-full py-3 ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                                    >Normal</label
                                >
                            </div>
                        </li>
                        <li class="w-full dark:border-gray-600">
                            <div class="flex items-center ps-3">
                                <input
                                    id="horizontal-list-radio-passport"
                                    type="radio"
                                    value=""
                                    name="list-radio"
                                    on:click={() => {
                                        task_priority = "Low";
                                    }}
                                    class="w-4 h-4 text-green-500 bg-gray-100 border-gray-300 focus:ring-pink-500 dark:focus:ring-pink-600 dark:ring-offset-gray-700 dark:focus:ring-offset-gray-700 focus:ring-2 dark:bg-gray-600 dark:border-gray-500"
                                />
                                <label
                                    for="horizontal-list-radio-passport"
                                    class="w-full py-3 ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                                    >Low</label
                                >
                            </div>
                        </li>
                    </ul>

                    <div class="grid grid-cols-2 gap-4">
                        <div class="col-span-2 sm:col-span-1">
                            <label
                                for="category"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                            >
                                Category
                            </label>
                            <select
                                id="category"
                                bind:value={task_category}
                                placeholder="Select category..."
                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-pink-500 focus:border-pink-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white dark:focus:ring-primary-500 dark:focus:border-primary-500"
                            >
                                <option value="School">School</option>
                                <option value="Work">Work</option>
                                <option value="Games">Games</option>
                                <option value="Exercise">Exercise</option>
                            </select>
                        </div>

                        <div class="relative col-span-2 sm:col-span-1">
                            <label
                                for="deadline"
                                class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                            >
                                Deadline
                            </label>
                            <input
                                bind:value={task_deadline}
                                id="default-datepicker"
                                datepicker-orientation="top right"
                                type="text"
                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-pink-500 focus:border-pink-500 block w-full pl-10 pr-10 py-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                placeholder="YYYY-MM-DD"
                            />
                        </div>
                    </div>

                    <button
                        type="submit"
                        class="w-full text-white border border-pink-500 bg-pink-500 hover:bg-white hover:text-pink-500 hover:bg-blue-800 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
                    >
                        Submit Task
                    </button>
                </form>
            </div>
        </div>
    </div>
</div>
