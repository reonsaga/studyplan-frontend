<!--Overall Parent Containers-->
<div class="flex-1 flex justify-center items-center xl:ml-64">
    <div class="p-4">
        <div class="mb-4">
            <div class="flex items-center justify-center rounded">
                <div class="relative min-h-screen z-10">
                    <div
                        class="top-4 left-3 flex flex-col items-center space-y-4"
                    >
                        <!--Card Container-->
                        <div
                            class="pt-4 px-4 pb-4 bg-white border xl:w-4/6 lg:w-5/6 md:w-5/6 w-full border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 space-y-4"
                        >
                            <!--Searchbar Container-->
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
                                            placeholder="Search forums..."
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
                                            data-modal-target="forumcreation-modal"
                                            data-modal-toggle="forumcreation-modal"
                                            type="button"
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

                        <!--Posts Container-->
                        <div
                            class="pt-4 px-4 pb-4 mb-4 bg-white border xl:w-4/6 lg:w-5/6 md:w-5/6 border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 space-y-4"
                        >
                            <div class="flex items-center">
                                <svg
                                    xmlns="http://www.w3.org/2000/svg"
                                    viewBox="0 0 24 24"
                                    fill="currentColor"
                                    class="size-6"
                                >
                                    <path
                                        fill-rule="evenodd"
                                        d="M18.685 19.097A9.723 9.723 0 0 0 21.75 12c0-5.385-4.365-9.75-9.75-9.75S2.25 6.615 2.25 12a9.723 9.723 0 0 0 3.065 7.097A9.716 9.716 0 0 0 12 21.75a9.716 9.716 0 0 0 6.685-2.653Zm-12.54-1.285A7.486 7.486 0 0 1 12 15a7.486 7.486 0 0 1 5.855 2.812A8.224 8.224 0 0 1 12 20.25a8.224 8.224 0 0 1-5.855-2.438ZM15.75 9a3.75 3.75 0 1 1-7.5 0 3.75 3.75 0 0 1 7.5 0Z"
                                        clip-rule="evenodd"
                                    />
                                </svg>
                                <span class="ms-2 text-gray-900 text-sm">
                                    BonnieG
                                </span>
                                <span class="mx-2 text-gray-500 text-sm">
                                    —
                                </span>
                                <span class="ms-2 text-gray-500 text-sm">
                                    4 hours ago
                                </span>
                            </div>
                            <h1 class="font-bold text-lg">
                                How to start with Flowbite Library
                            </h1>
                            <div class="flex flex-col items-center">
                                <img
                                    class="forum-image mx-4 mb-4 rounded-lg"
                                    src="/src/lib/images/sample-forum.jpg"
                                    alt="image description"
                                />

                                Lorem ipsum dolor sit amet consectetur
                                adipisicing elit. Nam illo dignissimos adipisci,
                                repellat alias eos. Rem possimus minus ullam
                                tempora dicta eligendi nesciunt debitis
                                architecto obcaecati facere! Accusamus, ut sed.
                            </div>
                            <hr class="bg-gray-500" />

                            <div class="flex items-center">
                                <button>
                                    <svg
                                        xmlns="http://www.w3.org/2000/svg"
                                        fill="none"
                                        viewBox="0 0 24 24"
                                        stroke-width="1.5"
                                        stroke="currentColor"
                                        class="size-6 stroke-gray-500"
                                    >
                                        <path
                                            stroke-linecap="round"
                                            stroke-linejoin="round"
                                            d="M6.633 10.25c.806 0 1.533-.446 2.031-1.08a9.041 9.041 0 0 1 2.861-2.4c.723-.384 1.35-.956 1.653-1.715a4.498 4.498 0 0 0 .322-1.672V2.75a.75.75 0 0 1 .75-.75 2.25 2.25 0 0 1 2.25 2.25c0 1.152-.26 2.243-.723 3.218-.266.558.107 1.282.725 1.282m0 0h3.126c1.026 0 1.945.694 2.054 1.715.045.422.068.85.068 1.285a11.95 11.95 0 0 1-2.649 7.521c-.388.482-.987.729-1.605.729H13.48c-.483 0-.964-.078-1.423-.23l-3.114-1.04a4.501 4.501 0 0 0-1.423-.23H5.904m10.598-9.75H14.25M5.904 18.5c.083.205.173.405.27.602.197.4-.078.898-.523.898h-.908c-.889 0-1.713-.518-1.972-1.368a12 12 0 0 1-.521-3.507c0-1.553.295-3.036.831-4.398C3.387 9.953 4.167 9.5 5 9.5h1.053c.472 0 .745.556.5.96a8.958 8.958 0 0 0-1.302 4.665c0 1.194.232 2.333.654 3.375Z"
                                        />
                                    </svg>
                                </button>
                                <span class="ms-2 text-gray-400 text-sm">
                                    7.2k
                                </span>
                                <button>
                                    <svg
                                        xmlns="http://www.w3.org/2000/svg"
                                        fill="none"
                                        viewBox="0 0 24 24"
                                        stroke-width="1.5"
                                        stroke="currentColor"
                                        class="ms-2 size-6 stroke-gray-500"
                                    >
                                        <path
                                            stroke-linecap="round"
                                            stroke-linejoin="round"
                                            d="M7.498 15.25H4.372c-1.026 0-1.945-.694-2.054-1.715a12.137 12.137 0 0 1-.068-1.285c0-2.848.992-5.464 2.649-7.521C5.287 4.247 5.886 4 6.504 4h4.016a4.5 4.5 0 0 1 1.423.23l3.114 1.04a4.5 4.5 0 0 0 1.423.23h1.294M7.498 15.25c.618 0 .991.724.725 1.282A7.471 7.471 0 0 0 7.5 19.75 2.25 2.25 0 0 0 9.75 22a.75.75 0 0 0 .75-.75v-.633c0-.573.11-1.14.322-1.672.304-.76.93-1.33 1.653-1.715a9.04 9.04 0 0 0 2.86-2.4c.498-.634 1.226-1.08 2.032-1.08h.384m-10.253 1.5H9.7m8.075-9.75c.01.05.027.1.05.148.593 1.2.925 2.55.925 3.977 0 1.487-.36 2.89-.999 4.125m.023-8.25c-.076-.365.183-.75.575-.75h.908c.889 0 1.713.518 1.972 1.368.339 1.11.521 2.287.521 3.507 0 1.553-.295 3.036-.831 4.398-.306.774-1.086 1.227-1.918 1.227h-1.053c-.472 0-.745-.556-.5-.96a8.95 8.95 0 0 0 .303-.54"
                                        />
                                    </svg>
                                </button>
                                <button>
                                    <svg
                                        xmlns="http://www.w3.org/2000/svg"
                                        fill="none"
                                        viewBox="0 0 24 24"
                                        stroke-width="1.5"
                                        stroke="currentColor"
                                        class="size-6 ms-6 stroke-gray-500"
                                    >
                                        <path
                                            stroke-linecap="round"
                                            stroke-linejoin="round"
                                            d="M8.625 9.75a.375.375 0 1 1-.75 0 .375.375 0 0 1 .75 0Zm0 0H8.25m4.125 0a.375.375 0 1 1-.75 0 .375.375 0 0 1 .75 0Zm0 0H12m4.125 0a.375.375 0 1 1-.75 0 .375.375 0 0 1 .75 0Zm0 0h-.375m-13.5 3.01c0 1.6 1.123 2.994 2.707 3.227 1.087.16 2.185.283 3.293.369V21l4.184-4.183a1.14 1.14 0 0 1 .778-.332 48.294 48.294 0 0 0 5.83-.498c1.585-.233 2.708-1.626 2.708-3.228V6.741c0-1.602-1.123-2.995-2.707-3.228A48.394 48.394 0 0 0 12 3c-2.392 0-4.744.175-7.043.513C3.373 3.746 2.25 5.14 2.25 6.741v6.018Z"
                                        />
                                    </svg>
                                </button>
                                <span class="ms-2 text-gray-400 text-sm">
                                    359
                                </span>
                            </div>
                        </div>

                        <div
                            class="pt-4 px-4 pb-4 mb-4 bg-white border xl:w-4/6 lg:w-5/6 md:w-5/6 border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 space-y-4"
                        >
                            <div class="flex items-center">
                                <svg
                                    xmlns="http://www.w3.org/2000/svg"
                                    viewBox="0 0 24 24"
                                    fill="currentColor"
                                    class="size-6"
                                >
                                    <path
                                        fill-rule="evenodd"
                                        d="M18.685 19.097A9.723 9.723 0 0 0 21.75 12c0-5.385-4.365-9.75-9.75-9.75S2.25 6.615 2.25 12a9.723 9.723 0 0 0 3.065 7.097A9.716 9.716 0 0 0 12 21.75a9.716 9.716 0 0 0 6.685-2.653Zm-12.54-1.285A7.486 7.486 0 0 1 12 15a7.486 7.486 0 0 1 5.855 2.812A8.224 8.224 0 0 1 12 20.25a8.224 8.224 0 0 1-5.855-2.438ZM15.75 9a3.75 3.75 0 1 1-7.5 0 3.75 3.75 0 0 1 7.5 0Z"
                                        clip-rule="evenodd"
                                    />
                                </svg>
                                <span class="ms-2 text-gray-900 text-sm">
                                    BonnieG
                                </span>
                                <span class="mx-2 text-gray-500 text-sm">
                                    —
                                </span>
                                <span class="ms-2 text-gray-500 text-sm">
                                    4 hours ago
                                </span>
                            </div>
                            <h1 class="font-bold text-lg">
                                How to start with Flowbite Library
                            </h1>
                            <div class="flex flex-col items-center">
                                <img
                                    class="forum-image mx-4 mb-4 rounded-lg"
                                    src="/src/lib/images/sample-forum.jpg"
                                    alt="image description"
                                />

                                Lorem ipsum dolor sit amet consectetur
                                adipisicing elit. Nam illo dignissimos adipisci,
                                repellat alias eos. Rem possimus minus ullam
                                tempora dicta eligendi nesciunt debitis
                                architecto obcaecati facere! Accusamus, ut sed.
                            </div>
                            <hr class="bg-gray-500" />

                            <div class="flex items-center">
                                <button>
                                    <svg
                                        xmlns="http://www.w3.org/2000/svg"
                                        fill="none"
                                        viewBox="0 0 24 24"
                                        stroke-width="1.5"
                                        stroke="currentColor"
                                        class="size-6 stroke-gray-500"
                                    >
                                        <path
                                            stroke-linecap="round"
                                            stroke-linejoin="round"
                                            d="M6.633 10.25c.806 0 1.533-.446 2.031-1.08a9.041 9.041 0 0 1 2.861-2.4c.723-.384 1.35-.956 1.653-1.715a4.498 4.498 0 0 0 .322-1.672V2.75a.75.75 0 0 1 .75-.75 2.25 2.25 0 0 1 2.25 2.25c0 1.152-.26 2.243-.723 3.218-.266.558.107 1.282.725 1.282m0 0h3.126c1.026 0 1.945.694 2.054 1.715.045.422.068.85.068 1.285a11.95 11.95 0 0 1-2.649 7.521c-.388.482-.987.729-1.605.729H13.48c-.483 0-.964-.078-1.423-.23l-3.114-1.04a4.501 4.501 0 0 0-1.423-.23H5.904m10.598-9.75H14.25M5.904 18.5c.083.205.173.405.27.602.197.4-.078.898-.523.898h-.908c-.889 0-1.713-.518-1.972-1.368a12 12 0 0 1-.521-3.507c0-1.553.295-3.036.831-4.398C3.387 9.953 4.167 9.5 5 9.5h1.053c.472 0 .745.556.5.96a8.958 8.958 0 0 0-1.302 4.665c0 1.194.232 2.333.654 3.375Z"
                                        />
                                    </svg>
                                </button>
                                <span class="ms-2 text-gray-400 text-sm">
                                    7.2k
                                </span>
                                <button>
                                    <svg
                                        xmlns="http://www.w3.org/2000/svg"
                                        fill="none"
                                        viewBox="0 0 24 24"
                                        stroke-width="1.5"
                                        stroke="currentColor"
                                        class="ms-2 size-6 stroke-gray-500"
                                    >
                                        <path
                                            stroke-linecap="round"
                                            stroke-linejoin="round"
                                            d="M7.498 15.25H4.372c-1.026 0-1.945-.694-2.054-1.715a12.137 12.137 0 0 1-.068-1.285c0-2.848.992-5.464 2.649-7.521C5.287 4.247 5.886 4 6.504 4h4.016a4.5 4.5 0 0 1 1.423.23l3.114 1.04a4.5 4.5 0 0 0 1.423.23h1.294M7.498 15.25c.618 0 .991.724.725 1.282A7.471 7.471 0 0 0 7.5 19.75 2.25 2.25 0 0 0 9.75 22a.75.75 0 0 0 .75-.75v-.633c0-.573.11-1.14.322-1.672.304-.76.93-1.33 1.653-1.715a9.04 9.04 0 0 0 2.86-2.4c.498-.634 1.226-1.08 2.032-1.08h.384m-10.253 1.5H9.7m8.075-9.75c.01.05.027.1.05.148.593 1.2.925 2.55.925 3.977 0 1.487-.36 2.89-.999 4.125m.023-8.25c-.076-.365.183-.75.575-.75h.908c.889 0 1.713.518 1.972 1.368.339 1.11.521 2.287.521 3.507 0 1.553-.295 3.036-.831 4.398-.306.774-1.086 1.227-1.918 1.227h-1.053c-.472 0-.745-.556-.5-.96a8.95 8.95 0 0 0 .303-.54"
                                        />
                                    </svg>
                                </button>
                                <button>
                                    <svg
                                        xmlns="http://www.w3.org/2000/svg"
                                        fill="none"
                                        viewBox="0 0 24 24"
                                        stroke-width="1.5"
                                        stroke="currentColor"
                                        class="size-6 ms-6 stroke-gray-500"
                                    >
                                        <path
                                            stroke-linecap="round"
                                            stroke-linejoin="round"
                                            d="M8.625 9.75a.375.375 0 1 1-.75 0 .375.375 0 0 1 .75 0Zm0 0H8.25m4.125 0a.375.375 0 1 1-.75 0 .375.375 0 0 1 .75 0Zm0 0H12m4.125 0a.375.375 0 1 1-.75 0 .375.375 0 0 1 .75 0Zm0 0h-.375m-13.5 3.01c0 1.6 1.123 2.994 2.707 3.227 1.087.16 2.185.283 3.293.369V21l4.184-4.183a1.14 1.14 0 0 1 .778-.332 48.294 48.294 0 0 0 5.83-.498c1.585-.233 2.708-1.626 2.708-3.228V6.741c0-1.602-1.123-2.995-2.707-3.228A48.394 48.394 0 0 0 12 3c-2.392 0-4.744.175-7.043.513C3.373 3.746 2.25 5.14 2.25 6.741v6.018Z"
                                        />
                                    </svg>
                                </button>
                                <span class="ms-2 text-gray-400 text-sm">
                                    359
                                </span>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>

