<script>
    import { onMount } from "svelte";
    import SectionWrapper from "../../components/SectionWrapper.svelte";
    import Sidebar from "../../components/Sidebar.svelte";
    import Tasks from "../../components/Tasks.svelte";
    import { goto } from "$app/navigation";
    let tasks;
    const getAccessToken = async () => {
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
    };
    const getTasks = async () => {
        const url = "https://studyplan-api.onrender.com/api/v1/tasks";
        const data = await fetch(url, {
            method: "GET",
            credentials: "include",
            headers: {
                "Content-Type": "application/x-www-form-urlencoded",
                Authorization: `Bearer ${sessionStorage.getItem("access_token")}`,
            },
        });
        const response = await data.json();
        tasks = response.data;
    };
    onMount(async () => {
        await getAccessToken();
        await getTasks();
    });
</script>

<SectionWrapper>
    <Sidebar />
    <Tasks {tasks} />
</SectionWrapper>
