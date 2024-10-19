<!--Import Svelte Thingies only for Timeline-->
<script>
    import { Timeline, TimelineItem, Button } from "flowbite-svelte";
</script>

<!--Overall Parent Containers-->
<div class="flex-1 flex justify-center items-center xl:ml-64">
    <div class="p-4">
        <div class="grid grid-cols-1 gap-4 mb-4">
            <div class="flex items-center justify-center rounded">
                <div class="relative min-h-screen z-10">
                    <div
                        class="top-4 left-3 flex flex-col items-center md:flex-row space-x-4 space-y-4"
                    >
                        <!--Column 1-->
                        <div
                            class="card mt-4 pt-1 px-4 pb-4 bg-white border w-96 border-gray-200 rounded-lg shadow space-y-4 md:self-start lg:ml-0"
                        >
                            <div class="flex items-center">
                                <svg
                                    xmlns="http://www.w3.org/2000/svg"
                                    viewBox="0 0 24 24"
                                    fill="currentColor"
                                    class="size-10 pe-2"
                                >
                                    <path
                                        d="M12.378 1.602a.75.75 0 0 0-.756 0L3 6.632l9 5.25 9-5.25-8.622-5.03ZM21.75 7.93l-9 5.25v9l8.628-5.032a.75.75 0 0 0 .372-.648V7.93ZM11.25 22.18v-9l-9-5.25v8.57a.75.75 0 0 0 .372.648l8.628 5.033Z"
                                    />
                                </svg>

                                <h1
                                    class="text-2xl font-bold text-gray-900 text-start mt-2 mb-2"
                                >
                                    Avatar
                                </h1>
                            </div>
                            <hr class="bg-gray-300" />
                            <div
                                class="flex flex-col justify-center items-center"
                            >
                                <img
                                    class="rounded-full w-48 h-48"
                                    src="/src/lib/images/placeholder.png"
                                    alt="image description"
                                />
                            </div>
                            <hr class="bg-gray-300" />
                            <div
                                class="flex flex-col justify-center items-center"
                            >
                                <button
                                    class="quiz-button"
                                    data-modal-target="forumcreation-modal"
                                    data-modal-toggle="forumcreation-modal"
                                    type="button"
                                >
                                    Change Avatar
                                </button>
                            </div>
                        </div>

                        <!--Column 2: Recent Activity-->
                        <div
                            class="settings-card pt-1 px-4 pb-4 w-5/6 md:w-[410px] lg:w-[600px] xl:w-[700px] mx-auto bg-white border border-gray-200 rounded-lg shadow space-y-4"
                        >
                            <div class="flex items-center">
                                <svg
                                    xmlns="http://www.w3.org/2000/svg"
                                    viewBox="0 0 24 24"
                                    fill="currentColor"
                                    class="size-10 pe-2"
                                >
                                    <path
                                        d="M18.75 12.75h1.5a.75.75 0 0 0 0-1.5h-1.5a.75.75 0 0 0 0 1.5ZM12 6a.75.75 0 0 1 .75-.75h7.5a.75.75 0 0 1 0 1.5h-7.5A.75.75 0 0 1 12 6ZM12 18a.75.75 0 0 1 .75-.75h7.5a.75.75 0 0 1 0 1.5h-7.5A.75.75 0 0 1 12 18ZM3.75 6.75h1.5a.75.75 0 1 0 0-1.5h-1.5a.75.75 0 0 0 0 1.5ZM5.25 18.75h-1.5a.75.75 0 0 1 0-1.5h1.5a.75.75 0 0 1 0 1.5ZM3 12a.75.75 0 0 1 .75-.75h7.5a.75.75 0 0 1 0 1.5h-7.5A.75.75 0 0 1 3 12ZM9 3.75a2.25 2.25 0 1 0 0 4.5 2.25 2.25 0 0 0 0-4.5ZM12.75 12a2.25 2.25 0 1 1 4.5 0 2.25 2.25 0 0 1-4.5 0ZM9 15.75a2.25 2.25 0 1 0 0 4.5 2.25 2.25 0 0 0 0-4.5Z"
                                    />
                                </svg>

                                <h1
                                    class="text-2xl font-bold text-gray-900 dark:text-white text-start mt-2 mb-2"
                                >
                                    Settings
                                </h1>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex flex-col items-start">
                                <label
                                    for="password"
                                    class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                                    >E-mail Address</label
                                >
                                <input
                                    type="text"
                                    class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-0 focus:border-pink-500 block w-full p-2.5"
                                    placeholder="youremail@gmail.com"
                                    readonly
                                />
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="grid grid-cols-2 space-x-2">
                                <div class="flex flex-col items-start">
                                    <label
                                        for="ouser"
                                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                                        >Username</label
                                    >
                                    <input
                                        type="text"
                                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-0 focus:border-pink-500 block w-full p-2.5"
                                        placeholder="Old username"
                                        readonly
                                    />
                                </div>
                                <div class="flex flex-col items-start">
                                    <label
                                        for="nuser"
                                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                                        >Change Username</label
                                    >
                                    <input
                                        type="text"
                                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-0 focus:border-pink-500 block w-full p-2.5"
                                        placeholder="New Username"
                                    />
                                </div>
                                <div
                                    class="flex items-center justify-center col-span-2"
                                >
                                    <button
                                        class="quiz-button w-[200px] ms-0"
                                        type="button"
                                    >
                                        Save Changes
                                    </button>
                                </div>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="grid grid-cols-2 space-x-2">
                                <div class="flex flex-col items-start">
                                    <label
                                        for="opass"
                                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                                        >Password</label
                                    >
                                    <input
                                        type="password"
                                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-0 focus:border-pink-500 block w-full p-2.5"
                                        placeholder="Enter your password"
                                    />
                                </div>
                                <div class="flex flex-col items-start">
                                    <label
                                        for="password"
                                        class="block mb-2 text-sm font-medium text-gray-900 dark:text-white"
                                        >Change Password</label
                                    >
                                    <input
                                        type="password"
                                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-0 focus:border-pink-500 block w-full p-2.5"
                                        placeholder="Enter your new password"
                                    />
                                </div>
                                <div
                                    class="flex items-center justify-center col-span-2"
                                >
                                    <button
                                        class="quiz-button w-[200px] ms-0"
                                        type="button"
                                    >
                                        Save Changes
                                    </button>
                                </div>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="grid grid-cols-2 gap-2">
                                <div class="flex items-center">
                                    <label
                                        class="inline-flex items-center cursor-pointer"
                                    >
                                        <input
                                            type="checkbox"
                                            value=""
                                            class="sr-only peer"
                                            checked
                                        />
                                        <div
                                            class="relative w-11 h-6 bg-gray-200 rounded-full peer-checked:bg-pink-500 after:content-[''] after:absolute after:top-0.5 after:left-0 after:bg-white after:border after:border-gray-300 after:rounded-full after:h-5 after:w-5 after:transition-all peer-checked:after:translate-x-full peer-checked:after:border-white"
                                        ></div>
                                        <span
                                            class="ms-3 text-sm font-medium text-gray-900"
                                            >Push Notifications</span
                                        >
                                    </label>
                                </div>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>

