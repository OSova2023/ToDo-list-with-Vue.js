<script>
import ButtonDel from './ButtonDel.vue'

export default {
  components: { ButtonDel },
  name: 'Todo-list',
  data() {
    return {
      title: 'delete',
      userInput: '',
      allTasks: []
    }
  },
  methods: {
    createTask() {
      if (this.userInput.trim() !== '') {
        this.allTasks.unshift(this.userInput)
        this.userInput = ''
      }
    },
    deleteTask(index) {
      // this.allTasks = this.allTasks.filter((el, i) => {
      //   i !== index
      this.allTasks.splice(index, 1)
      // })
      console.log(this.allTasks)
    }
  }
}
</script>

<template>
  <div class="container">
    <main>
      <h1>Todo list</h1>
      <h4>Add new item to the list</h4>
      <div class="group">
        <input v-model="userInput" type="text" placeholder="type your text" />
        <button @click="createTask" class="buttonAdd">Add a new task</button>
      </div>
    </main>

    <ul class="list">
      <li v-for="(el, index) in allTasks" v-bind:key="index">
        <span>{{ index + 1 }}.</span>{{ el }}<ButtonDel @remove="deleteTask(index)" />
      </li>
    </ul>
  </div>
</template>

<style scoped>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

.container {
  max-width: 100%;
  display: flex;
  flex-direction: column;
  align-items: center;
}

main {
  display: flex;
  flex-direction: column;
  align-items: center;
}

input {
  background: #fff;
  border-radius: 5px;
  border: 3px #1f3830 solid;
  color: #1f3830;
  padding: 5px 10px;
}
.buttonAdd {
  background: #fff;
  border-radius: 5px;
  border: 3px #1f3830 solid;
  color: #1f3830;
  font-weight: 700;
  margin-left: 20px;
  padding: 5px 10px;
}

.buttonAdd:hover {
  background: #1f3830;
  color: #fff;
}

.list {
  list-style: none;
  width: 500px;
}

.list li {
  display: flex;
  position: relative;
  margin: 10px;
  background: #1f3830;
  color: #fff;
  border-radius: 5px;
  padding: 15px 10px;
  width: 100%;
}

.list li span {
  margin-right: 10px;
}

.list li .delete {
  float: left;
  background: rgb(91, 17, 17);
  color: #fff;
  border-radius: 5px;
  padding: 5px 10px;
  position: absolute;
  right: 10px;
  align-self: center;
  top: 20%;
}

.delete:hover {
  background: #fff;
  color: rgb(91, 17, 17);
  font-weight: 700;
  transform: scale(1.2);
}
</style>
