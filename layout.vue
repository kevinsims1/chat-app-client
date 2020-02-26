<template>
    <div class="card">
        <div class="sidenav">
            <a href="#">
                <div> 
                    {{this.curUsr.user.name}}
                </div>
                <div v-for="room in this.curUsr.rooms"
                     :key="room.id"> 
                    {{room.name}}
                </div>
            </a>
        </div>
        <slot />
    </div>
</template>

<script>
    export default {

        async created(){
            var urlParams = new URLSearchParams(window.location.search);
            var token =  urlParams.get("token");
            window.localStorage.setItem("Auth",token) 
            var response = await window.fetch("http://localhost:3000/user", { headers: {authorization: token}, mode: 'cors', method: "GET"})
            var cur = await response.json()
            this.curUsr = cur
            console.log(cur)
          },

        data(){
         return{
            curUsr: {}  
        } 
        },

        methods: {
            sendMessage(e) {
                e.preventDefault();
            }
        },
    }
</script>

<style scoped>
.card{
    height: 100vh;
    display: flex;
    flex-direction: row;
    overflow-y: hidden;
}

.sidenav {
    height: 100%; /* Full-height: remove this if you want "auto" height */
    width: 160px; /* Set the width of the sidebar */  
    top: 0; /* Stay at the top */
    left: 0;
    background-color: #111; /* Black */
    overflow-x: hidden; /* Disable horizontal scroll */
    padding-top: 20px;
}

/* The navigation menu links */
.sidenav a {
  text-decoration: none;
  font-size: 25px;
  color: #818181;
  display: block;
}

.sidenav a div {
  padding: .5rem;
  text-decoration: none;
  font-size: 25px;
  color: white;
  display: block;
}

/* When you mouse over the navigation links, change their color */
.sidenav a div:hover {
  color: red;
}

/* On smaller screens, where height is less than 450px, change the style of the sidebar (less padding and a smaller font size) */
@media screen and (max-height: 450px) {
  .sidenav {padding-top: 15px;}
  .sidenav a {font-size: 18px;}
}
</style>