<!--Change Avatar-->
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
                    Avatars
                </h3>
                <button
                    type="button"
                    class="text-gray-400 bg-transparent hover:bg-gray-200 hover:text-gray-900 rounded-lg text-sm w-8 h-8 inline-flex justify-center items-center"
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
                    <div class="flex flex-row items-start">
                        <h1 class="text-lg text-gray-700">Land :</h1>
                        <h1 class="text-lg text-pink-500 ms-3">0/5</h1>
                    </div>
                    <div class="grid grid-cols-5">
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="land-radio1"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="land-radio1"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Dog</label
                                >
                            </div>
                        </div>
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="land-radio2"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="land-radio2"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Dog</label
                                >
                            </div>
                        </div>
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="land-radio3"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="land-radio3"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Dog</label
                                >
                            </div>
                        </div>
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="land-radio4"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="land-radio4"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Dog</label
                                >
                            </div>
                        </div>
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="land-radio5"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="land-radio5"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Dog</label
                                >
                            </div>
                        </div>
                    </div>
                    <hr class="bg-gray-300" />
                    <div class="flex flex-row items-start">
                        <h1 class="text-lg text-gray-700">Sea :</h1>
                        <h1 class="text-lg text-pink-500 ms-3">0/5</h1>
                    </div>
                    <div class="grid grid-cols-5">
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="sea-radio1"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="sea-radio1"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Fish</label
                                >
                            </div>
                        </div>
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="sea-radio2"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="sea-radio2"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Fish</label
                                >
                            </div>
                        </div>
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="sea-radio3"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="sea-radio3"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Fish</label
                                >
                            </div>
                        </div>
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="sea-radio4"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="sea-radio4"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Fish</label
                                >
                            </div>
                        </div>
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="sea-radio5"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="sea-radio5"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Fish</label
                                >
                            </div>
                        </div>
                    </div>
                    <hr class="bg-gray-300" />

                    <div class="flex flex-row items-start">
                        <h1 class="text-lg text-gray-700">Air :</h1>
                        <h1 class="text-lg text-pink-500 ms-3">0/5</h1>
                    </div>
                    <div class="grid grid-cols-5">
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="air-radio1"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="air-radio1"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Eagle</label
                                >
                            </div>
                        </div>
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="air-radio2"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="air-radio2"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Eagle</label
                                >
                            </div>
                        </div>
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="air-radio3"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="air-radio3"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Eagle</label
                                >
                            </div>
                        </div>
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="air-radio4"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="air-radio4"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Eagle</label
                                >
                            </div>
                        </div>
                        <div class="flex flex-col">
                            <img
                                class="trophy-image mx-4 mb-4 rounded-lg"
                                src="/src/lib/images/placeholder.png"
                                alt="image description"
                            />
                            <div class="flex flex-row justify-center">
                                <input
                                    id="air-radio5"
                                    type="radio"
                                    value=""
                                    name="inline-radio-group"
                                    class="w-4 h-4 text-pink-500 bg-gray-100 border-gray-300 focus:ring-pink-500 focus:ring-2"
                                />
                                <label
                                    for="air-radio5"
                                    class="ms-2 text-sm font-medium text-gray-700"
                                    >Eagle</label
                                >
                            </div>
                        </div>
                    </div>
                    <hr class="bg-gray-300" />
                    <button type="submit" class="w-full quiz-button">
                        Select Avatar
                    </button>
                </form>
            </div>
        </div>
    </div>
</div>
