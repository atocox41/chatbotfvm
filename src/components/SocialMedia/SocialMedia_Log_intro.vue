<template>
  <div>
    <div class="container">
      <div class="phone sociallogin">
        <div class="glplogo_reg">
          <router-link to="/"><img src="glplogo.png" class="glplogo_reg_img">
          </router-link>
          <p class="glplogo_reg_p">Enter your phone number</p>
            <div class="container mb-3">
              <div class="flex flex-wrap">
                <div class="component-container">
                  <div class="component mb-2">
                    <VuePhoneNumberInput v-model="phoneNumber" placeholder="" class="phone_num_input"/>
                  </div>
                </div>
              </div>
            </div>
            <p class="validation_desc">Please use a valid phone number, not a VoIP or landline number.</p>
          <p class="glplogo_reg_validate">By entering your number, you're agreeing to our <b>Terms of Sevice</b> and <b>Privacy Policy</b>.</p>
          <div class="sociallogo_btn">
            <router-link to="/socialmedia/socialmedia_log_verify">
              <button class="glplogo_reg_btn">Next <img class="glplogo_reg_btn_img" src="reg_next.png"/>
              </button>
            </router-link>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
// import Vue from 'vue'; 
import VuePhoneNumberInput from 'vue-phone-number-input';
import 'vue-phone-number-input/dist/vue-phone-number-input.css';

// Vue.use(VuePhoneNumberInput)

export default {
  name: 'SocialMedia_Log_intro',
  components: {
    VuePhoneNumberInput
  },
  data() {
      return {
        phoneNumber: null
      }
  },
  computed: {
      resultsTable () {
        return Object.keys(this.results)
      },
      resultsTable2 () {
        return Object.keys(this.results2)
      },
      resultsTable3 () {
        return Object.keys(this.results3)
      }
  },
  methods: {
      onUpdate (payload) {
        this.results = payload
      },
      onUpdate2 (payload) {
        this.results2 = payload
      },
      onUpdate3 (payload) {
        this.results3 = payload
      }
  }
}
</script>
<style>
  .glplogo_reg {
    text-align: left;
    width: 100%;
    margin: 30px 40px;
  }
  .glplogo_reg_p {
    margin: 0 0 10px 0;
  }
  .glplogo_reg_img {
    margin: 250px 0 30px 0;
  }
  .social_input {
    border-radius: 12px !important;
    border: 0 solid white !important;
    margin-bottom: 20px;
    background-color: #F4F9FE !important;
  }
  .glplogo_reg_validate {
    font-size: 14px;
    margin: 20px 0 0;
  }
  .glplogo_reg_btn {
    background-color: #F4992D;
    color: white;
    padding: 8px 50px;
    border-radius: 30px;
    font-size: 18px;
    margin: 20px auto;
  }
  .glplogo_reg_btn_img {
    margin: 0 0 2px 10px;
  }
  .input-tel__input {
    border-radius: 20px;
  }
  .validation_desc {
    color: #FF0000;
    font-size: 10px;
    margin: 0 auto;
    text-align: center;
  }
  .mb-3 {
    margin-bottom: 0 !important;
  }
</style>

