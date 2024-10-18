<script>
    import { goto } from "$app/navigation";
    function toggleSidebar() {
        const sidebar = document.getElementById("sidebar-multi-level-sidebar");
        sidebar.classList.toggle("-translate-x-full");

        // Add or remove the event listener for outside click when the sidebar is open
        if (!sidebar.classList.contains("-translate-x-full")) {
            document.addEventListener("click", handleClickOutsideSidebar);
        } else {
            document.removeEventListener("click", handleClickOutsideSidebar);
        }
    }
    function toggleDropdown() {
        const dropdown = document.getElementById("dropdown-example");
        dropdown.classList.toggle("hidden");
    }
    function handleClickOutsideSidebar(event) {
        const sidebar = document.getElementById("sidebar-multi-level-sidebar");
        const toggleButton = document.querySelector(".p-2.mt-2.ms-3"); // Your toggle button

        // Check if the click is outside the sidebar and not on the toggle button
        if (
            !sidebar.contains(event.target) &&
            !toggleButton.contains(event.target)
        ) {
            sidebar.classList.add("-translate-x-full");
            document.removeEventListener("click", handleClickOutsideSidebar);
        }
    }
    function logout() {
        sessionStorage.removeItem("access_token");
        goto("./");
    }
</script>

<!--Mobile Mode Buttons-->
<div class="items-center flex flex-row">
    <button
        on:click={toggleSidebar}
        type="button"
        class="inline-flex items-center p-2 mt-2 ms-3 text-sm text-gray-500 rounded-lg xl:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600"
    >
        <span class="sr-only">Open sidebar</span>
        <svg
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
                d="M3.75 6.75h16.5M3.75 12h16.5m-16.5 5.25h16.5"
            />
        </svg>
    </button>

    <button
        id="dropdownNotificationButton"
        data-dropdown-toggle="dropdownNotification"
        class="block lg:hidden flex items-end p-2 mt-2 me-3 text-sm text-gray-500 rounded-lg xl:hidden hover:bg-gray-100 focus:outline-none focus:ring-2 focus:ring-gray-200 dark:text-gray-400 dark:hover:bg-gray-700 dark:focus:ring-gray-600 ml-auto"
        type="button"
    >
        <span class="sr-only">Notifications</span>
        <svg
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
                d="M14.857 17.082a23.848 23.848 0 0 0 5.454-1.31A8.967 8.967 0 0 1 18 9.75V9A6 6 0 0 0 6 9v.75a8.967 8.967 0 0 1-2.312 6.022c1.733.64 3.56 1.085 5.455 1.31m5.714 0a24.255 24.255 0 0 1-5.714 0m5.714 0a3 3 0 1 1-5.714 0"
            />
        </svg>
    </button>
</div>

<!--Sidebar Start-->
<aside
    id="sidebar-multi-level-sidebar"
    class="fixed top-0 left-0 z-40 w-64 h-screen transition-transform -translate-x-full xl:translate-x-0"
    aria-label="Sidebar"
