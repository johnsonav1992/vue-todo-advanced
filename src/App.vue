<template>
  <h1>Vue Todo List</h1>
  <form action="submit">
				<input
					type="text"
					v-model="textInput"
					placeholder="Type a todo item"
				/>
				<button @click="addTodo">+</button>
			</form>
			<section class="section">
				<ul>
					<li v-for="todo in todoList" :key="todo">
						{{ todo }} <button @click="deleteTodo(todo)">-</button>
					</li>
				</ul>
			</section>
</template>

<script>

export default {
  data() {
    return {
      todoList: [],
      textInput: ''
    }
  },
  methods: {
    addTodo(e) {
            e.preventDefault()
            if (this.textInput === '') return
            this.todoList.push(this.textInput)
            this.textInput = ''
        },
        deleteTodo(todo) {
            const todoIndex = this.todoList.indexOf(todo)
            this.todoList.splice(todoIndex, 1)
        }
  },
  name: 'App',
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  margin-top: 60px;
}

body {
  background-color: gray;
}

h1 {
  color: #3eb27f;
  font-weight: bold;
  text-shadow: 1px 1px 5px rgb(31, 30, 30);
}

.section {
  display: flex;
  flex-direction: column;
  justify-content: center;
  width: 100vw;
}

form {
  display: flex;
  align-items: center;
  gap: .75rem;
}

input {
  border-color: transparent;
  border-radius: 1rem;
  padding: .25rem;
}

input:focus {
  outline-color:#3eb27f ;
}

button {
  margin: 0;
  border: none;
  border-radius: 50%;
  height: 25px;
  width: 25px;
}

button:hover {
  cursor: pointer;
  background-color: #3eb27f;
}

ul {
  list-style: none;
  display: flex;
  justify-content: center;
  margin: 0;
  padding: 0;
}

li {
  text-decoration: none;
}
</style>
