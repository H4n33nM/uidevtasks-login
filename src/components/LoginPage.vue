<template>
  <link href='https://fonts.googleapis.com/css?family=Poppins' rel='stylesheet'>
  <link href='https://fonts.googleapis.com/css?family=Avenir' rel='stylesheet'>

  <div class="login-container">
    <!--login form-->
    <div class="login-form">
      <form @submit.prevent="handleLogin">
        <h1>Welcome back!</h1>
        <div class="alternate-login">
          <button class="alt">Continue with Google</button>
          <button class="alt">Continue with Twitter</button>
        </div>
        <hr class="divider">
        Enter your email address
        <input v-model="email" type="email">
        Enter your password
        <input v-model="password" type="password">
        <span class="hyperlink">Forgot your password?</span>
        <button class="sign-in" type="submit">Sign In</button>
      </form>
      <p>Don't have an account? <span class="hyperlink">Sign up here!</span></p>
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
h1 {
  color: #333333;
  font-size: 32px;
}

.login-container {
  display: flex;
  flex-direction: row-reverse;
  width: 100vw;
  height: 100vh;
  font-family: 'Poppins';
  font-size: 16px;
  margin-top: 60px;
  font-size: 16px;
  color: #666666;
  text-align: left;
}

/*Image*/
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

/*Login Form*/
hr.divider {
  border-top: 1px solid #66666640;
  width: 590px;
  position: absolute;
  top: 365px;
}

.login-form {
  width: 50%;
  padding: 20px;
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

.hyperlink {
  text-decoration: underline;
  color: #111111;
  text-align: center;
}

.hyperlink:hover {
  color: #0000ff;
}

.hyperlink:active {
  color: #ff0000;
}

.sign-in {
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

.sign-in:hover {
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

.alt {
  display: block;
  font-family: 'Avenir';
  font-size: 22px;
  color: #333333;
  background-color: #ffffff;
  border: 1px solid #333333;
  border-radius: 32px;
  width: 568px;
  height: 64px;
  margin-top: 35px;
  transition-duration: 0.3s;
}

.alt:hover {
  display: block;
  font-family: 'Avenir';
  font-size: 22px;
  color: #333333;
  background-color: #e1e1e1;
  border: 1px solid #333333;
  border-radius: 32px;
  width: 568px;
  height: 64px;
  margin-top: 35px;
}

.alternate-login {
  padding: 0px 10px 40px 10px;
}
</style>