>
    <div class="h-full px-3 py-4 overflow-y-auto bg-gray-50 dark:bg-gray-800">
        <ul class="space-y-2 font-medium">
            <li>
                <h1
                    class="flex items-center p-2 text-pink-500 text-2xl italic font-bold rounded-lg dark:text-white group"
                >
                    StudyPlan
                </h1>
            </li>

            <!--Home Button-->
            <li>
                <button
                    type="button"
                    on:click={() => goto("/home")}
                    class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700 group"
                >
                    <svg
                        viewBox="0 0 24 24"
                        class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white"
                        aria-hidden="true"
                        xmlns="http://www.w3.org/2000/svg"
                        fill="currentColor"
                    >
                        <path
                            d="M11.47 3.841a.75.75 0 0 1 1.06 0l8.69 8.69a.75.75 0 1 0 1.06-1.061l-8.689-8.69a2.25 2.25 0 0 0-3.182 0l-8.69 8.69a.75.75 0 1 0 1.061 1.06l8.69-8.689Z"
                        />
                        <path
                            d="m12 5.432 8.159 8.159c.03.03.06.058.091.086v6.198c0 1.035-.84 1.875-1.875 1.875H15a.75.75 0 0 1-.75-.75v-4.5a.75.75 0 0 0-.75-.75h-3a.75.75 0 0 0-.75.75V21a.75.75 0 0 1-.75.75H5.625a1.875 1.875 0 0 1-1.875-1.875v-6.198a2.29 2.29 0 0 0 .091-.086L12 5.432Z"
                        />
                    </svg>

                    <span class="flex-1 ms-3 whitespace-nowrap">Home</span>
                </button>
            </li>
            <!--Tasks Button-->
            <li>
                <button
                    type="button"
                    on:click={() => goto("./tasks")}
                    class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700 group"
                >
                    <svg
                        viewBox="0 0 24 24"
                        class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white"
                        aria-hidden="true"
                        xmlns="http://www.w3.org/2000/svg"
                        fill="currentColor"
                    >
                        <path
                            fill-rule="evenodd"
                            d="M1.5 5.625c0-1.036.84-1.875 1.875-1.875h17.25c1.035 0 1.875.84 1.875 1.875v12.75c0 1.035-.84 1.875-1.875 1.875H3.375A1.875 1.875 0 0 1 1.5 18.375V5.625ZM21 9.375A.375.375 0 0 0 20.625 9h-7.5a.375.375 0 0 0-.375.375v1.5c0 .207.168.375.375.375h7.5a.375.375 0 0 0 .375-.375v-1.5Zm0 3.75a.375.375 0 0 0-.375-.375h-7.5a.375.375 0 0 0-.375.375v1.5c0 .207.168.375.375.375h7.5a.375.375 0 0 0 .375-.375v-1.5Zm0 3.75a.375.375 0 0 0-.375-.375h-7.5a.375.375 0 0 0-.375.375v1.5c0 .207.168.375.375.375h7.5a.375.375 0 0 0 .375-.375v-1.5ZM10.875 18.75a.375.375 0 0 0 .375-.375v-1.5a.375.375 0 0 0-.375-.375h-7.5a.375.375 0 0 0-.375.375v1.5c0 .207.168.375.375.375h7.5ZM3.375 15h7.5a.375.375 0 0 0 .375-.375v-1.5a.375.375 0 0 0-.375-.375h-7.5a.375.375 0 0 0-.375.375v1.5c0 .207.168.375.375.375Zm0-3.75h7.5a.375.375 0 0 0 .375-.375v-1.5A.375.375 0 0 0 10.875 9h-7.5A.375.375 0 0 0 3 9.375v1.5c0 .207.168.375.375.375Z"
                            clip-rule="evenodd"
                        />
                    </svg>

                    <span class="flex-1 ms-3 whitespace-nowrap">Tasks</span>
                    <span
                        class="inline-flex items-center justify-center w-3 h-3 p-3 ms-3 text-sm font-medium text-pink-800 bg-pink-100 rounded-full dark:bg-blue-900 dark:text-blue-300"
                        >3</span
                    >
                </button>
            </li>
            <!--Study Tools Button-->
            <li>
                <button
                    type="button"
                    on:click={() => goto("./tools")}
                    class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700 group"
                >
                    <svg
                        viewBox="0 0 24 24"
                        class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white"
                        aria-hidden="true"
                        xmlns="http://www.w3.org/2000/svg"
                        fill="currentColor"
                    >
                        <path
                            d="M11.25 4.533A9.707 9.707 0 0 0 6 3a9.735 9.735 0 0 0-3.25.555.75.75 0 0 0-.5.707v14.25a.75.75 0 0 0 1 .707A8.237 8.237 0 0 1 6 18.75c1.995 0 3.823.707 5.25 1.886V4.533ZM12.75 20.636A8.214 8.214 0 0 1 18 18.75c.966 0 1.89.166 2.75.47a.75.75 0 0 0 1-.708V4.262a.75.75 0 0 0-.5-.707A9.735 9.735 0 0 0 18 3a9.707 9.707 0 0 0-5.25 1.533v16.103Z"
                        />
                    </svg>

                    <span class="flex-1 ms-3 whitespace-nowrap"
                        >Study Tools</span
                    >
                </button>
            </li>
            <!--Games Button-->
            <li>
                <button
                    type="button"
                    on:click={() => goto("./engage")}
                    class="flex items-center p-2 text-gray-900 rounded-lg dark:text-white hover:bg-gray-100 dark:hover:bg-gray-700 group"
                >
                    <svg
                        viewBox="0 0 24 24"
                        class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white"
                        aria-hidden="true"
                        xmlns="http://www.w3.org/2000/svg"
                        fill="currentColor"
                    >
                        <path
                            d="M11.25 5.337c0-.355-.186-.676-.401-.959a1.647 1.647 0 0 1-.349-1.003c0-1.036 1.007-1.875 2.25-1.875S15 2.34 15 3.375c0 .369-.128.713-.349 1.003-.215.283-.401.604-.401.959 0 .332.278.598.61.578 1.91-.114 3.79-.342 5.632-.676a.75.75 0 0 1 .878.645 49.17 49.17 0 0 1 .376 5.452.657.657 0 0 1-.66.664c-.354 0-.675-.186-.958-.401a1.647 1.647 0 0 0-1.003-.349c-1.035 0-1.875 1.007-1.875 2.25s.84 2.25 1.875 2.25c.369 0 .713-.128 1.003-.349.283-.215.604-.401.959-.401.31 0 .557.262.534.571a48.774 48.774 0 0 1-.595 4.845.75.75 0 0 1-.61.61c-1.82.317-3.673.533-5.555.642a.58.58 0 0 1-.611-.581c0-.355.186-.676.401-.959.221-.29.349-.634.349-1.003 0-1.035-1.007-1.875-2.25-1.875s-2.25.84-2.25 1.875c0 .369.128.713.349 1.003.215.283.401.604.401.959a.641.641 0 0 1-.658.643 49.118 49.118 0 0 1-4.708-.36.75.75 0 0 1-.645-.878c.293-1.614.504-3.257.629-4.924A.53.53 0 0 0 5.337 15c-.355 0-.676.186-.959.401-.29.221-.634.349-1.003.349-1.036 0-1.875-1.007-1.875-2.25s.84-2.25 1.875-2.25c.369 0 .713.128 1.003.349.283.215.604.401.959.401a.656.656 0 0 0 .659-.663 47.703 47.703 0 0 0-.31-4.82.75.75 0 0 1 .83-.832c1.343.155 2.703.254 4.077.294a.64.64 0 0 0 .657-.642Z"
                        />
                    </svg>

                    <span class="flex-1 ms-3 whitespace-nowrap">Engage</span>
                </button>
            </li>
            <!--Settings Dropdown Button-->
            <li>
                <button
                    type="button"
                    on:click={toggleDropdown}
                    class="flex items-center w-full p-2 text-gray-900 transition duration-75 rounded-lg group hover:bg-gray-100 dark:text-white dark:hover:bg-gray-700"
                >
                    <svg
                        viewBox="0 0 24 24"
                        class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 group-hover:text-gray-900 dark:text-gray-400 dark:group-hover:text-white"
                        aria-hidden="true"
                        xmlns="http://www.w3.org/2000/svg"
                        fill="currentColor"
                    >
                        <path
                            fill-rule="evenodd"
                            d="M11.078 2.25c-.917 0-1.699.663-1.85 1.567L9.05 4.889c-.02.12-.115.26-.297.348a7.493 7.493 0 0 0-.986.57c-.166.115-.334.126-.45.083L6.3 5.508a1.875 1.875 0 0 0-2.282.819l-.922 1.597a1.875 1.875 0 0 0 .432 2.385l.84.692c.095.078.17.229.154.43a7.598 7.598 0 0 0 0 1.139c.015.2-.059.352-.153.43l-.841.692a1.875 1.875 0 0 0-.432 2.385l.922 1.597a1.875 1.875 0 0 0 2.282.818l1.019-.382c.115-.043.283-.031.45.082.312.214.641.405.985.57.182.088.277.228.297.35l.178 1.071c.151.904.933 1.567 1.85 1.567h1.844c.916 0 1.699-.663 1.85-1.567l.178-1.072c.02-.12.114-.26.297-.349.344-.165.673-.356.985-.57.167-.114.335-.125.45-.082l1.02.382a1.875 1.875 0 0 0 2.28-.819l.923-1.597a1.875 1.875 0 0 0-.432-2.385l-.84-.692c-.095-.078-.17-.229-.154-.43a7.614 7.614 0 0 0 0-1.139c-.016-.2.059-.352.153-.43l.84-.692c.708-.582.891-1.59.433-2.385l-.922-1.597a1.875 1.875 0 0 0-2.282-.818l-1.02.382c-.114.043-.282.031-.449-.083a7.49 7.49 0 0 0-.985-.57c-.183-.087-.277-.227-.297-.348l-.179-1.072a1.875 1.875 0 0 0-1.85-1.567h-1.843ZM12 15.75a3.75 3.75 0 1 0 0-7.5 3.75 3.75 0 0 0 0 7.5Z"
                            clip-rule="evenodd"
                        />
                    </svg>

                    <span
                        class="flex-1 ms-3 text-left rtl:text-right whitespace-nowrap"
                        >Settings</span
                    >
                    <svg
                        class="w-3 h-3"
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
                    </svg>
                </button>
                <ul id="dropdown-example" class="hidden py-2 space-y-2">
                    <li>
                        <a
                            href="#"
                            class="flex items-center w-full p-2 text-gray-900 transition duration-75 rounded-lg pl-11 group hover:bg-gray-100 dark:text-white dark:hover:bg-gray-700"
                        >
                            <svg
                                class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white"
                                aria-hidden="true"
                                xmlns="http://www.w3.org/2000/svg"
                                fill="currentColor"
                            >
                                <path
                                    d="M18.75 12.75h1.5a.75.75 0 0 0 0-1.5h-1.5a.75.75 0 0 0 0 1.5ZM12 6a.75.75 0 0 1 .75-.75h7.5a.75.75 0 0 1 0 1.5h-7.5A.75.75 0 0 1 12 6ZM12 18a.75.75 0 0 1 .75-.75h7.5a.75.75 0 0 1 0 1.5h-7.5A.75.75 0 0 1 12 18ZM3.75 6.75h1.5a.75.75 0 1 0 0-1.5h-1.5a.75.75 0 0 0 0 1.5ZM5.25 18.75h-1.5a.75.75 0 0 1 0-1.5h1.5a.75.75 0 0 1 0 1.5ZM3 12a.75.75 0 0 1 .75-.75h7.5a.75.75 0 0 1 0 1.5h-7.5A.75.75 0 0 1 3 12ZM9 3.75a2.25 2.25 0 1 0 0 4.5 2.25 2.25 0 0 0 0-4.5ZM12.75 12a2.25 2.25 0 1 1 4.5 0 2.25 2.25 0 0 1-4.5 0ZM9 15.75a2.25 2.25 0 1 0 0 4.5 2.25 2.25 0 0 0 0-4.5Z"
                                />
                            </svg>

                            <span class="flex-1 ms-3 whitespace-nowrap"
                                >General</span
                            ></a
                        >
                    </li>
                    <li>
                        <a
                            href="#"
                            class="flex items-center w-full p-2 text-gray-900 transition duration-75 rounded-lg pl-11 group hover:bg-gray-100 dark:text-white dark:hover:bg-gray-700"
                        >
                            <svg
                                viewBox="0 0 24 24"
                                class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 dark:text-gray-400 group-hover:text-gray-900 dark:group-hover:text-white"
                                aria-hidden="true"
                                xmlns="http://www.w3.org/2000/svg"
                                fill="currentColor"
                            >
                                <path
                                    fill-rule="evenodd"
                                    d="M18.685 19.097A9.723 9.723 0 0 0 21.75 12c0-5.385-4.365-9.75-9.75-9.75S2.25 6.615 2.25 12a9.723 9.723 0 0 0 3.065 7.097A9.716 9.716 0 0 0 12 21.75a9.716 9.716 0 0 0 6.685-2.653Zm-12.54-1.285A7.486 7.486 0 0 1 12 15a7.486 7.486 0 0 1 5.855 2.812A8.224 8.224 0 0 1 12 20.25a8.224 8.224 0 0 1-5.855-2.438ZM15.75 9a3.75 3.75 0 1 1-7.5 0 3.75 3.75 0 0 1 7.5 0Z"
                                    clip-rule="evenodd"
                                />
                            </svg>

                            <span class="flex-1 ms-3 whitespace-nowrap"
                                >Profile</span
                            ></a
                        >
                    </li>
                    <li>
                        <button
                            type="button"
                            on:click={() => logout()}
                            class="flex items-center w-full p-2 text-gray-900 transition duration-75 rounded-lg pl-11 group hover:bg-gray-100 dark:text-white dark:hover:bg-gray-700"
                        >
                            <svg
                                viewBox="0 0 24 24"
                                class="flex-shrink-0 w-5 h-5 text-gray-500 transition duration-75 group-hover:text-gray-900 dark:text-gray-400 dark:group-hover:text-white"
                                aria-hidden="true"
                                xmlns="http://www.w3.org/2000/svg"
                                fill="currentColor"
                            >
                                <path
                                    fill-rule="evenodd"
                                    d="M7.5 3.75A1.5 1.5 0 0 0 6 5.25v13.5a1.5 1.5 0 0 0 1.5 1.5h6a1.5 1.5 0 0 0 1.5-1.5V15a.75.75 0 0 1 1.5 0v3.75a3 3 0 0 1-3 3h-6a3 3 0 0 1-3-3V5.25a3 3 0 0 1 3-3h6a3 3 0 0 1 3 3V9A.75.75 0 0 1 15 9V5.25a1.5 1.5 0 0 0-1.5-1.5h-6Zm10.72 4.72a.75.75 0 0 1 1.06 0l3 3a.75.75 0 0 1 0 1.06l-3 3a.75.75 0 1 1-1.06-1.06l1.72-1.72H9a.75.75 0 0 1 0-1.5h10.94l-1.72-1.72a.75.75 0 0 1 0-1.06Z"
                                    clip-rule="evenodd"
                                />
                            </svg>

                            <span class="flex-1 ms-3 whitespace-nowrap"
                                >Logout</span
                            ></button
                        >
                    </li>
                </ul>
            </li>
        </ul>
    </div>
