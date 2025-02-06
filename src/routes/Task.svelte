<script>
    let taskList = $state([]);
    function addTask() {
        console.log("btn pressed")
        const task = document.getElementById("taskInput").value;
        if (task.length > 0) {
            const taskBody = {
                id: crypto.randomUUID(),
                title: task,
            };

            taskList.push(taskBody);
            document.getElementById("taskInput").value = "";
            console.log("list", taskList);
        } else {
            window.alert("Please write some text");
        }
    }
</script>

<div class="flex items-center justify-center">
    <h1 class="font-bold text-orange-500 text-2xl mt-4">Enter Task below:</h1>
</div>
<br />
<div class="flex items-center justify-center">
    <input
        id="taskInput"
        class="border-2 border-black mr-5"
        type="text"
        name="title"
    /><button class="rounded border-2 border-black p-2" onclick={addTask}
        >Add</button
    >
</div>
<div class="flex items-center justify-center ">
    <ul>
        {#each taskList as task}
            <li class="m-5 border-2 border-orange-500 w-96 text-center">{task?.title}</li>
        {/each}
    </ul>
</div>