<!--Forum Creation Pop-up-->
<div
    id="forumcreation-modal"
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
                    Create Post
                </h3>
                <button
                    type="button"
                    class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm w-8 h-8 inline-flex justify-center items-center dark:hover:bg-gray-600 dark:hover:text-white"
                    data-modal-hide="forumcreation-modal"
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
                    <div></div>
                    <label
                        aria-label="disabled input 2"
                        for="taskdetails"
                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                        >Post Title</label
                    >
                    <input
                        type="text"
                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-0 focus:border-pink-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white"
                        name="ftitle"
                        id="ftitle"
                    />
                    <label
                        for="postform"
                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                        >Post Content</label
                    >
                    <form>
                        <div
                            class="w-full mb-4 border border-gray-200 rounded-lg bg-gray-50"
                        >
                            <div
                                class="flex items-center justify-between px-3 py-2 border-b"
                            >
                                <div
                                    class="flex flex-wrap items-center divide-gray-200 sm:divide-x sm:rtl:divide-x-reverse"
                                >
                                    <div
                                        class="flex items-center space-x-1 rtl:space-x-reverse sm:pe-4"
                                    >
                                        <button
                                            type="button"
                                            class="p-2 text-gray-500 rounded cursor-pointer hover:text-gray-900 hover:bg-gray-100"
                                        >
                                            <svg
                                                class="w-4 h-4"
                                                aria-hidden="true"
                                                xmlns="http://www.w3.org/2000/svg"
                                                fill="none"
                                                viewBox="0 0 12 20"
                                            >
                                                <path
                                                    stroke="currentColor"
                                                    stroke-linejoin="round"
                                                    stroke-width="2"
                                                    d="M1 6v8a5 5 0 1 0 10 0V4.5a3.5 3.5 0 1 0-7 0V13a2 2 0 0 0 4 0V6"
                                                />
                                            </svg>
                                            <span class="sr-only"
                                                >Attach file</span
                                            >
                                        </button>

                                        <button
                                            type="button"
                                            class="p-2 text-gray-500 rounded cursor-pointer hover:text-gray-900 hover:bg-gray-100 dark:text-gray-400 dark:hover:text-white dark:hover:bg-gray-600"
                                        >
                                            <svg
                                                class="w-4 h-4"
                                                aria-hidden="true"
                                                xmlns="http://www.w3.org/2000/svg"
                                                fill="currentColor"
                                                viewBox="0 0 16 20"
                                            >
                                                <path
                                                    d="M14.066 0H7v5a2 2 0 0 1-2 2H0v11a1.97 1.97 0 0 0 1.934 2h12.132A1.97 1.97 0 0 0 16 18V2a1.97 1.97 0 0 0-1.934-2ZM10.5 6a1.5 1.5 0 1 1 0 2.999A1.5 1.5 0 0 1 10.5 6Zm2.221 10.515a1 1 0 0 1-.858.485h-8a1 1 0 0 1-.9-1.43L5.6 10.039a.978.978 0 0 1 .936-.57 1 1 0 0 1 .9.632l1.181 2.981.541-1a.945.945 0 0 1 .883-.522 1 1 0 0 1 .879.529l1.832 3.438a1 1 0 0 1-.031.988Z"
                                                />
                                                <path
                                                    d="M5 5V.13a2.96 2.96 0 0 0-1.293.749L.879 3.707A2.98 2.98 0 0 0 .13 5H5Z"
                                                />
                                            </svg>
                                            <span class="sr-only"
                                                >Upload image</span
                                            >
                                        </button>
                                        <button
                                            type="button"
                                            class="p-2 text-gray-500 rounded cursor-pointer hover:text-gray-900 hover:bg-gray-100 dark:text-gray-400 dark:hover:text-white dark:hover:bg-gray-600"
                                        >
                                            <svg
                                                class="w-4 h-4"
                                                aria-hidden="true"
                                                xmlns="http://www.w3.org/2000/svg"
                                                fill="currentColor"
                                                viewBox="0 0 16 20"
                                            >
                                                <path
                                                    d="M5 5V.13a2.96 2.96 0 0 0-1.293.749L.879 3.707A2.96 2.96 0 0 0 .13 5H5Z"
                                                />
                                                <path
                                                    d="M14.067 0H7v5a2 2 0 0 1-2 2H0v11a1.969 1.969 0 0 0 1.933 2h12.134A1.97 1.97 0 0 0 16 18V2a1.97 1.97 0 0 0-1.933-2ZM6.709 13.809a1 1 0 1 1-1.418 1.409l-2-2.013a1 1 0 0 1 0-1.412l2-2a1 1 0 0 1 1.414 1.414L5.412 12.5l1.297 1.309Zm6-.6-2 2.013a1 1 0 1 1-1.418-1.409l1.3-1.307-1.295-1.295a1 1 0 0 1 1.414-1.414l2 2a1 1 0 0 1-.001 1.408v.004Z"
                                                />
                                            </svg>
                                            <span class="sr-only"
                                                >Format code</span
                                            >
                                        </button>
                                    </div>
                                </div>
                            </div>
                            <div
                                class="px-4 py-2 bg-white rounded-b-lg dark:bg-gray-800"
                            >
                                <label for="editor" class="sr-only"
                                    >Publish post</label
                                >
                                <textarea
                                    id="editor"
                                    rows="8"
                                    class="block w-full px-0 text-sm text-gray-800 bg-white border-0 focus:ring-0"
                                    required
                                ></textarea>
                            </div>
                        </div>
                    </form>

                    <div class="grid grid-cols-1">
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
                                class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-pink-500 focus:border-pink-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white dark:focus:ring-primary-500 dark:focus:border-primary-500"
                            >
                                <option value="School">School</option>
                                <option value="Work">Work</option>
                                <option value="Games">Games</option>
                                <option value="Exercise">Exercise</option>
                            </select>
                        </div>
                    </div>

                    <button
                        type="submit"
                        class="w-full text-white border border-pink-500 bg-pink-500 hover:bg-white hover:text-pink-500 hover:bg-blue-800 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
                    >
                        Post
                    </button>
                </form>
            </div>
        </div>
    </div>
</div>
