<template>
    <div class="task-container"
        @dblclick="$emit(`toggle-reminder`, task.id)" 
        :class="[task.reminder ? 'reminder' : '', 'task']"
        >
        <h3>{{ task.text }}</h3>
        <p>{{ task.day }}</p>
        <span @click="$emit(`delete-task`, task.id)">
            <i class="fas fa-times"></i><span>Remove</span>
        </span>

    </div>
</template>

<script>
export default {
    name: "Task",
    props: {
        task: Object,
    },
}
</script>

<style scoped>
.fas{
    color: red;
    cursor: pointer;
    margin-right: 8px;
}

.task.reminder {
  border-left: 5px solid green;
}

.task-container{
    cursor: pointer;
    display: flex;
    justify-content: space-between;
    align-items: center;
    width: 100%;
}
</style>