<template>
  <div class="form">
      <input type="text" v-model="task" name="task" placeholder="Enter a task...">
      <button @click="newTask">ADD</button>
  </div>
</template>

<script>
export default {
    data () {
        return {
            task: ""
        }
    },
    methods: {
        newTask () {
          this.$store.commit("newTask", this.task)
          this.task = ""
        }
    }
}
</script>

<style scoped>
  .form {
      width: 100vw;
      height: 35px;
      display: flex;
      align-items: stretch;
      margin: 0;
  }
  .form input {
      flex: 1;
  }
</style>