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
  color: #2c3e50;
  margin-top: 60px;
}

.section {
  display: flex;
  flex-direction: column;
  justify-content: flex-start;
}

ul {
  list-style: none;
  display: flex;
  justify-content: flex-start;
  background-color: red;
}

li {
  text-decoration: none;
}
</style>
