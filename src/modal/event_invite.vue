<template>
  <transition name="modal-fade">
    <div class="modal-backdrop bg-mask event_invite_modal_position" v-on:click.self="userProfileBackdrop">
      <div class="event_invite_modal"
        role="dialog"
        aria-labelledby="modalTitle"
        aria-describedby="modalDescription"
      >
        <header
          class="event_invite_body"
          id="modalTitle"
        >
            <p class="medium_1_title">TOMORROW   7:00 AM</p>
              <p class="medium_title">Let’s All win the Market!!<br>Start Learning today!</p>
              
              <p class="event_invite_para"><span>from</span><img src="triangle.png" class="favicon_img"><span class="event_para_small">MAKING BIG TIME MONEY 101...</span></p>
              <hr class="event_invite_hr">
              <div class="event_user event_user_img">
                <img src="Jean_Smith.png">
                <img src="George Dy.png">
                <img src="Alex Smith.png">
                <img src="Susan Boyle.png">
                <img src="Peter Rogers.png">
              </div>
              <p class="event_invite_para"><span class="event_para_small">with Jean Smith, George Dy, Alex Smith, Susan Boyle, Peter Rogers</span></p>
              <hr class="event_invite_hr">
              <p class="event_invite_title">Invite 1,000 people to your Event!</p>
              <div class="event_invite_url">
                      <input type="text" placeholder="" class="form-control" v-model="promotion_link">
              </div>
              <div class="event_user link_img_margin">
                <p><img src="share.png"><br><span>Share</span></p>
                <p><img src="tweet.png"><br><span>Tweet</span></p>
                <p><img src="copy_link.png" @click="copyLink"><br><span>Copy Link</span></p>
                <p><img src="add_tocal.png"><br><span>Add to Cal</span></p>
              </div>
        </header>
      </div>
    </div>
  </transition>
</template>

<script>
  export default {
    name: 'Event_Invite',
    data() {
      return {
        promotion_link: "www.goldenlinkplus.com"
      }
    },
    methods: {
      close() {
        this.$emit('close');
      },
      userProfileBackdrop(evt) {
        if(evt.target.classList.length > 0 && "bg-mask"){
          this.$emit('user-backdrop');
        }
      },
      copyLink: function () {
        this.$copyText(this.promotion_link).then(function (e) {
        }, function (e) {
        })
      }
    }
  };
</script>
<style>
    .header_event {
    border-radius: 30px;
  }
  .event_invite_hr {
    margin: 10px 20px 20px;
  }
  .event_invite_para {
    margin: 10px 20px;
    display: inline-block;
    font-size: 16px;
  }
  .event_invite_para img {
    margin: 0 5px 0 10px;
  }
  .event_invite_para span {
    font-size: 16px;
  }
  .event_invite_para .event_para_small {
    font-size: 14px;
    letter-spacing: 0.05em;
  }
  .event_user {
    margin: 0 20px;
    text-align: center;
    display: flex;
  }
  .event_invite_title {
    color: #F4992D;
    font-size: 18px;
    margin: 0 20px;
  }
  .event_invite_url {
    margin: 10px 20px 20px;
  }
  .event_invite_url input {
    height: 50px;
    padding: 0 38px;
    background-color: #F4F9FE;
    border: 0 solid white;
    border-radius: 12px;
  }
  .event_user p {
    margin: auto;
  }
  .event_user span {
    margin-top: 10px;
    display: block;
  }
  .event_done {
    border-radius: 30px;
    background-color: #F4992D;
    color: white;
    padding: 8px 50px;
    margin: 30px auto;
    display: -webkit-box;
    display: -ms-flexbox;
    display: flex;
  }
  .medium_1_title img {
    float: right;
    margin-top: 5px;
  }
  .event_invite_position {
    text-align: left;
    overflow: auto;
    height: 1000px;
    background: white;
    border-radius: 0;
    width: 100%;
  }
  .each_height {
    height: 1000px !important;
  }
  .modal_event_transform {
    transform: translate(0, 25%) !important;
  }
  .event_invite_modal {
    transform: translate(0, 0) !important;
    max-width: 414px;
    width: 100%;
  }
  .event_invite_modal_position {
    align-items: flex-end !important;
  }
  .event_invite_body {
    text-align: left;
    overflow: auto;
    height: 100%;
    background: white;
    border-radius: 12px 12px 0 0;
    width: 100%;
    max-width: 414px;
  }
  .link_img_margin {
    margin-bottom: 20px;
  }
  .event_user_img img {
    margin: auto;
  }
</style>
