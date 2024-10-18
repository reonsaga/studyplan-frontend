<script>
    import { goto } from "$app/navigation";
    import Login from "../components/Login.svelte";
    const handleLogin = async (email, password) => {
        const url = "https://studyplan-api.onrender.com/api/v1/login";
        await fetch(url, {
            method: "POST",
            credentials: "include",
            headers: {
                "Content-Type": "application/x-www-form-urlencoded",
            },
            body: new URLSearchParams({
                username: email,
                password: password,
            }),
        }).then((response) => {
            if (!response.ok) {
                throw new Error("HTTP error " + response.status);
            } else {
                goto("./tasks");
            }
        });
    };
</script>

<Login {handleLogin} />
