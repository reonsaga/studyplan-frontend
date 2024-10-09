<script>
    import { goto } from "$app/navigation";

    export let tasks = [];
    let selectedTask = null;
    let task_priority;
    let is_done;;
    let task_category;
    let task_deadline;
    let task_details;
    let task_uuid;
    function toggleModal(task) {
        selectedTask = task;
        task_priority = task.task_priority;
        is_done = task.is_done;
        task_category = task.task_category;
        task_details = task.task_details;
        task_uuid = task.task_uuid;
        task_deadline = task.task_deadline.split('T')[0];
        const modal = document.getElementById('readonly-modal');
        modal.classList.toggle('hidden');
    }
    const deleteTask = async() => {
        const url = `https://studyplan-api.onrender.com/api/v1/task/${selectedTask.task_uuid.toString()}`
        await fetch(url, {
            method: 'DELETE',
            headers: {
                'Content-Type': 'application/json',
                'Authorization': `Bearer ${sessionStorage.getItem('access_token')}`
            }
        })
        const modal = document.getElementById('readonly-modal');
        modal.classList.toggle('hidden');
        window.location.reload()
    }
    const updateTask = async() => {
        const url = `https://studyplan-api.onrender.com/api/v1/task`
        const payload = {
            task_details: task_details,
            task_priority: task_priority,
            task_category: task_category,
            task_deadline: task_deadline,
            is_done: is_done,
            task_uuid: task_uuid
        }
        await fetch(url, {
            method: 'PATCH',
            headers: {
                'Content-Type': 'application/json',
                'Authorization': `Bearer ${sessionStorage.getItem('access_token')}`
            },
            body: JSON.stringify(payload)
        })
        const modal = document.getElementById('readonly-modal');
        modal.classList.toggle('hidden');
        window.location.reload()
    }
</script>

<div
    class="pt-4 px-4 pb-4 mb-4 bg-white border xl:w-4/6 lg:w-5/6 md:w-5/6 w-full max-w-full border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 space-y-4"
