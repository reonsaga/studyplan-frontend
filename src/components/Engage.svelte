<!--Script for gif play on click-->
<script>
    import { Tooltip, Button } from "flowbite-svelte";
    let isPlaying = false;
    const pausedSrc = "/src/lib/images/bag-static.png";
    const animatedSrc = "/src/lib/images/bag-open.gif";

    function playGif() {
        isPlaying = true;
    }
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
                            class="card mt-4 pt-1 px-4 pb-4 bg-white border w-[400px] sm:w-[400px] md:w-[325px] lg:w-[400px] border-gray-200 rounded-lg shadow space-y-4 md:self-start lg:ml-0"
                        >
                            <div class="flex items-center">
                                <svg
                                    xmlns="http://www.w3.org/2000/svg"
                                    viewBox="0 0 24 24"
                                    fill="currentColor"
                                    class="size-10 pe-2"
                                >
                                    <path
                                        fill-rule="evenodd"
                                        d="M9 4.5a.75.75 0 0 1 .721.544l.813 2.846a3.75 3.75 0 0 0 2.576 2.576l2.846.813a.75.75 0 0 1 0 1.442l-2.846.813a3.75 3.75 0 0 0-2.576 2.576l-.813 2.846a.75.75 0 0 1-1.442 0l-.813-2.846a3.75 3.75 0 0 0-2.576-2.576l-2.846-.813a.75.75 0 0 1 0-1.442l2.846-.813A3.75 3.75 0 0 0 7.466 7.89l.813-2.846A.75.75 0 0 1 9 4.5ZM18 1.5a.75.75 0 0 1 .728.568l.258 1.036c.236.94.97 1.674 1.91 1.91l1.036.258a.75.75 0 0 1 0 1.456l-1.036.258c-.94.236-1.674.97-1.91 1.91l-.258 1.036a.75.75 0 0 1-1.456 0l-.258-1.036a2.625 2.625 0 0 0-1.91-1.91l-1.036-.258a.75.75 0 0 1 0-1.456l1.036-.258a2.625 2.625 0 0 0 1.91-1.91l.258-1.036A.75.75 0 0 1 18 1.5ZM16.5 15a.75.75 0 0 1 .712.513l.394 1.183c.15.447.5.799.948.948l1.183.395a.75.75 0 0 1 0 1.422l-1.183.395c-.447.15-.799.5-.948.948l-.395 1.183a.75.75 0 0 1-1.422 0l-.395-1.183a1.5 1.5 0 0 0-.948-.948l-1.183-.395a.75.75 0 0 1 0-1.422l1.183-.395c.447-.15.799-.5.948-.948l.395-1.183A.75.75 0 0 1 16.5 15Z"
                                        clip-rule="evenodd"
                                    />
                                </svg>

                                <h1
                                    class="text-2xl font-bold text-gray-900 text-start mt-2 mb-2"
                                >
                                    Pull Avatars
                                </h1>
                                <div class="flex-grow"></div>
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
                                    class="mx-2"
                                    type="dark"
                                    trigger="click"
                                    triggeredBy="#click"
                                    placement="bottom"
                                    >Welcome to the Avatar System! <br /> Here
                                    you can use your acquired points to get
                                    different avatars that serve as your profile
                                    image! <br /> You can spend a minimum of 20
                                    points for a single pull and 200 points for
                                    10 pulls at once.
                                    <hr class="my-2" />
                                    <div
                                        style="display: flex; justify-content: space-between; width: 100%;"
                                    >
                                        <span>Prize</span>
                                        <span>Chance</span>
                                    </div>
                                    <hr class="my-2" />
                                    <div
                                        style="display: flex; justify-content: space-between; width: 100%;"
                                    >
                                        <span>Common</span>
                                        <span>70%</span>
                                    </div>
                                    <div
                                        style="display: flex; justify-content: space-between; width: 100%;"
                                    >
                                        <span>Rare</span>
                                        <span>28%</span>
                                    </div>
                                    <div
                                        style="display: flex; justify-content: space-between; width: 100%;"
                                    >
                                        <span>Epic</span>
                                        <span>2%</span>
                                    </div>
                                    <hr class="my-2" />
                                    Note: If you get a duplicate avatar, you will
                                    be compensated with points according to the rarity
                                    of<br />the duplicate.
                                    <hr class="my-2" />
                                    <div
                                        style="display: flex; justify-content: space-between; width: 100%;"
                                    >
                                        <span>Duplicate</span>
                                        <span>Points</span>
                                    </div>
                                    <hr class="my-2" />
                                    <div
                                        style="display: flex; justify-content: space-between; width: 100%;"
                                    >
                                        <span>Common</span>
                                        <span>5</span>
                                    </div>
                                    <div
                                        style="display: flex; justify-content: space-between; width: 100%;"
                                    >
                                        <span>Rare</span>
                                        <span>20</span>
                                    </div>
                                    <div
                                        style="display: flex; justify-content: space-between; width: 100%;"
                                    >
                                        <span>Epic</span>
                                        <span>100</span>
                                    </div>
                                </Tooltip>
                            </div>

                            <hr class="bg-gray-500" />

                            <div class="flex flex-col items-center">
                                <img
                                    class="mx-4 mb-4 rounded-lg w-96 h-48"
                                    src="/src/lib/images/sample-forum.jpg"
                                />

                                <div class="flex flex-row items-center">
                                    <h1
                                        class="text-xl font-bold text-gray-900 text-start mt-2 mb-2"
                                    >
                                        You have:
                                    </h1>
                                    <h1
                                        class="ms-2 text-xl font-bold text-pink-500 text-start mt-2 mb-2"
                                    >
                                        200
                                    </h1>
                                    <svg
                                        xmlns="http://www.w3.org/2000/svg"
                                        viewBox="0 0 24 24"
                                        fill="pink"
                                        class="size-8 w-6 h-6 ps-1"
                                    >
                                        <path
                                            fill-rule="evenodd"
                                            d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z"
                                            clip-rule="evenodd"
                                        />
                                    </svg>
                                </div>
                                <div class="grid grid-cols-2 gap-8">
                                    <div class="flex flex-col items-center">
                                        <button
                                            data-modal-target="pull-modal"
                                            data-modal-toggle="pull-modal"
                                            type="submit"
                                            class="w-full text-white border border-pink-500 bg-pink-500 hover:bg-white hover:text-pink-500 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
                                        >
                                            <div
                                                class="flex flex-row items-center"
                                            >
                                                <h1
                                                    class="text-xl font-bold mt-2 mb-2"
                                                >
                                                    20
                                                </h1>
                                                <svg
                                                    xmlns="http://www.w3.org/2000/svg"
                                                    viewBox="0 0 24 24"
                                                    fill="pink"
                                                    class="size-8 w-6 h-6 ps-1"
                                                >
                                                    <path
                                                        fill-rule="evenodd"
                                                        d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z"
                                                        clip-rule="evenodd"
                                                    />
                                                </svg>
                                            </div>
                                        </button>
                                        <div class="mt-0 text-center">
                                            <h1
                                                class="text-gray-900 text-sm font-bold"
                                            >
                                                1 Pull
                                            </h1>
                                        </div>
                                    </div>

                                    <div class="flex flex-col items-center">
                                        <button
                                            data-modal-target="pull-modal"
                                            data-modal-toggle="pull-modal"
                                            type="submit"
                                            class="w-full text-white border border-pink-500 bg-pink-500 hover:bg-white hover:text-pink-500 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
                                        >
                                            <div
                                                class="flex flex-row items-center"
                                            >
                                                <h1
                                                    class="text-xl font-bold mt-2 mb-2"
                                                >
                                                    200
                                                </h1>
                                                <svg
                                                    xmlns="http://www.w3.org/2000/svg"
                                                    viewBox="0 0 24 24"
                                                    fill="pink"
                                                    class="size-8 w-6 h-6 ps-1"
                                                >
                                                    <path
                                                        fill-rule="evenodd"
                                                        d="M10.788 3.21c.448-1.077 1.976-1.077 2.424 0l2.082 5.006 5.404.434c1.164.093 1.636 1.545.749 2.305l-4.117 3.527 1.257 5.273c.271 1.136-.964 2.033-1.96 1.425L12 18.354 7.373 21.18c-.996.608-2.231-.29-1.96-1.425l1.257-5.273-4.117-3.527c-.887-.76-.415-2.212.749-2.305l5.404-.434 2.082-5.005Z"
                                                        clip-rule="evenodd"
                                                    />
                                                </svg>
                                            </div>
                                        </button>
                                        <div class="mt-0 text-center">
                                            <h1
                                                class="text-gray-900 text-sm font-bold"
                                            >
                                                10 Pulls
                                            </h1>
                                        </div>
                                    </div>
                                </div>
                            </div>
                        </div>

                        <!--Column 2-->
                        <div
                            class="pt-1 px-4 pb-4 w-[400px] md:w-[410px] lg:w-[600px] xl:w-[700px] mx-auto bg-white border border-gray-200 rounded-lg shadow space-y-4"
                        >
                            <div class="flex items-center">
                                <svg
                                    xmlns="http://www.w3.org/2000/svg"
                                    viewBox="0 0 24 24"
                                    fill="currentColor"
                                    class="size-10 pe-2"
                                >
                                    <path
                                        fill-rule="evenodd"
                                        d="M12 2.25c-5.385 0-9.75 4.365-9.75 9.75s4.365 9.75 9.75 9.75 9.75-4.365 9.75-9.75S17.385 2.25 12 2.25ZM6.262 6.072a8.25 8.25 0 1 0 10.562-.766 4.5 4.5 0 0 1-1.318 1.357L14.25 7.5l.165.33a.809.809 0 0 1-1.086 1.085l-.604-.302a1.125 1.125 0 0 0-1.298.21l-.132.131c-.439.44-.439 1.152 0 1.591l.296.296c.256.257.622.374.98.314l1.17-.195c.323-.054.654.036.905.245l1.33 1.108c.32.267.46.694.358 1.1a8.7 8.7 0 0 1-2.288 4.04l-.723.724a1.125 1.125 0 0 1-1.298.21l-.153-.076a1.125 1.125 0 0 1-.622-1.006v-1.089c0-.298-.119-.585-.33-.796l-1.347-1.347a1.125 1.125 0 0 1-.21-1.298L9.75 12l-1.64-1.64a6 6 0 0 1-1.676-3.257l-.172-1.03Z"
                                        clip-rule="evenodd"
                                    />
                                </svg>

                                <h1
                                    class="text-2xl font-bold text-gray-900 dark:text-white text-start mt-2 mb-2"
                                >
                                    Leaderboards
                                </h1>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <p
                                    class="ms-2 text-sm font-bold text-yellow-300"
                                >
                                    1.
                                </p>
                                <p
                                    class="ms-2 text-sm font-bold text-yellow-300"
                                >
                                    First Placeman
                                </p>
                                <div class="flex-grow"></div>
                                <p class="text-sm font-bold text-pink-500">
                                    2000 points
                                </p>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <p class="ms-2 text-sm font-bold text-gray-400">
                                    2.
                                </p>
                                <p class="ms-2 text-sm font-bold text-gray-400">
                                    Second Placeman
                                </p>
                                <div class="flex-grow"></div>
                                <p class="text-sm font-bold text-pink-500">
                                    1000 points
                                </p>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <p
                                    class="ms-2 text-sm font-bold text-yellow-600"
                                >
                                    3.
                                </p>
                                <p
                                    class="ms-2 text-sm font-bold text-yellow-600"
                                >
                                    Third Placeman
                                </p>
                                <div class="flex-grow"></div>
                                <p class="text-sm font-bold text-pink-500">
                                    500 points
                                </p>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <p class="ms-2 text-sm font-bold text-gray-700">
                                    4.
                                </p>
                                <p class="ms-2 text-sm font-bold text-gray-700">
                                    Fourth Placeman
                                </p>
                                <div class="flex-grow"></div>
                                <p class="text-sm font-bold text-pink-500">
                                    125 points
                                </p>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <p class="ms-2 text-sm font-bold text-gray-700">
                                    5.
                                </p>
                                <p class="ms-2 text-sm font-bold text-gray-700">
                                    Fifth Placeman
                                </p>
                                <div class="flex-grow"></div>
                                <p class="text-sm font-bold text-pink-500">
                                    50 points
                                </p>
                            </div>
                            <hr class="bg-gray-500" />

                            <div class="flex items-center">
                                <svg
                                    xmlns="http://www.w3.org/2000/svg"
                                    viewBox="0 0 24 24"
                                    fill="currentColor"
                                    class="size-10 pe-2"
                                >
                                    <path
                                        fill-rule="evenodd"
                                        d="M12 2.25c-5.385 0-9.75 4.365-9.75 9.75s4.365 9.75 9.75 9.75 9.75-4.365 9.75-9.75S17.385 2.25 12 2.25ZM6.262 6.072a8.25 8.25 0 1 0 10.562-.766 4.5 4.5 0 0 1-1.318 1.357L14.25 7.5l.165.33a.809.809 0 0 1-1.086 1.085l-.604-.302a1.125 1.125 0 0 0-1.298.21l-.132.131c-.439.44-.439 1.152 0 1.591l.296.296c.256.257.622.374.98.314l1.17-.195c.323-.054.654.036.905.245l1.33 1.108c.32.267.46.694.358 1.1a8.7 8.7 0 0 1-2.288 4.04l-.723.724a1.125 1.125 0 0 1-1.298.21l-.153-.076a1.125 1.125 0 0 1-.622-1.006v-1.089c0-.298-.119-.585-.33-.796l-1.347-1.347a1.125 1.125 0 0 1-.21-1.298L9.75 12l-1.64-1.64a6 6 0 0 1-1.676-3.257l-.172-1.03Z"
                                        clip-rule="evenodd"
                                    />
                                </svg>

                                <h1
                                    class="text-2xl font-bold text-gray-900 dark:text-white text-start mt-2 mb-2"
                                >
                                    Monthly Activity
                                </h1>
                            </div>
                            <hr class="bg-gray-500" />
                            <div
                                class="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-4 gap-4 items-stretch"
                            >
                                <div
                                    class="flex flex-col pt-1 px-4 pb-4 w-full mx-auto bg-white border border-gray-200 rounded-lg shadow space-y-4"
                                >
                                    <h1
                                        class="font-bold text-gray-400 text-start mt-2 mb-2"
                                    >
                                        LEADERBOARD PLACEMENT
                                    </h1>
                                    <hr class="bg-gray-500" />
                                    <h1
                                        class="text-2xl font-bold text-pink-500 text-start mt-2 mb-2"
                                    >
                                        1245th
                                    </h1>
                                </div>

                                <div
                                    class="flex flex-col pt-1 px-4 pb-4 w-full mx-auto bg-white border border-gray-200 rounded-lg shadow space-y-4"
                                >
                                    <h1
                                        class="font-bold text-gray-400 text-start mt-2 mb-2"
                                    >
                                        TASKS COMPLETED
                                    </h1>
                                    <hr class="bg-gray-500" />
                                    <h1
                                        class="text-2xl font-bold text-pink-500 text-start mt-2 mb-2"
                                    >
                                        7
                                    </h1>
                                </div>

                                <div
                                    class="flex flex-col pt-1 px-4 pb-4 w-full mx-auto bg-white border border-gray-200 rounded-lg shadow space-y-4"
                                >
                                    <h1
                                        class="font-bold text-gray-400 text-start mt-2 mb-2"
                                    >
                                        STUDY SESSIONS COMPLETED
                                    </h1>
                                    <hr class="bg-gray-500" />
                                    <h1
                                        class="text-2xl font-bold text-pink-500 text-start mt-2 mb-2"
                                    >
                                        3
                                    </h1>
                                </div>

                                <div
                                    class="flex flex-col pt-1 px-4 pb-4 w-full mx-auto bg-white border border-gray-200 rounded-lg shadow space-y-4"
                                >
                                    <h1
                                        class="font-bold text-gray-400 text-start mt-2 mb-2"
                                    >
                                        POINTS ACCUMULATED
                                    </h1>

                                    <hr class="bg-gray-500" />
                                    <h1
                                        class="text-2xl font-bold text-pink-500 text-start mt-2 mb-2"
                                    >
                                        0
                                    </h1>
                                </div>
                            </div>

                            <hr class="bg-gray-500" />
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>

<!--Pull Pop-up-->
<div
    id="pull-modal"
    tabindex="-1"
    aria-hidden="true"
    class="hidden overflow-y-auto overflow-x-hidden fixed inset-0 z-50 flex justify-center items-center"
>
    <div class="relative w-full max-w-md md:max-w-lg lg:max-w-xl p-4">
        <!-- Modal content -->
        <div class="relative bg-white rounded-lg shadow dark:bg-gray-700">
            <!-- Modal header -->
            <div
                class="flex flex-col items-center justify-between p-4 md:p-5 border-b rounded-t dark:border-gray-600"
            >
                <h3
                    class="text-2xl font-semibold text-gray-900 dark:text-white"
                >
                    Open the bag!
                </h3>

                <hr class="bg-gray-500" />
                <div class="flex flex-col items-center">
                    <!-- Clickable image to trigger animation -->
                    <img
                        class="mx-4 mb-4 rounded-lg cursor-pointer"
                        src={isPlaying ? animatedSrc : pausedSrc}
                        alt="image description"
                        on:click={playGif}
                    />
                </div>
            </div>
        </div>
    </div>
</div>
