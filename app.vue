<template>
    <div id="app-4">
  <ol>
    <Todo v-for="todo in todos" :todo="todo" :key="todo.text"/>
  </ol>

  <p>{{ message }}</p>
  <button @click="reverseMessage">Reverse Message</button>
  
  <div id="app-6">
    <p>{{ message }}</p>
    <input v-model="message">
</div>
</div>
</template>

<script>
    import Todo from "./todo"
    export default {
        components: {
            Todo
        },

        async created(){
            var urlParams = new URLSearchParams(window.location.search);
            var token =  urlParams.get("token"); 
            var response = await window.fetch("http://localhost:3000/user", { headers: {authorization: token}, mode: 'cors', method: "GET"})
            var user = await response.json()
            console.log(user)
        },

        data() {
            return {message: 'Hello Vue!',
                     todos: [
                        { text: 'Learn JavaScript' },
                        { text: 'Learn Vue' },
                        { text: 'Build something awesome' }
                    ]
                }
        },

        methods: {
          reverseMessage: function () {
            this.message = this.message.split('').reverse().join('')
          }
        }
    }
</script>
