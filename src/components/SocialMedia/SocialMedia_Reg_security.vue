<template>
  <div>
    <div class="container">
      <div class="phone passcode">
        <div class="glplogo_reg_security">
          <p class="glplogo_reg_security_title"><b>Use TouchID to Sign up</b></p>
          <div class="glplogo_reg_signup">
            <p class="glplogo_reg_p">Enter your passcode</p>
            <input
              type="password"
              class="form-control social_input_password"
              v-model="passcode"
              aria-describedby=""
              placeholder=""
            />
            <p class="glplogo_reg_confirm">Confirm passcode</p>
            <input
              type="password"
              class="form-control social_input_password"
              v-model="repasscode"
              aria-describedby=""
              placeholder=""
            />
            <p class="email_validation" v-if="passcode != repasscode">Set Passcode failed!</p>
          </div>
          <div class="sociallogo_btn"><button><router-link to="/socialmedia/socialmedia_reg_verify" class="glplogo_reg_btn">Next <img class="glplogo_reg_btn_img" src="reg_next.png"/></router-link></button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>

export default {
  name: 'SocialMedia_Reg_security',
  components: {
  },
  data() {
      return {
        passcode: '',
        repasscode: ''
      }
  },
  methods: {
  }
}
</script>
<style>
  .passcode {
    background: white !important;
  }
  .glplogo_reg_security {
    text-align: center;
    width: 100%;
    margin: 30px 40px;
  }
  .glplogo_reg_p {
    margin: 0 0 10px 0;
  }
  .glplogo_reg_img {
    margin: 250px 0 30px 0;
  }
  .glplogo_reg_confirm {
    margin: 45px 0 10px 0;
  }
  .glplogo_reg_passcode {
    font-size: 14px;
    margin: 0 0 200px 0;
  }
  .glplogo_reg_btn_img {
    margin: 0 0 2px 10px;
  }
  .glplogo_reg_security_title {
    margin: 80px 0;
  }
  .glplogo_reg_signup {
    display: inline-block;
    margin: 0 0 60px 0;
  }
</style>
