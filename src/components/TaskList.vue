<template>
  <div>
      <label for="showDone">
      <input type="checkbox"  name="showDone" v-model="showDone"/> Show Done
      </label>
      <ul>
          <li v-for="task in tasks" :key="task.id">
            <p :class="task.done ? 'done' : ''" @click="$store.commit('toggleDone', task.id)">{{task.task}}</p>
            <div @click="$store.commit('removeTask', task.id)" class="remove">X</div>
          </li>
      </ul>
  </div>
</template>

<script>
export default {
  props: ["showsDone"],
  computed: {
      tasks () {
          if(this.showDone) {
             return this.$store.getters.doneTasks
          } else 
          return this.$store.state.tasks
      }
  },
  data () {
      return {
          showDone: false
      }
  }
}
</script>

<style scoped>
  label {
      display: flex;
      align-items: center;
      justify-content: center;
      color: #888;
      font-size: 14px;
      text-transform: uppercase;
      padding: 15px;
      border-bottom: 1px dashed #888;
  }
  label input {
      margin-right: 5px;
  }

  ul {
      display: flex;
      flex-direction: column;
      margin: 0;
      padding: 0;
  }

  ul li {
      display: flex;
      padding: 15px;
      border-bottom: 1px dashed #aaa;
      justify-content: space-between;
      align-items: center;
  }

  ul li p {
      margin: 0;
      color: #171717;
      font-weight: 300;
      text-transform: uppercase;
  }

  ul li  .done {
      color: #af1e2d;
      font-weight: 300;
      font-size: 20px;
      text-decoration: line-through;

  }
</style>