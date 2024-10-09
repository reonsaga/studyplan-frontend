<!--Script for gif play on click-->
<script>
    let isPlaying = false;
    const pausedSrc = "images/bag-static.png";
    const animatedSrc = "images/bag-open.gif";

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
                        class="top-4 left-3 flex flex-col items-center lg:items-start lg:flex-row lg:space-x-4 space-y-4 lg:space-y-0"
                    >
                        <!--Column 1-->
                        <div
                            class="card pt-1 px-4 pb-4 bg-white border w-5/6 border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 space-y-4"
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
                                    class="text-2xl font-bold text-gray-900 dark:text-white text-start mt-2 mb-2"
                                >
                                    Sprite Pool
                                </h1>
                            </div>

                            <hr class="bg-gray-500" />

                            <div class="flex flex-col items-center">
                                <div class="flex flex-row items-center">
                                    <h1
                                        class="text-xl font-bold text-gray-900 dark:text-white text-start mt-2 mb-2"
                                    >
                                        You have: 200
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
