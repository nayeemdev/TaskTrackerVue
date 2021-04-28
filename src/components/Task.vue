<template>
<div :class="[task.reminder ? 'reminder' : '', 'task'] ">
    <h3>
        {{ task.text }}
        <i :class="[task.reminder ? 'fa-bell-slash' : 'fa-bell', 'fas']"></i>    
    </h3>
    <p>
        {{ task.date }}
        <i class="fas fa-trash"></i>
    </p>
</div>
</template>

<script>
export default {
    name: 'Task',
    props: {
        task: Object
    }
}
</script>

<style scope>
    .task {
        background: #eee;
        margin: 5px;
        padding: 10px 20px;
        cursor: pointer;
    }

    .task.reminder {
        border-left: 5px solid green;
    }

    .task p, .task h3 {
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
    .task p i {
        color: red;
    }
    .task h3 i {
        color: green;
    }
</style>