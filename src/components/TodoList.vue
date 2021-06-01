<template>
    <h2>TodoList</h2>
    <div v-for="task in tasks" :key="task.name">
        <div class="task" :class="{ alert: task.completed===false }">
            {{ task.name }} {{ task.deadline }} completed
            <input type="checkbox" @click='modify(task)' />
        </div>
    </div>
    <div>
        <label>
            task name
            <input v-model="newTaskName" type="text" />
        </label>
        <label>
            deadline
            <input v-model="newTaskDeadline" type="text" />
        </label>
        <button @click=addTask>add</button>
    </div>
</template>

<style>
.alert{
    color: red;
}
</style>

<script>
import { ref } from "vue";

export default{
    setup(){
        const tasks = ref([]);
        const newTaskName = ref("");
        const newTaskDeadline = ref("");

        const addTask = () => {
            tasks.value.push({ name: newTaskName.value, deadline: newTaskDeadline.value, completed: false });
        };

        const modify = (task) => {
            task.completed = !task.completed;
        }

        return { tasks, newTaskName, newTaskDeadline, addTask, modify };
    },
};
</script>