</aside>

<!--Mobile Mode Notifications-->
<div
    id="dropdownNotification"
    aria-labelledby="dropdownNotificationButton"
    class="z-50 hidden card pt-1 px-4 pb-4 bg-white border sm:w-5/6 lg:w-80 xl:w-80 border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 space-y-4"
>
    <div>
        <div class="flex items-center">
            <svg
                xmlns="http://www.w3.org/2000/svg"
                fill="none"
                viewBox="0 0 24 24"
                stroke-width="1.5"
                stroke="currentColor"
                class="size-10 pe-2"
            >
                <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    d="M14.857 17.082a23.848 23.848 0 0 0 5.454-1.31A8.967 8.967 0 0 1 18 9.75V9A6 6 0 0 0 6 9v.75a8.967 8.967 0 0 1-2.312 6.022c1.733.64 3.56 1.085 5.455 1.31m5.714 0a24.255 24.255 0 0 1-5.714 0m5.714 0a3 3 0 1 1-5.714 0"
                />
            </svg>

            <h1
                class="text-2xl font-bold text-gray-900 dark:text-white text-start mt-2 mb-2"
            >
                Events
            </h1>
        </div>
        <hr class="bg-gray-500" />
        <h1 class="text-lg font-semibold text-gray-900 dark:text-white">
            October 1, 2024
        </h1>

        <ol class="mt-3 divide-y divider-gray-200 dark:divide-gray-700">
            <li>
                <a
                    href="#"
                    class="items-center block p-3 sm:flex hover:bg-gray-100 dark:hover:bg-gray-700"
                >
                    <div class="text-gray-600 dark:text-gray-400">
                        <div class="text-base font-normal">
                            <span
                                class="font-medium text-gray-900 dark:text-white"
                                >Computerman31</span
                            >
                            commented on
                            <span
                                class="font-medium text-gray-900 dark:text-white"
                                >BonnieG's</span
                            >
                            post in
                            <span
                                class="font-medium text-pink-500 dark:text-white"
                            >
                                How to start with Flowbite library</span
                            >
                        </div>
                        <div class="text-sm font-normal">
                            "Thanks for the tips man"
                        </div>
                    </div>
                </a>
            </li>
            <li>
                <a
                    href="#"
                    class="items-center block p-3 sm:flex hover:bg-gray-100 dark:hover:bg-gray-700"
                >
                    <div class="text-gray-600 dark:text-gray-400">
                        <div class="text-base font-normal">
                            <span
                                class="font-medium text-gray-900 dark:text-white"
                                >Computerman31</span
                            >
                            commented on
                            <span
                                class="font-medium text-gray-900 dark:text-white"
                                >BonnieG's</span
                            >
                            post in
                            <span
                                class="font-medium text-pink-500 dark:text-white"
                            >
                                How to start with Flowbite library</span
                            >
                        </div>
                        <div class="text-sm font-normal">
                            "Thanks for the tips man"
                        </div>
                    </div>
                </a>
            </li>
        </ol>
    </div>
    <hr class="bg-gray-500" />
    <div>
        <h1 class="text-lg font-semibold text-gray-900 dark:text-white">
            October 2, 2024
        </h1>
        <ol class="mt-3 divide-y divider-gray-200 dark:divide-gray-700">
            <li>
                <a
                    href="#"
                    class="items-center block p-3 sm:flex hover:bg-gray-100 dark:hover:bg-gray-700"
                >
                    <div class="text-gray-600 dark:text-gray-400">
                        <div class="text-base font-normal">
                            <span
                                class="font-medium text-gray-900 dark:text-white"
                                >Computerman31</span
                            >
                            commented on
                            <span
                                class="font-medium text-gray-900 dark:text-white"
                                >BonnieG's</span
                            >
                            post in
                            <span
                                class="font-medium text-pink-500 dark:text-white"
                            >
                                How to start with Flowbite library</span
                            >
                        </div>
                        <div class="text-sm font-normal">
                            "Thanks for the tips man"
                        </div>
                    </div>
                </a>
            </li>
            <li>
                <a
                    href="#"
                    class="items-center block p-3 sm:flex hover:bg-gray-100 dark:hover:bg-gray-700"
                >
                    <div class="text-gray-600 dark:text-gray-400">
                        <div class="text-base font-normal">
                            <span
                                class="font-medium text-gray-900 dark:text-white"
                                >Computerman31</span
                            >
                            commented on
                            <span
                                class="font-medium text-gray-900 dark:text-white"
                                >BonnieG's</span
                            >
                            post in
                            <span
                                class="font-medium text-pink-500 dark:text-white"
                            >
                                How to start with Flowbite library</span
                            >
                        </div>
                        <div class="text-sm font-normal">
                            "Thanks for the tips man"
                        </div>
                    </div>
                </a>
            </li>
        </ol>
    </div>
</div>
