<script>
    import Register from "../../components/Register.svelte";
    import SectionWrapper from "../../components/SectionWrapper.svelte";
    import { onMount } from "svelte";
    import { goto } from "$app/navigation";
    onMount(async() => {
            const url = "https://studyplan-api.onrender.com/api/v1/access"
            const data = await fetch(url, {
                method: "GET",
                credentials: 'include',
                headers: {
                    "Content-Type": "application/x-www-form-urlencoded"
                },
            })
            const response = await data.json()
            if (data.ok) {
                sessionStorage.setItem("access_token", response.access_token)
            } else {
                goto('./')
            }
        }
    )
    const handleRegister = async(email, fname, lname, password) => {
        const url = "https://studyplan-api.onrender.com/api/v1/register"
        const payload = {
            "user_email": email,
            "user_fname": fname,
            "user_lname": lname,
            "user_password": password
        }
        const data = await fetch(url, {
            method: "POST",
            credentials: 'include',
            headers: {
                "Content-Type": "application/json",
            },
            body: JSON.stringify(payload)
        })
        const response = await data.json()
        if (data.ok) {
            goto('./')
        } else {
            throw new Error(`${response.detail}`);

        }
    }
</script>

<Register handleRegister={handleRegister} />
