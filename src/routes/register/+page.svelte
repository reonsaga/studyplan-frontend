<script>
    import Register from "../../components/Register.svelte";
    import SectionWrapper from "../../components/SectionWrapper.svelte";
    import { onMount } from "svelte";
    import { goto } from "$app/navigation";
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
