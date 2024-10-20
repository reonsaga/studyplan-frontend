<script>
    import TaskCard from "./TaskCard.svelte";
    export let tasks;
    let task_priority;
    let task_details;
    let task_category;
    let task_deadline;

    // State for error messages
    let task_priority_error = "";
    let task_details_error = "";
    let task_category_error = "";
    let task_deadline_error = "";
    let general_error = "";

    const createTask = async (event) => {
        event?.preventDefault();

        // Reset error messages
        task_priority_error = "";
        task_details_error = "";
        task_category_error = "";
        task_deadline_error = "";
        general_error = "";

        // Validation checks
        if (!task_priority) {
            task_priority_error = "Please fill out this field";
        }
        if (!task_details) {
            task_details_error = "Please fill out this field";
        }
        if (!task_category) {
            task_category_error = "Please fill out this field";
        }
        if (!task_deadline) {
            task_deadline_error = "Please fill out this field";
        } else if (!/^\d{4}-\d{2}-\d{2}$/.test(task_deadline)) {
            // If the format is incorrect, do not proceed
            return;
        }

        // If there are no errors, proceed with the task creation
        if (
            !task_priority_error &&
            !task_details_error &&
            !task_category_error &&
            !task_deadline_error
        ) {
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
                general_error = "Failed to create task";
                console.error("Failed to create task");
            }
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
                        class="top-0 left-0 flex flex-col items-center space-y-4 w-full"
                    >
                        <!--Searchbar Container-->
                        <div
                            class="pt-4 px-4 pb-4 bg-white border xl:w-4/6 lg:w-5/6 md:w-5/6 w-full border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 space-y-4"
                        >
                            <form class="flex items-center max-w-sm mx-auto">
                                <label for="simple-search" class="sr-only"
                                    >Search</label
                                >
                                <div class="relative w-full">
                                    <div
                                        class="absolute inset-y-0 start-0 flex items-center ps-3 pointer-events-none"
                                    >
                                        <svg
                                            xmlns="http://www.w3.org/2000/svg"
                                            fill="none"
                                            viewBox="0 0 24 24"
                                            stroke-width="1.5"
                                            stroke="gray"
                                            class="size-4"
                                        >
                                            <path
                                                stroke-linecap="round"
                                                stroke-linejoin="round"
                                                d="m21 21-5.197-5.197m0 0A7.5 7.5 0 1 0 5.196 5.196a7.5 7.5 0 0 0 10.607 10.607Z"
                                            />
                                        </svg>
                                    </div>
                                    <input
                                        type="text"
                                        id="simple-search"
                                        class="mt-1 bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-0 focus:ring-pink-500 focus:border-pink-500 block w-full ps-10 p-2.5"
                                        placeholder="Search..."
                                        required
                                    />
                                </div>
                                <button
                                    type="submit"
                                    class="p-2.5 ms-2 text-sm font-medium text-white rounded-lg bg-pink-500 hover:bg-pink-700"
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
                                <div class="flex-shrink-0 ms-2">
                                    <button
                                        data-modal-target="authentication-modal"
                                        data-modal-toggle="authentication-modal"
                                        type="button"
                                        class="text-pink-500 border border-pink-500 bg-white hover:bg-pink-500 hover:text-white font-bold w-10 h-10 rounded-full text-sm p-2.5 text-center inline-flex items-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
                                    >
                                        <svg
                                            xmlns="http://www.w3.org/2000/svg"
                                            fill="none"
                                            viewBox="0 0 24 24"
                                            stroke-width="1.5"
                                            stroke="currentColor"
                                            class="w-5 h-5"
                                        >
                                            <path
                                                stroke-linecap="round"
                                                stroke-linejoin="round"
                                                d="M12 4.5v15m7.5-7.5h-15"
                                            />
                                        </svg>
                                        <span class="sr-only">Add task</span>
                                    </button>
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

<!-- Add task pop-up -->
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
                <form class="space-y-4" on:submit={createTask}>
                    <label
                        for="taskdetails"
                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                    >
                        Task details
                    </label>
                    <textarea
                        id="taskdetails"
                        rows="4"
                        bind:value={task_details}
                        class="block p-2.5 w-full text-sm text-gray-900 bg-gray-50 rounded-lg border border-gray-300 focus:ring-pink-500 focus:border-pink-500 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                        placeholder="Task details..."
                        required
                    ></textarea>

                    <label
                        for="taskprio"
                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                    >
                        Priority
                    </label>
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
                                    required
                                />
                                <label
                                    for="horizontal-list-radio-license"
                                    class="w-full py-3 ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                                    >High</label
                                >
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
                                    required
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
                                    required
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
                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-pink-500 focus:border-pink-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white dark:focus:ring-primary-500 dark:focus:border-primary-500"
                                required
                            >
                                <option value="" disabled selected
                                    >Select category...</option
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
                                type="text"
                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-pink-500 focus:border-pink-500 block w-full pl-10 pr-10 py-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                placeholder="YYYY-MM-DD"
                                required
                            />
                            {#if !/^\d{4}-\d{2}-\d{2}$/.test(task_deadline) && task_deadline}
                                <p
                                    class="absolute text-sm text-gray-500 dark:text-gray-400"
                                    style="top: 100%; left: 0;"
                                >
                                    Please correct format
                                </p>
                            {/if}
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
