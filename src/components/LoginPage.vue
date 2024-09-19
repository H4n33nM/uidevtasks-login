<template>
  <link href='https://fonts.googleapis.com/css?family=Poppins' rel='stylesheet'>
  <div class="login-container">

    <!--login form-->
    <div class="login-form">
      <form @submit.prevent="handleLogin">
        <p>Enter your email address</p>
        <input v-model="email" type="email">
        <p>Enter your password</p>
        <input v-model="password" type="password">
        <button type="submit">Sign In</button>
      </form>
    </div>

    <!--image-->
    <div class="image">
      <img :src="flowersImage" alt="Flowers" />
      <div class="overlay"></div>
    </div>

  </div>
</template>


<script>
export default {
  name: 'LoginPage',
  data() {
    return {
      flowersImage: require('@/assets/flowers.png'),
      email: '',
      password: ''
    }
  },
  methods: {
    handleLogin() {
      if (this.email && this.password) {
        this.$emit('login', { email: this.email, password: this.password });
        this.email = '';
        this.password = '';
        alert('Login successful!');
      }
    }
  }
}
</script>


<style scoped>
.login-container {
  display: flex;
  flex-direction: row-reverse;
  width: 100vw;
  height: 100vh;
  font-family: 'Poppins';
  font-size: 16px;
  margin-top: 60px;
}

.image {
  display: flex;
  flex: 1;
}

.image img {
  position: relative;
  right: 8px;
  bottom: 60px;
  width: 720px;
  height: 1024px;
}

.overlay {
  position: absolute;
  top: 0px;
  left: 0px;
  width: 720px;
  height: 1024px;
  background-color: rgba(17, 17, 17, 0.25);
  z-index: 1;
}

.login-form {
  width: 50%;
  padding: 20px;
}

p {
  font-size: 16px;
  color: #666666;
  text-align: left;
}

input {
  display: block;
  border: 1px solid #66666659;
  border-radius: 12px;
  width: 568px;
  height: 30px;
  padding: 10px;
  margin-bottom: 15px;
  transition-duration: 0.3s;
}

input:hover {
  border: 1px solid #997825;
}

button {
  display: block;
  font-family: 'Poppins';
  font-size: 20px;
  color: #ffffff;
  background-color: #997825;
  border: 1px solid #997825;
  border-radius: 32px;
  width: 304px;
  height: 64px;
  margin-top: 35px;
  transition-duration: 0.3s;
}

button:hover {
  display: block;
  font-family: 'Poppins';
  font-size: 20px;
  color: #ffffff;
  background-color: #65501a;
  border: 1px solid #65501a;
  border-radius: 32px;
  width: 304px;
  height: 64px;
  margin-top: 35px;
}
</style>
