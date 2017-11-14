<template>
  <!--
    I'd prefer use bootstrap row and col- divs here instead
    of table and tbody-hack. See discussion here: https://github.com/vuejs/Discussion/issues/295
  -->
  <tbody>
    <!-- display only -->
    <tr v-if="!isNew">
      <td class="task_user">{{name}}</td>
      <td class="task_date">{{date}}</td>
      <td class="task_time">{{time}}</td>
    </tr>
    <tr v-if="!isNew">
      <td colspan="3" class="task_description">
        <div class="toto">{{description}}</div>
      </td>
    </tr>

    <!-- edit -->
    <tr v-if="isNew">
      <td class="task_user"><input type="text" v-model="name"></td>
      <td class="task_date"><input type="text" v-model="date"></td>
      <td class="task_time"><input type="text" v-model="time"></td>
    </tr>
    <tr v-if="isNew">
      <td colspan="3" class="task_description">
        <div class="toto"><input type="text" v-model="description"></div>
      </td>
    </tr>
  </tbody>
</template>

<script>
  export default {
    props:{
      task: { type: Object, required: false },
      isNew: { type: Boolean, required: true },
    },

    created(){
      if(!this.isNew){
        this.id = this.task.id;
        this.name = this.task.name;
        this.date = this.task.date;
        this.time = this.task.time;
        this.description = this.task.description;
      }
    },

    data() {
      return {
        id: 1,
        name: "",
        date: new Date(),
        time: "0:00 ",
        description: ""
      };
    }
  };
</script>
