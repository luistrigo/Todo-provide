<template>
 <h1>ToDo's</h1>
    <TaskForm/>
    <TaskItem v-for="task in tasks" :key="task.id" :task="task"/>
</template>

<script>
import { provide, ref, watchEffect } from 'vue'
import TaskForm from './TaskForm.vue'
import TaskItem from './TaskItem.vue'
export default {
  components: { TaskForm, TaskItem },
    setup(){
        const tasks = ref([])

        //MAke tasks available througth upper components
        provide('tasks',tasks)

        //On reload load tasks from local storage
        if(localStorage.getItem('tasks')){
          tasks.value = JSON.parse(localStorage.getItem('tasks'))
        }

        //watch changes in Task an backup in local storage
        watchEffect(()=>{
          localStorage.setItem('tasks',JSON.stringify(tasks.value))
        })

        return {tasks}
    }
}
</script>