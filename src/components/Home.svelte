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
                        class="top-4 left-3 flex flex-col items-center lg:items-start lg:flex-row lg:space-x-4 space-y-4 lg:space-y-0"
                    >
                        <!--Column 1: Upcoming Deadlines-->
                        <div
                            class="card pt-1 px-4 pb-4 bg-white border sm:w-5/6 lg:w-80 xl:w-96 border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 space-y-4"
                        >
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
                                        d="M6.75 3v2.25M17.25 3v2.25M3 18.75V7.5a2.25 2.25 0 0 1 2.25-2.25h13.5A2.25 2.25 0 0 1 21 7.5v11.25m-18 0A2.25 2.25 0 0 0 5.25 21h13.5A2.25 2.25 0 0 0 21 18.75m-18 0v-7.5A2.25 2.25 0 0 1 5.25 9h13.5A2.25 2.25 0 0 1 21 11.25v7.5"
                                    />
                                </svg>

                                <h1
                                    class="text-2xl font-bold text-gray-900 dark:text-white text-start mt-2 mb-2"
                                >
                                    Upcoming Deadlines
                                </h1>
                            </div>
                            <div class="flex items-center">
                                <Timeline>
                                    <TimelineItem
                                        title="Assignment CCE105"
                                        date="September 30, 2024"
                                    >
                                        <p
                                            class="mb-4 text-base font-normal text-gray-500 dark:text-gray-400"
                                        >
                                            Lorem ipsum dolor sit amet
                                            consectetur adipisicing elit. At,
                                            aspernatur! Nesciunt blanditiis
                                            perspiciatis provident nostrum
                                            tenetur, recusandae suscipit maxime
                                            laborum perferendis, repellat a?
                                            Minima iste corporis rerum impedit
                                            reprehenderit ad.
                                        </p>
                                    </TimelineItem>
                                    <TimelineItem
                                        title="Application 2"
                                        date="October 1, 2024"
                                    >
                                        <p
                                            class="mb-4 text-base font-normal text-gray-500 dark:text-gray-400"
                                        >
                                            Lorem ipsum dolor sit amet,
                                            consectetur adipisicing elit. Quasi,
                                            autem eligendi sint maiores iusto
                                            laborum dolore dolores, porro atque
                                            at perspiciatis assumenda molestias
                                            sequi beatae libero quos quidem
                                            deserunt. Ipsum.
                                        </p>
                                    </TimelineItem>
                                    <TimelineItem
                                        title="Dropkick"
                                        date="October 5, 2024"
                                    >
                                        <p
                                            class="mb-4 text-base font-normal text-gray-500 dark:text-gray-400"
                                        >
                                            Lorem ipsum dolor sit amet
                                            consectetur adipisicing elit.
                                            Molestias, facere perspiciatis, nisi
                                            exercitationem magnam delectus quam,
                                            accusantium earum itaque minus autem
                                            dicta qui? Eos adipisci magni
                                            debitis sunt minima inventore!
                                        </p>
                                    </TimelineItem>
                                </Timeline>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <!--Link this to Tasks Page-->
                                <a
                                    href="#"
                                    class=" font-bold text-gray-900 dark:text-white text-start"
                                >
                                    ...
                                </a>
                            </div>
                        </div>

                        <!--Column 2: Recent Activity-->
                        <div
                            class="card pt-1 px-4 pb-4 bg-white border sm:w-5/6 lg:w-80 xl:w-80 border-gray-200 rounded-lg shadow dark:bg-gray-800 dark:border-gray-700 space-y-4"
                        >
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
                                        d="M9.568 3H5.25A2.25 2.25 0 0 0 3 5.25v4.318c0 .597.237 1.17.659 1.591l9.581 9.581c.699.699 1.78.872 2.607.33a18.095 18.095 0 0 0 5.223-5.223c.542-.827.369-1.908-.33-2.607L11.16 3.66A2.25 2.25 0 0 0 9.568 3Z"
                                    />
                                    <path
                                        stroke-linecap="round"
                                        stroke-linejoin="round"
                                        d="M6 6h.008v.008H6V6Z"
                                    />
                                </svg>

                                <h1
                                    class="text-2xl font-bold text-gray-900 dark:text-white text-start mt-2 mb-2"
                                >
                                    Task Categories
                                </h1>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <p
                                    class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300 strikethrough"
                                >
                                    School
                                </p>
                                <div class="flex-grow"></div>
                                <p
                                    class="text-sm font-medium text-pink-400 dark:text-gray-300"
                                >
                                    2 tasks
                                </p>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <p
                                    class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300 strikethrough"
                                >
                                    Work
                                </p>
                                <div class="flex-grow"></div>
                                <p
                                    class="text-sm font-medium text-pink-400 dark:text-gray-300"
                                >
                                    7 tasks
                                </p>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <p
                                    class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300 strikethrough"
                                >
                                    Games
                                </p>
                                <div class="flex-grow"></div>
                                <p
                                    class="text-sm font-medium text-pink-400 dark:text-gray-300"
                                >
                                    1 task
                                </p>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <p
                                    class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300 strikethrough"
                                >
                                    Exercise
                                </p>
                                <div class="flex-grow"></div>
                                <p
                                    class="text-sm font-medium text-pink-400 dark:text-gray-300"
                                >
                                    1 task
                                </p>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <a
                                    href="#"
                                    class=" font-bold text-gray-900 dark:text-white text-start"
                                >
                                    ...
                                </a>
                            </div>
                            <hr class="bg-gray-500" />
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
                                        d="M4.26 10.147a60.438 60.438 0 0 0-.491 6.347A48.62 48.62 0 0 1 12 20.904a48.62 48.62 0 0 1 8.232-4.41 60.46 60.46 0 0 0-.491-6.347m-15.482 0a50.636 50.636 0 0 0-2.658-.813A59.906 59.906 0 0 1 12 3.493a59.903 59.903 0 0 1 10.399 5.84c-.896.248-1.783.52-2.658.814m-15.482 0A50.717 50.717 0 0 1 12 13.489a50.702 50.702 0 0 1 7.74-3.342M6.75 15a.75.75 0 1 0 0-1.5.75.75 0 0 0 0 1.5Zm0 0v-3.675A55.378 55.378 0 0 1 12 8.443m-7.007 11.55A5.981 5.981 0 0 0 6.75 15.75v-1.5"
                                    />
                                </svg>

                                <h1
                                    class="text-2xl font-bold text-gray-900 dark:text-white text-start mt-2 mb-2"
                                >
                                    Recent Activity
                                </h1>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <p
                                    class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300 strikethrough"
                                >
                                    Tasks Completed
                                </p>
                                <div class="flex-grow"></div>
                                <p
                                    class="text-sm font-medium text-pink-400 dark:text-gray-300"
                                >
                                    0 tasks
                                </p>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <p
                                    class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300 strikethrough"
                                >
                                    Study Sessions Completed
                                </p>
                                <div class="flex-grow"></div>
                                <p
                                    class="text-sm font-medium text-pink-400 dark:text-gray-300"
                                >
                                    2 sessions
                                </p>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <p
                                    class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300 strikethrough"
                                >
                                    Forum Activity
                                </p>
                                <div class="flex-grow"></div>
                                <p
                                    class="text-sm font-medium text-pink-400 dark:text-gray-300"
                                >
                                    0 posts
                                </p>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <p
                                    class="ms-2 text-sm font-medium text-gray-900 dark:text-gray-300 strikethrough"
                                >
                                    Points earned
                                </p>
                                <div class="flex-grow"></div>
                                <p
                                    class="text-sm font-medium text-pink-400 dark:text-gray-300"
                                >
                                    21 points
                                </p>
                            </div>
                            <hr class="bg-gray-500" />
                            <div class="flex items-center">
                                <a
                                    href="#"
                                    class=" font-bold text-gray-900 dark:text-white text-start"
                                >
                                    ...
                                </a>
                            </div>
                        </div>
                    </div>
                </div>
            </div>
        </div>
    </div>
</div>
