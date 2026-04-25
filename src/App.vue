<template>
  <div id="app">
    <div class="container">
      <h1>ToDo VUE</h1>
      <div class="input-group">
        <input class="input" v-model="newToDo" placeholder="Add a new task..." />
        <button class="add-button" v-on:click="add()">Add</button>
      </div>
      <ul class="todo-list">
        <li v-for="(todo, i) in existingToDo" :key="todo.id" class="todo-item">
          <span class="todo-text">{{ i + 1 }}. {{ todo.text }}</span>
          <button class="delete-button" @click="deleteToDo(i)">X</button>
        </li>
      </ul>
      <button class="clear-all-button" @click="deleteAllToDo()">Clear All</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'app',
  data() {
    return {
      newToDo: '',
      existingToDo: [
        { text: 'Get Groceries', id: 0 },
        { text: 'Run Errands', id: 1 },
        { text: 'Walk the dog', id: 2 },
      ],
    };
  },
  methods: {
    add() {
      if (!this.newToDo.trim()) return;
      this.existingToDo.push({
        text: this.newToDo,
        id: new Date().valueOf(),
      });
      this.newToDo = '';
    },
    deleteToDo(i) {
      this.existingToDo.splice(i, 1);
    },
    deleteAllToDo() {
      this.existingToDo = [];
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@200;300;400;600;700&display=swap');

* {
  font-family: 'Nunito', sans-serif;
  margin: 0;
  padding: 0;
  box-sizing: border-box;
  outline: none;
  text-decoration: none;
}

body {
  display: flex;
  height: 100vh;
  justify-content: center;
  align-items: center;
  padding: 10px;
  background: linear-gradient(135deg, #71b7e6, #9b59b6);
}

#app {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}

.container {
  max-width: 500px;
  width: 100%;
  background: #fff;
  padding: 30px 35px;
  border-radius: 12px;
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.15);
}

.container h1 {
  text-align: center;
  margin-bottom: 24px;
  color: #333;
  font-weight: 700;
  font-size: 28px;
}

.input-group {
  display: flex;
  gap: 10px;
  margin-bottom: 20px;
}

.input {
  flex: 1;
  padding: 12px 16px;
  border: 2px solid #e0e0e0;
  border-radius: 8px;
  font-size: 16px;
  color: #333;
  transition: border-color 0.3s ease;
}

.input:focus {
  border-color: #9b59b6;
}

.add-button {
  padding: 12px 24px;
  background: linear-gradient(135deg, #71b7e6, #9b59b6);
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.add-button:hover {
  transform: translateY(-2px);
  box-shadow: 0 5px 15px rgba(155, 89, 182, 0.4);
}

.todo-list {
  list-style: none;
  margin-bottom: 20px;
}

.todo-item {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 14px 16px;
  margin-bottom: 10px;
  background: #f9f9f9;
  border-radius: 8px;
  border-left: 4px solid #71b7e6;
  transition: background 0.2s ease, transform 0.2s ease;
}

.todo-item:hover {
  background: #f0f0f0;
  transform: translateX(4px);
}

.todo-text {
  font-size: 16px;
  color: #444;
  font-weight: 500;
}

.delete-button {
  width: 32px;
  height: 32px;
  background: #ff6b6b;
  color: #fff;
  border: none;
  border-radius: 6px;
  font-size: 14px;
  font-weight: 700;
  cursor: pointer;
  transition: background 0.2s ease, transform 0.2s ease;
}

.delete-button:hover {
  background: #ee5253;
  transform: scale(1.1);
}

.clear-all-button {
  width: 100%;
  padding: 12px;
  background: #ff9f43;
  color: #fff;
  border: none;
  border-radius: 8px;
  font-size: 16px;
  font-weight: 600;
  cursor: pointer;
  transition: background 0.2s ease, transform 0.2s ease;
}

.clear-all-button:hover {
  background: #ff7f00;
  transform: translateY(-2px);
}
</style>

