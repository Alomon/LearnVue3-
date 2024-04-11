<template>
  <form v-if="!token" class="m-4">
    <p class="m-2" v-if="error">{{error}}</p>
    <input v-model="username" class="form-control m-2" type="text" name="username" placeholder="Введи логин">
    <input v-model="password" class="form-control m-2" type="password" name="password" placeholder="Введи пароль">
    <button @click="singIn" class="btn btn-info m-2">Вход</button>

  </form>
  <p v-if="token">Вы авторизированны!</p>
</template>

<script>
 export default {
   data() {
     return {
       token: localStorage.getItem('token') || null,
       username: null,
       password: null,
       error: null,
     }
   },
   methods: {
     singIn(event){
       this.error = null;
       event.preventDefault();
       fetch('https://dummyjson.com/auth/login', {
         method: 'POST',
         headers: {'Content-Type': 'application/json'},
         body: JSON.stringify({
           username: this.username,
           password: this.password,
           expiresInMins: 30,
         })
       })
           .then( response => response.json() )
           .then( data => {
             if(data.message) {
                   this.error = data.message;
             } else {
               this.token = data.token;
               localStorage.setItem('token', data.token);
             }
           })

     }
   }
 }
</script>

/*"username": "kdulyt",
"password": "5t6q4KC7O",*/