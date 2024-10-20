<script>
    import { slide } from "svelte/transition"; // Import slide transition

    export let handleRegister;
    let email = "";
    let fname = "";
    let lname = "";
    let password = "";
    let cpassword = "";
    let checked = false;

    let showError = false;
    let errorMessage = "";

    const clear = () => {
        email = "";
        fname = "";
        lname = "";
        password = "";
        cpassword = "";
        checked = false;
        showError = false;
    };

    const validateEmail = (email) => {
        const emailPattern = /^[^\s@]+@[^\s@]+\.[^\s@]+$/;
        return emailPattern.test(email);
    };

    const register = () => {
        // Check for blank fields
        if (!email || !fname || !lname || !password || !cpassword || !checked) {
            showError = true;
            errorMessage =
                "All fields must be filled and agree to the Terms and Conditions.";
        }
        // Check for valid email format
        else if (!validateEmail(email)) {
            showError = true;
            errorMessage = "Please enter a valid email address.";
        }
        // Check if password and confirm password match
        else if (password !== cpassword) {
            showError = true;
            errorMessage = "Passwords do not match.";
        }
        // If everything is fine, proceed with registration
        else {
            showError = false; // Hide error message
            handleRegister(email, fname, lname, password); // Proceed with registration logic
            clear(); // Clear fields after registration
        }
    };
</script>

<body>
    <div
        class="flex items-center justify-center min-h-screen bg-rose-200 dark:bg-gray-900"
    >
        <div
            class="relative flex flex-col m-6 space-y-8 bg-white shadow-2xl rounded-2xl md:flex-row md:space-y-0"
        >
            <!-- Input Side -->
            <div class="flex flex-col justify-center p-8 md:p-14">
                <h1
                    class="text-6xl font-bold italic text-gray-900 dark:text-white text-center"
                >
                    PlanTogether
                </h1>
                <div class="py-2">
                    <label
                        for="fname"
                        class="block text-md font-medium text-gray-900 dark:text-white"
                        >First Name</label
                    >
                    <input
                        type="text"
                        class="w-full p-2 border border-gray-300 rounded-md placeholder:font-light placeholder:text-gray-500"
                        name="fname"
                        id="fname"
                        bind:value={fname}
                        placeholder="John"
                    />
                    <label
                        for="lname"
                        class="block mt-2 text-md font-medium text-gray-900 dark:text-white"
                        >Last Name</label
                    >
                    <input
                        type="text"
                        class="w-full p-2 border border-gray-300 rounded-md placeholder:font-light placeholder:text-gray-500"
                        name="lname"
                        id="lname"
                        bind:value={lname}
                        placeholder="Doe"
                    />
                    <label
                        for="email"
                        class="block mt-2 text-md font-medium text-gray-900 dark:text-white"
                        >E-mail Address</label
                    >
                    <input
                        type="text"
                        class="w-full p-2 border border-gray-300 rounded-md placeholder:font-light placeholder:text-gray-500"
                        name="email"
                        id="email"
                        bind:value={email}
                        placeholder="studyplan@company.com"
                    />
                    <label
                        for="password"
                        class="block mt-2 text-sm font-medium text-gray-900 dark:text-white"
                        >Password</label
                    >
                    <input
                        type="password"
                        name="password"
                        id="password"
                        bind:value={password}
                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-0 focus:border-pink-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white"
                        placeholder="••••••••"
                        required
                    />
                    <label
                        for="cpassword"
                        class="block mt-2 text-sm font-medium text-gray-900 dark:text-white"
                        >Confirm Password</label
                    >
                    <input
                        type="password"
                        name="cpassword"
                        id="cpassword"
                        bind:value={cpassword}
                        class="bg-gray-50 border border-gray-300 text-gray-900 text-sm rounded-lg focus:ring-0 focus:border-pink-500 block w-full p-2.5 dark:bg-gray-600 dark:border-gray-500 dark:placeholder-gray-400 dark:text-white"
                        placeholder="••••••••"
                        required
                    />
                </div>
                <div class="flex justify-between w-full py-2">
                    <div class="flex items-center">
                        <input
                            required
                            id="agree"
                            type="checkbox"
                            bind:checked
                            class="w-4 h-4 text-white bg-gray-100 border-gray-300 rounded focus:ring-pink-500 focus:ring-2 checked:bg-pink-600 checked:border-pink-600 dark:bg-gray-700 dark:border-gray-600 dark:focus:ring-blue-500 dark:ring-offset-gray-800"
                        />
                        <label
                            for="agree"
                            class="ml-2 text-sm font-medium text-gray-900 dark:text-gray-300"
                        >
                            I Agree to the
                            <!-- Link to Terms and Conditions -->
                            <a
                                href="#"
                                class="text-pink-500 hover:underline dark:text-blue-500"
                                >Terms and Conditions</a
                            >
                        </label>
                    </div>
                </div>
                <button
                    type="button"
                    on:click={register}
                    class="w-full text-white bg-pink-500 hover:bg-pink-800 focus:ring-4 focus:outline-none focus:ring-pink-300 font-medium rounded-lg text-sm px-5 py-2.5 text-center dark:bg-blue-600 dark:hover:bg-blue-700 dark:focus:ring-blue-800"
                    >Register</button
                >

                <div class="mt-2 text-center text-gray-400">
                    Already have an account?
                    <!--Link to Login Page-->
                    <a
                        href="/"
                        class="text-pink-500 hover:underline dark:text-blue-500"
                        >Login</a
                    >
                </div>

                <!-- Error Alert (with Svelte slide transition) -->
                {#if showError}
                    <div
                        id="alert-2"
                        class="mt-2 flex items-center p-4 mb-4 text-red-800 rounded-lg bg-red-50 w-[300px] mx-auto"
                        role="alert"
                        transition:slide={{ duration: 200 }}
                    >
                        <svg
                            class="flex-shrink-0 w-4 h-4"
                            aria-hidden="true"
                            xmlns="http://www.w3.org/2000/svg"
                            fill="currentColor"
                            viewBox="0 0 20 20"
                        >
                            <path
                                d="M10 .5a9.5 9.5 0 1 0 9.5 9.5A9.51 9.51 0 0 0 10 .5ZM9.5 4a1.5 1.5 0 1 1 0 3 1.5 1.5 0 0 1 0-3ZM12 15H8a1 1 0 0 1 0-2h1v-3H8a1 1 0 0 1 0-2h2a1 1 0 0 1 1 1v4h1a1 1 0 0 1 0 2Z"
                            />
                        </svg>
                        <div class="ms-3 text-xs font-medium">
                            {errorMessage}
                        </div>
                        <button
                            type="button"
                            class="ms-auto -mx-1.5 -my-1.5 bg-red-50 text-red-500 rounded-lg focus:ring-2 focus:ring-red-400 p-1.5 hover:bg-red-200 inline-flex items-center justify-center h-8 w-8"
                            on:click={() => (showError = false)}
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
                        </button>
                    </div>
                {/if}
            </div>
            <!--Image Side-->
            <div class="relative">
                <img
                    src="/src/lib/images/bg-login.png"
                    alt="img"
                    class="w-[400px] h-full hidden rounded-r-2xl md:block object-cover"
                />
            </div>
        </div>
    </div>
</body>
