<script>
    import Engage from "../../components/Engage.svelte";
    import SectionWrapper from "../../components/SectionWrapper.svelte";
    import Sidebar from "../../components/Sidebar.svelte";
    import { onMount } from "svelte";
    import { goto } from "$app/navigation";
    onMount(async () => {
        const url = "https://studyplan-api.onrender.com/api/v1/access";
        const data = await fetch(url, {
            method: "GET",
            credentials: "include",
            headers: {
                "Content-Type": "application/x-www-form-urlencoded",
            },
        });
        const response = await data.json();
        if (data.ok) {
            sessionStorage.setItem("access_token", response.access_token);
        } else {
            goto("./");
        }
    });
</script>

<SectionWrapper>
    <Sidebar />
    <Engage />
</SectionWrapper>
