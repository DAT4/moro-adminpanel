<template>
    <div class="box col align-items-center">
        <h1>Login</h1>
        <p> Please enter your login and password!</p> 
        <input type="text" v-model="user.username"> 
        <input type="password" v-model="user.password"> 
        <input type="submit" value="Login" v-on:click="login">
    </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Login',
  data() {
      return {
          user: {
              username: '',
              password: '',
              authenticated: false,
          },
          token: '',
      }
  },
  props: {
    msg: String
  },
  methods: {
      async login() {
          const res = await axios.post('https://tmp.mama.sh/api/login', this.user);
          this.user.authenticated = true;
          this.token = res.data.token;
          window.localStorage['moroToken'] = res.data.token;
      },
  }
}
</script>

<style scoped>
@import url('https://fonts.googleapis.com/css?family=Anton');

.box {
    background: rgba(25,25,25,0.40);
    transition: 0.25s;
    border-radius: 24px;
    padding: 20px ;
    color: #CCFFC8;
}

.box input[type="text"],
.box input[type="password"] {
    border: 0;
    background: none;
    display: block;
    margin: 20px auto;
    text-align: center;
    border: 2px solid #CE93D8;
    padding: 10px 10px;
    width: 250px;
    outline: none;
    color: #CE93D8;
    border-radius: 24px;
    transition: 0.25s
}

.box h1 {
    font-family: 'Anton', sans-serif;
    font-size: 72px;
    color: #CE93D8;
    text-transform: uppercase;
    font-weight: 500
}

.box input[type="text"]:focus,
.box input[type="password"]:focus {
    color: #CCFFC8;
    width: 100%;
    border-color: #CCFFC8;
}

.box input[type="submit"] {
    border: 0;
    background: none;
    display: block;
    margin: 20px auto;
    text-align: center;
    border: 2px solid #CCFFC8;
    width: 250px;
    padding: 10px 10px;
    outline: none;
    color: #CCFFC8;
    border-radius: 24px;
    transition: 0.25s;
    cursor: pointer
}

.box input[type="submit"]:hover {
    background: #CCFFC8;
    transition: 0.50s;
    color: #CE93D8;
}

</style>
