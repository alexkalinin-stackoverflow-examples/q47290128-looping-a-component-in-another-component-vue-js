<script>
  import Task from "./Task.vue";

  export default {
    components: { Task },
    data() {
      return {
        tasks: [],
        isLoading: false,
        doShowNewTaskAddingDialog: false,
      };
    },
    created(){
//      this.isLoading = true;

//      $.ajax({
//        url: '/some/tasks/url',
//        method: 'GET',
//        dataType: 'json',
//        success: (tasks) => {
//          this.isLoading = false;
//          this.tasks = tasks;
//        }
//      });

       this.tasks = [
         {id: 1, name: "task 1", date: new Date(), time: "9:31", description: "descr 1" },
         {id: 1, name: "task 2", date: new Date(), time: "9:32", description: "descr 2" },
         {id: 1, name: "task 3", date: new Date(), time: "9:33", description: "descr 3" },
         {id: 1, name: "task 4", date: new Date(), time: "9:34", description: "descr 4" },
       ]
    },
    methods:{
      addButtonHandler(){
        this.doShowNewTaskAddingDialog = true;
      }
    }
  };
</script>

<template>
  <div>
    <div v-if="isLoading">Please wait, loading tasks...</div>
    <table v-if="!isLoading">
      <task
        v-for="task in tasks"
        :key="task.id"
        :task="task"
        :isNew="false"
      />

      <task
        v-if="doShowNewTaskAddingDialog"
        :isNew="true"
      />
    </table>
    <a href="javascript:" @click="addButtonHandler">Add new?</a>
  </div>
</template>

<style>
  table, td{
    border-collapse: collapse;
    border: 1px solid black;
  }
</style>
