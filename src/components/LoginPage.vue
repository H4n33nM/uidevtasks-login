<template>
  <link href='https://fonts.googleapis.com/css?family=Poppins' rel='stylesheet'>
  <link href='https://fonts.googleapis.com/css?family=Avenir' rel='stylesheet'>

  <div class="login-container">
    <!--login form-->
    <div class="login-form">
      <form @submit.prevent="handleLogin">
        <h1>Welcome back!</h1>
        <div class="alternate-login">
          <button class="alt"><img :src="google" alt="Google" class="icon" />Continue with Google</button>
          <button class="alt"><img :src="twitter" alt="Twitter" class="icon" />Continue with Twitter</button>
        </div>
        <hr class="divider">
        Enter your email address
        <input v-model="email" type="email">
        Enter your password
        <div class="password-input">
          <input v-model="password" :type="passwordVisible ? 'text' : 'password'">
          <button type="button" @click="togglePasswordVisibility">
            <img :src="passwordVisible ? hideIcon : showIcon" alt="Toggle Password Visibility" />
            {{ passwordVisible ? 'Hide' : 'Show' }}
          </button>
        </div>
        <span class="hyperlink">Forgot your password?</span>
        <button class="sign-in" type="submit">Sign In</button>
      </form>
      <p>Don't have an account? <span class="hyperlink">Sign up here!</span></p>
    </div>

    <!--image-->
    <div class="image">
      <h1 id="image-text">Work with us</h1>
      <span id="placeholder">Lorem ipsum dolor sit amet,
        consectetur adipiscing elit. Morbi
        lobortis maximus nunc, ac rhoncus odio
        congue quis. Sed ac semper orci, eu
        porttitor lacus. </span>
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
      google: require('@/assets/google.png'),
      twitter: require('@/assets/twitter.png'),
      showIcon: require('@/assets/show.png'),
      hideIcon: require('@/assets/hide.png'),
      email: '',
      password: '',
      passwordVisible: false
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
    },
    togglePasswordVisibility() {
      this.passwordVisible = !this.passwordVisible;
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

#image-text {
  position: absolute;
  right: 1450px;
  bottom: 595px;
  z-index: 2;
  color: #ffffff;
  font-size: 56px;
}

#placeholder {
  position: absolute;
  right: 1330px;
  bottom: 450px;
  padding-left: 95px;
  z-index: 2;
  color: #ffffff;
  font-size: 24px;
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

.password-input {
  display: flex;
  align-items: center;
}

button {
  display: flex;
  align-items: center;
  padding: 8px;
  background: none;
  border: none;
  cursor: pointer;
  transition-duration: 0.3s;
  font-family: 'Poppins';
}

button img {
  width: 24px;
  height: 24px;
  margin-right: 5px;
}

button:hover {
  color: #997825;
  /* Change text color on hover */
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

.icon {
  position: absolute;
  right: 770px;
  padding: 1px;
}
</style>
