<template>
    <div class="card mt-3">
      <div class="card-body">
          <div class="card-title">
              <h3>Chat Group</h3>
              <hr>
          </div>
          <div class="card-body">
              <div class="messages" v-for="(msg, index) in messages" :key="index">
                  <p><span class="font-weight-bold">{{ msg.user }}: </span>{{ msg.message }}</p>
              </div>
          </div>
      </div>
      <div class="card-footer">
          <form @submit.prevent="sendMessage">
              <div class="gorm-group pb-3">
                  <label for="message">Message:</label>
                  <input type="text" v-model="message" class="form-control">
              </div>
              <button type="submit" class="btn btn-success">Send</button>
          </form>
      </div>
  </div>
</template>

<script>
    export default {

        async created(){
            var urlParams = new URLSearchParams(window.location.search);
            var token =  urlParams.get("token");
            window.localStorage.setItem("Auth",token) 
            var response = await window.fetch("http://localhost:3000/user", { headers: {authorization: this.token}, mode: 'cors', method: "GET"})
            var user = await response.json()
            console.log(user)
        },

        data() {
            return {
            user: '',
            message: '',
            messages: []
          }
        },

        methods: {
            sendMessage(e) {
                e.preventDefault();
            }
        },
    }
</script>
