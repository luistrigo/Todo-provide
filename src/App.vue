<template>
<div  class="container mt-3">
  <div class="row justify-content-center">
    <div class="col-lg-6">
      <TodoApp></TodoApp>
    </div>
  </div>
</div>
</template>

<script>
import TodoApp from "./components/TodoApp.vue"
export default {
  name: 'App',
  components: {
    TodoApp
  }
}
</script>