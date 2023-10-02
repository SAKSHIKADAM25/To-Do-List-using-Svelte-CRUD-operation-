<script>
    let task = "";
    let newTasks = [];
    function addTask() {
        if (task == "") {
            alert("Please enter a task!");
        } else {
            newTasks = [...newTasks, task];
        }
        task = "";
    }
    function deleteTask(index) {
		newTasks = [...newTasks.slice(0, index), ...newTasks.slice(index + 1)];
    }
    function editTask(index) {
        task = newTasks[index];
        deleteEditedTask();
    }
    function deleteEditedTask() {
        newTasks.splice(newTasks.indexOf(task), 1);
    }
</script>

<main>
    <title>TODO LIST</title>
    <h1>To-Do List</h1>
    <input type="text" placeholder="Enter the task" bind:value={task} />
    <button on:click={addTask}>Add</button>
    <ul>
        {#each newTasks as task, index (task)}
            <li class="task-item">
                <label>
                    <input type="checkbox" />
                    {task}
                </label>
                <button class="edit-btn" on:click={() => editTask(index)}
                    >Edit</button
                >
                <button class="delete-btn" on:click={() => deleteTask(index)}
                    >x</button
                >
            </li>
        {/each}
    </ul>
</main>

<style>
    main {
        align-items: center;
        max-width: 550px;
        font-family: Arial, sans-serif;
        background-color: lightblue;
        margin: 90px auto;
        padding: 30px 20px 50px;
        border-radius: 8px;
    }

    h1 {
        margin: 10px;
        text-align: center;
        margin-bottom: 10px;
    }

    input {
        width: 250px;
        height: 40px;
        margin: 20px 20px 20px 130px;
        border-radius: 5px;
        font-size: 20px;
    }

    button {
        background-color: #5c9cef;
        width: 70px;
        height: 50px;
        margin: 20px;
        border-radius: 5px;
        font-size: 20px;
        font-weight: 900;
        border: 2000px;
        cursor: pointer;
    }

    ul li {
        display: flex;
        width: 200px;
        height: 30px;
        text-align: center;
    }

    input[type="checkbox"] {
        width: 18px;
        height: 18px;
        margin: 10px 10px 40px 40px;
        cursor: pointer;
    }

    input[type="checkbox"]:checked {
        background-color: #5c9cef;
        border: 2px solid #5c9cef;
    }

    .task-item {
        width: 500px;
        height: 50px;
        font-size: 22px;
        /* margin: 10px 5px 15px 20px; */
        align-content: center;
    }

    .edit-btn {
        width: 50px;
        height: 30px;
        background-color: darkgray;
        margin: 10px 10px auto 350px;
        font-size: 15px;
        border-radius: 5px;
        cursor: pointer;
        position: absolute;
    }

    .delete-btn {
        width: 20px;
        height: 20px;
        border-radius: 10px;
        background-color: darkgray;
        margin: 10px 10px auto 430px;
        font-size: 15px;
        position: absolute;
    }
</style>
