<template>
    <div id="app-4">
  <ol>
    <li :key="todo.text" v-for="todo in todos">
      {{ todo.text }}
    </li>
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
    export default {
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