>
    <div class="flex flex-col mb-4">
        <!--Task Details-->
        <div
            class="flex flex-row justify-between items-center"
        >
            <h1 class="font-bold mb-1 text-lg">
                Task Details
            </h1>
            <div class="hidden md:flex space-x-6">
                <!--Tasks Parameters Heading-->
                <h1
                    class="text-md text-lg text-right w-24 md:w-20 lg:w-20"
                >
                    Status
                </h1>

                <h1
                    class="text-md text-lg text-right w-24 md:w-20 lg:w-20"
                >
                    Priority
                </h1>

                <h1
                    class="text-md text-lg text-right w-24 md:w-20 lg:w-20"
                >
                    Category
                </h1>

                <h1
                    class="text-md text-lg text-right w-24 md:w-20 lg:w-20"
                >
                    Deadline
                </h1>
            </div>
        </div>

        <hr class="bg-gray-500" />

        <!-- Task Section -->
         {#each tasks as task}
        <div
            class="flex flex-row items-center justify-between mt-4 mb-4"
        >
            <div class="flex items-center">
                <input
                    id="default-checkbox"
                    type="checkbox"
                    value=""
                    class="w-5 h-5 text-pink-500 bg-gray-100 border-gray-300 rounded focus:ring-pink-500 dark:focus:ring-blue-600 dark:ring-offset-gray-800 focus:ring-2 dark:bg-gray-700 dark:border-gray-600"
                />
                <!--Task Name(button leads to readonly Task Details)-->
                <button
                    data-modal-target="readonly-modal"
                    data-modal-toggle="readonly-modal"
                    type="button"
                    on:click={() => toggleModal(task)}
                    class="text-gray-500 hover:text-pink-500 rounded-lg text-sm text-center ms-4 dark:border-blue-500 dark:text-blue-500 dark:hover:text-white dark:hover:bg-blue-500 dark:focus:ring-blue-800"
                    >{task.task_details.length > 15 ? `${task.task_details.substring(0, 15)}...`
        : task.task_details}</button
                >
            </div>

            <!--Task Parameter Values-->
            <div
                class="hidden md:flex space-x-6 flex-grow justify-end"
            >
                <span
                    class="text-yellow-300 font-bold text-sm w-24 md:w-20 lg:w-20 text-center"
                    >{task.is_done ? "Completed":"In Progress"}</span
                >

                <span
                    class="text-red-500 font-bold text-sm w-24 md:w-20 lg:w-20 text-center"
                    >{task.task_priority}</span
                >

                <span
                    class="text-gray-900 font-bold text-sm w-24 md:w-20 lg:w-20 text-center"
                    >{task.task_category}</span
                >

                <span
                    class="text-pink-500 font-bold text-sm w-24 md:w-20 lg:w-20 text-center"
                    >{task.task_deadline.split("T")[0]}</span
                >
            </div>
        </div>
        <hr class="bg-gray-500" />
        {/each}
    </div>
    {#if selectedTask !== null}
        <hr class="bg-gray-500" />
    {/if}
</div>

<!--Readonly tasks (when clicking a certain task)-->
<div
    id="readonly-modal"
    tabindex="-2"
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
                    View Task
                </h3>
                <button
                    type="button"
                    on:click={() => {
                        const modal = document.getElementById('readonly-modal');
                        modal.classList.toggle('hidden');
                    }}
                    class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm w-8 h-8 inline-flex justify-center items-center dark:hover:bg-gray-600 dark:hover:text-white"
                    data-modal-hide="readonly-modal"
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
                <form class="space-y-4" action="#">
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
                                    checked={task_priority === "High"}
                                    on:click={() => task_priority = "High"}
                                    id="horizontal-list-radio-license"
                                    type="radio"
                                    value=""
                                    name="list-radio"
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
                                    checked={task_priority === "Normal"}
                                    on:click={() => task_priority = "Normal"}
                                    id="horizontal-list-radio-military"
                                    type="radio"
                                    value=""
                                    name="list-radio"
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
                                    checked={task_priority === "Low"}
                                    on:click={() => task_priority = "Low"}
                                    id="horizontal-list-radio-passport"
                                    type="radio"
                                    value=""
                                    name="list-radio"
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
                                placeholder="Select category..."
                                bind:value={task_category}
                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-pink-500 focus:border-pink-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white dark:focus:ring-primary-500 dark:focus:border-primary-500"
                            >
                                <option value="School" selected={task_category === "School"}>School</option>
                                <option value="Work" selected={task_category === "Work"}>Work</option>
                                <option value="Games" selected={task_category === "Games"}>Games</option>
                                <option value="Exercise" selected={task_category === "Exercise"}>Exercise</option>
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
                                datepicker
                                id="default-datepicker"
                                datepicker-orientation="top right"
                                type="text"
                                bind:value={task_deadline}
                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-pink-500 focus:border-pink-500 block w-full pl-10 pr-10 py-2.5 dark:bg-gray-700 dark:border-gray-600 dark:placeholder-gray-400 dark:text-white dark:focus:ring-blue-500 dark:focus:border-blue-500"
                                placeholder="YYYY-MM-DD"
                            />
                        </div>
                    </div>
                    <label
                        for="taskstatus"
                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                        >Task Status</label
                    >
                    <ul
                        class="items-center w-full text-sm font-medium text-gray-900 bg-white border border-gray-200 rounded-lg sm:flex dark:bg-gray-700 dark:border-gray-600 dark:text-white"
                    >
                        <li
                            class="w-full border-b border-gray-200 sm:border-b-0 sm:border-r dark:border-gray-600"
                        >
                            <div class="flex items-center ps-3">
                                <input
                                    checked={is_done}
                                    id="horizontal-list-radio-license"
                                    type="radio"
                                    value=""
                                    on:click={() => is_done=true}
                                    name="taskstat"
                                    class="w-4 h-4 text-green-500 bg-gray-100 border-gray-300 focus:ring-pink-500 dark:focus:ring-blue-600 dark:ring-offset-gray-700 dark:focus:ring-offset-gray-700 focus:ring-2 dark:bg-gray-600 dark:border-gray-500"
                                />
                                <label
                                    for="horizontal-list-radio-license"
                                    class="w-full py-3 ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                                    >Completed
                                </label>
                            </div>
                        </li>
                        <li
                            class="w-full border-b border-gray-200 sm:border-b-0 sm:border-r dark:border-gray-600"
                        >
                            <div class="flex items-center ps-3">
                                <input
                                    checked={!is_done}
                                    on:click={() => is_done=false}
                                    id="horizontal-list-radio-military"
                                    type="radio"
                                    value=""
                                    name="taskstat"
                                    class="w-4 h-4 text-yellow-300 bg-gray-100 border-gray-300 focus:ring-pink-500 dark:focus:ring-blue-600 dark:ring-offset-gray-700 dark:focus:ring-offset-gray-700 focus:ring-2 dark:bg-gray-600 dark:border-gray-500"
                                />
                                <label
                                    for="horizontal-list-radio-military"
                                    class="w-full py-3 ms-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                                    >In Progress</label
                                >
                            </div>
                        </li>
                    </ul>
                    <div class="grid grid-cols-2 gap-4">
                        <div class="flex justify-center">
                            <button
                                type="button"
                                on:click={updateTask}
                                class="w-5/6 text-white border border-pink-500 bg-pink-500 hover:bg-white hover:text-pink-500 hover:bg-blue-800 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
                            >
                                Finish
                            </button>
                        </div>
                        <div class="flex justify-center">
                            <button
                                type="button"
                                on:click={deleteTask}
                                class="w-5/6 text-white border border-red-500 bg-red-500 hover:bg-white hover:text-red-700 hover:border-red-700 hover:bg-blue-800 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
                            >
                                Delete Task
                            </button>
                        </div>
                    </div>
                </form>
            </div>
        </div>
    </div>
</div>
