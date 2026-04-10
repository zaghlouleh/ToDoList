<template>
  <div id="app">
    <div class="container">
      <h1>ToDo VUE</h1>
      <input class="input" v-model="newToDo" />
      <button class="add-button" v-on:click="add()">Add</button>
      <button class="delete-butten" @click="deleteAllToDo(i)">X</button>
      <ul style="list-style-type: none;">
        <li v-for="(todo,i) in existingToDo" :key="i">
          <span> {{ i + 1 }} {{ todo.text }} </span>
          <button class="delete-butten" @click="deleteToDo(i)">X</button>
        </li>
      </ul>
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
        { text: 'walkg dog', id: 2 },
      ],
    };
  },
  methods: {
    add() {
      this.existingToDo.push({
        text: this.newToDo,
        id: new Date().valueOf(),
      }),
        (this.newToDo = "");
    },
    deleteToDo(i) {
      this.existingToDo.splice(i, 1);
    },
      deleteAllToDo(i) {
      this.existingToDo.splice(i);
    },
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Nunito:wght@200;300;400;600;700&display=swap');
*{
    font-family: 'Nunito' sans-serif;
    margin: 0;
    padding: 0;
    text-transform: capitalize;
    box-sizing: border-box;
    outline: none;
    text-decoration: none;
}
.container{
    max-width: 700px;
    width: 100%;
    background: #fff;
    padding: 25px 30px;
    border-radius: 5px;
}
.delete-butten input{
    height: 100%;
    width: 100%;
    outline: none;
    color: #fff;
    background:linear-gradient(135deg, #71b7e6, #9b59b6) ;
    border: none;
    font-size: 18px;
    font-weight: 500;
    letter-spacing: 1px;
    border-radius: 5px;
}
.delete-butten input:hover{
    background:  linear-gradient(-135deg, #71b7e6, #9b59b6);
}
#app{
    display: flex;
    height: 100vh;
    justify-content: center;
    align-items: center;
    padding: 10px;
    background: linear-gradient(135deg, #71b7e6, #9b59b6);
}
body{
    display: flex;
    height: 100vh;
    justify-content: center;
    align-items: center;
    padding: 10px;
    background: linear-gradient(135deg, #71b7e6, #9b59b6);
}
</style>