<template>
  <div>
    <div class="container">
      <div class="phone sociallogin" v-show="!isloading">
        
          <div class="event_body_title">
            <p class="event_favicon_img"><img src="triangle.png">MAKING BIG TIME MONEY 101<img src="lock.png" class="event_room_lock"></p>
            <p class="event_desc">Let’s All win the Market!! Start<br>Learning today!</p>
            
              <p class="event_back">
                <router-link to="/socialmedia/socialmedia_main_event_hallway">
                  <img src="event_back.png">Go to Hallway
                </router-link>
              <span @click="showEventSetting"><img src="img/dots.png"></span></p>
          </div>
          <div class="event_body">
            <p class="promotional_text">Promotional text goes here</p>
            <div class="event_user_group">
              <div v-for="(item, index) in datas" :key="index" class="event_each_user">
                <div class="event_icon">
                    <img v-if="isAddingCoin" class="blink-img"  :class="{'blinkingUser': item.blink == true}" src="coin_10.png"  @click="showBlinkItem(index)">
                    <img v-if="!isAddingCoin" class="diamond-img"  :class="{'diamondAppear': item.diamondActive == true}" src="frame_diamond2.png"  @dblclick="showDiamondItem(index)">
                    <img :src="`${item.image_url}`" :class="{'user_logo_border': item.active == true}">
                    <div>
                        <img src="pink_star.png" v-if="item.star" class="event_star">
                        <img src="mute.png" v-if="item.mute" class="event_mute">
                        <img src="diamond.png" v-if="item.diamond" class="event_diamond">
                    </div>
                </div>
                <p class="coin_letter"><img src="event_user_coin.png" class="event_user_coin"><span>{{item.event_user_coin}}K</span></p>
                <p class="coin_letter"><img src="event_user_diamond.png" class="event_user_coin"><span>{{item.event_user_diamond}}</span></p>
                <p>{{item.name}}</p>
              </div>
            </div>

            <div class="event_ranking">
              <button class="audience_btn" :class="{'border_btn': isAudience == true}" @click="showAudience"><b>Audience</b></button>
              <button class="speakers_btn" :class="{'border_btn': isAudience != true}" @click="showSpeakers"><b>Speakers</b></button>
            </div>

            <div v-if="isAudience == true" class="coin_letter">
            <p class="event_ranking_title">Top 18 GCoins sent by audience</p>
            </div>
            <div v-else class="coin_letter">
            <p class="event_ranking_title">Top 5 GCoins sent by speakers</p>
            </div>

            <div v-if="isAudience == true">
              <div v-for="(item, index) in rangking1" :key="index" class="rangking_data">
                <img :src="`${item.rangking_image}`">
                <p>{{item.rangking_name}}<span>{{item.rangking_coin}}</span></p>
              </div>
            </div>
            <div v-else>
              <div v-for="(item, index) in rangking2" :key="index" class="rangking_data">
                <img :src="`${item.rangking_image}`">
                <p>{{item.rangking_name}}<span>{{item.rangking_coin}}</span></p>
              </div>
            </div>

            <div class="event_mute_group">
              <div v-for="(item, index) in mutedata" :key="index" class="mute_user">
                
                <div class="mute_icon">
                  <img :src="`${item.mute_image}`" class="mute_user_img">
                </div>
                <p>{{item.mute_user}}</p>
              </div>
            </div>
          </div>
          <div class="footer_background">
            <div class="footer_modal" v-show="!isAddingCoin">
                <router-link to="/socialmedia/socialmedia_main">
                    <span class="footer_img_rest_left">
                        <img src="Leave_Quietly.png">
                        <p>Leave Quietly</p>
                    </span>
                </router-link>
                <span class="footer_img_rest_left">
                    <router-link to="/socialmedia/socialmedia_main_event_chat">
                        <img src="chat.png">
                    </router-link>
                    <p>Chat</p>
                </span>
                <button class="audio_circle_btn"  @click="imgClicked = !imgClicked" v-on:click ="clicked = !clicked">
                    <img :src="imgSrc"/>
                </button>
                <span class="footer_img_rest_right"  @click="showInvite">
                    <img src="invite.png">
                    <p>Invite</p>
                </span>
                <span class="footer_img_rest_right" @click="showSendGcoin">
                    <img src="send_gcoins.png">
                    <p>Send GCoins</p>
                </span>
            </div>
                <img src="handsup.png" class="handsup_modal" @click="showHostView">
            <div class="footer_modal footer_modal_border" v-show="isAddingCoin">
                <button class="send_coin_btn "><img src="modal_coin.png">115, 250</button>
                <div class="charge_close" @click="doneAddingCoin">
                    <img src="cancel_coin.png">
                    <span>Close</span>
                </div>
            </div>
          </div>
          <SendGcoin 
            v-show="f_show_send_gcoin"
            @user-backdrop="removeFlagFromStack"
          >
          </SendGcoin>
          <vuedal></vuedal>
          <UserProfile 
            v-show="f_show_user_profile"
            @user-backdrop="removeFlagFromStack"
          >
          </UserProfile>
          <HostView 
            v-show="f_show_host_view"
            @user-backdrop="removeFlagFromStack"
          >
          </HostView>
          <Invite 
            v-show="f_show_invite"
            @user-backdrop="removeFlagFromStack"
          >
          </Invite>
          <Price 
            v-show="f_show_price"
            @user-backdrop="removeFlagFromStack"
          >
          </Price>
          <Supporter 
            v-show="f_show_supporter"
            @user-backdrop="removeFlagFromStack"
          >
          </Supporter>
          <EventSetting 
            v-show="f_show_event_setting"
            @close="closeEventSetting"
            @user-backdrop="removeFlagFromStack"
          >
          </EventSetting>
          <UpcomingEvent 
            v-show="f_show_upcoming_event"
            @close="closeUpcomingEvent"
            @view-backdrop="closeUpcomingEvent"
          >
          </UpcomingEvent>
      </div>
    </div>
  </div>

</template>

<script>
import { default as Vuedals, Component as Vuedal, Bus as VuedalsBus } from 'vuedals';
import UserProfile from "../../modal/user_profile.vue";
import SendGcoin from "../../modal/send_gcoin.vue";
import HostView from "../../modal/host_view.vue";
import Invite from "../../modal/invite.vue";
import Price from "../../modal/price.vue";
import Supporter from "../../modal/supporter.vue";
import EventSetting from "../../modal/event_setting.vue";
import UpcomingEvent from "../../modal/event_invite.vue";

export default {
  name: 'Event_Quick',
  components: {
      Vuedal,
      UserProfile,
      SendGcoin,
      HostView,
      Invite,
      Price,
      Supporter,
      EventSetting,
      UpcomingEvent
  },
  data () {
    return {
        isAddingCoin: false,
        isBlink: false,
        isDiamond: false,
        isBlink1: false,
        isloading: true,
        isModalVisible: false,
        clicked: false,
        imgClicked: false,
        isAudience: true,
        f_show_user_profile: false,
        f_show_send_gcoin: false,
        f_show_host_view: false,
        f_show_invite: false,
        f_show_supporter: false,
        f_show_price: false,
        f_show_event_setting: false,
        f_show_upcoming_event: false,
        modalStack: [],
        datas: [
            {
              image_url: "shane.png",
              star: true,
              mute: true,
              diamond: true,
              active: false,
              blink: false,
              event_user_coin: 892,
              event_user_diamond: 526,
              name: "Shane",
              diamondActive: false
            },
            {
              image_url: "eduardo.png",
              star: false,
              mute: false,
              diamond: true,
              active: true,
              blink: false,
              event_user_coin: 484.2,
              event_user_diamond: 526,
              name: "Kristin",
              diamondActive: false
            },
            {
              image_url: "leslie.png",
              star: true,
              mute: true,
              diamond: true,
              active: false,
              blink: false,
              event_user_coin: 345.6,
              event_user_diamond: 526,
              name: "Leslie",
              diamondActive: false
            },
            {
              image_url: "eduardo.png",
              star: true,
              mute: true,
              diamond: true,
              active: false,
              blink: false,
              event_user_coin: 527.1,
              event_user_diamond: 526,
              name: "Eduardo",
              diamondActive: false
            },
            {
              image_url: "eduardo.png",
              star: false,
              mute: true,
              diamond: true,
              active: true,
              blink: false,
              event_user_coin: 78.5,
              event_user_diamond: 526,
              name: "Jorge",
              diamondActive: false
            },
            {
              image_url: "esther.png",
              star: true,
              mute: true,
              diamond: true,
              active: false,
              blink: false,
              event_user_coin: 18.9,
              event_user_diamond: 526,
              name: "Esther",
              diamondActive: false
            },
            {
              image_url: "leslie.png",
              star: false,
              mute: true,
              diamond: true,
              active: false,
              blink: false,
              event_user_coin: 27.5,
              event_user_diamond: 526,
              name: "Tanya",
              diamondActive: false
            },
            {
              image_url: "shane.png",
              star: false,
              mute: true,
              diamond: true,
              active: false,
              blink: false,
              event_user_coin: 38.8,
              event_user_diamond: 526,
              name: "Ronald",
              diamondActive: false
            },
            {
              image_url: "esther.png",
              star: false,
              mute: true,
              diamond: true,
              active: false,
              blink: false,
              event_user_coin: 190.5,
              event_user_diamond: 526,
              name: "Philip",
              diamondActive: false
            },
        ],
        rangking2: [
            {
              rangking_image: "Ray.png",
              rangking_name: "Virginia Jones",
              rangking_coin: "915.6K",
            },
            {
              rangking_image: "mona.png",
              rangking_name: "Lavern Laboy",
              rangking_coin: "847.3K",
            },
            {
              rangking_image: "Jean_Smith.png",
              rangking_name: "Annette Black",
              rangking_coin: "654.2K",
            },
            {
              rangking_image: "Richard_Bennett_off.png",
              rangking_name: "Darron Kowski",
              rangking_coin: "302.8K",
            },
            {
              rangking_image: "Susan Boyle.png",
              rangking_name: "Robert Fox",
              rangking_coin: "113.3K",
            },
        ],
        rangking1: [
            {
              rangking_image: "Ray.png",
              rangking_name: "Erin Hughes",
              rangking_coin: "876.5K",
            },
            {
              rangking_image: "mona.png",
              rangking_name: "Marvin McKinney",
              rangking_coin: "678.6K",
            },
            {
              rangking_image: "Jean_Smith.png",
              rangking_name: "Lucy Fletcher",
              rangking_coin: "582.3K",
            },
            {
              rangking_image: "Richard_Bennett_off.png",
              rangking_name: "Ronald Richards",
              rangking_coin: "76.5K",
            },
            {
              rangking_image: "Susan Boyle.png",
              rangking_name: "Kathryn Murphy",
              rangking_coin: "24K",
            },
            {
              rangking_image: "Alex Smith.png",
              rangking_name: "Emily Malone",
              rangking_coin: "18.5K",
            },
            {
              rangking_image: "Collen.png",
              rangking_name: "Patricia Clark",
              rangking_coin: "12.9K",
            },
            {
              rangking_image: "Grandma.png",
              rangking_name: "Jerome Bell",
              rangking_coin: "6.7K",
            },
            {
              rangking_image: "Irma.png",
              rangking_name: "Floyd Miles",
              rangking_coin: "5.9K",
            },
            {
              rangking_image: "Lily.png",
              rangking_name: "Mary Lopez",
              rangking_coin: "3.6K",
            },
            {
              rangking_image: "Kathry.png",
              rangking_name: "Amanda Rice",
              rangking_coin: "3.2K",
            },
            {
              rangking_image: "Judith.png",
              rangking_name: "Lydia Sharp",
              rangking_coin: "1.1K",
            },
            {
              rangking_image: "Priscilla.png",
              rangking_name: "Darrell Steward",
              rangking_coin: "546",
            },
            {
              rangking_image: "Serenity.png",
              rangking_name: "Ida Baldwin",
              rangking_coin: "404",
            },
            {
              rangking_image: "Savannah.png",
              rangking_name: "Jacob Jones",
              rangking_coin: "395",
            },
            {
              rangking_image: "Wendy.png",
              rangking_name: "Linda Carroll",
              rangking_coin: "375",
            },
            {
              rangking_image: "Susan Boyle.png",
              rangking_name: "Ruth West",
              rangking_coin: "210",
            },
            {
              rangking_image: "Philip.png",
              rangking_name: "Cody Fisher",
              rangking_coin: "75",
            },
        ],
        mutedata: [
            {
              mute_image: "Irma.png",
              mute_user: "Pat",
            },
            {
              mute_image: "Wendy.png",
              mute_user: "Wendy",
            },
            {
              mute_image: "Irma.png",
              mute_user: "Tanya",
            },
            {
              mute_image: "Wendy.png",
              mute_user: "Marvin",
            },
            {
              mute_image: "Irma.png",
              mute_user: "Pat",
            },
            {
              mute_image: "Wendy.png",
              mute_user: "Wendy",
            },
            {
              mute_image: "Irma.png",
              mute_user: "Tanya",
            },
            {
              mute_image: "Wendy.png",
              mute_user: "Marvin",
            },
        ]
    }
  },
  
  methods: {
    addingCoin() {
        this.isAddingCoin = true;
        this.f_show_send_gcoin = false;
    },
    doneAddingCoin() {
        this.isAddingCoin = false;
    },
    showBlinkItem(index) {
        if (this.isAddingCoin) {
            this.datas[index].blink = true
            setTimeout(() => {
                this.datas[index].blink = false
            }, 2000)
        }
    },
    showDiamondItem(index) {
        if (!this.isAddingCoin) {
            this.datas[index].diamondActive = true
            setTimeout(() => {
                this.datas[index].diamondActive = false
            }, 2000)
        }
    },
    showBlink() {
        if (this.isAddingCoin) {
            this.isBlink = true
            setTimeout(() => {
                this.isBlink = false
            }, 2000)
        }
    },
    showBlink1() {
        if (this.isAddingCoin) {
            this.isBlink1 = true
            setTimeout(() => {
                this.isBlink1 = false
            }, 2000)
        } 
    },
    killLoading() {
      setTimeout(() => {
          this.isloading = false
      }, 2000)
    },
    showIt() {
        Vuedals.$emit('new', {
            name: 'showing-the-money',

            component: {
                name: 'the-money',

                template: `
                    <div>
                        <h1>THE MONEY!</h1>
                        <p>Money, money, money, moooneeyyy $ $ $ $</p>
                    </div>
                `
              }
            });
    },
    showAudience() {
      this.isAudience = true;
    },
    showSpeakers() {
      this.isAudience = false;
    },
    showModal() {
      this.isModalVisible = true;
    },
    closeUserProfileModal() {
      this.isModalVisible = false;
    },
    closeSendGcoinModal() {
      this.isModalVisible = false;
    },
    closeHostViewModal() {
      this.isModalVisible = false;
    },
    removeFlagFromStack() {

      let temp = this.modalStack.pop(-1);

      switch (temp) {
        case 'f_show_send_gcoin':
          this.f_show_send_gcoin = false
          break;
        default:
          // statements_def
          break;
      }
      switch (temp) {
        case 'f_show_user_profile':
          this.f_show_user_profile = false
          break;
        default:
          // statements_def
          break;
      }
      switch (temp) {
        case 'f_show_host_view':
          this.f_show_host_view = false
          break;
        default:
          // statements_def
          break;
      }
      switch (temp) {
        case 'f_show_invite':
          this.f_show_invite = false
          break;
        default:
          // statements_def
          break;
      }
      switch (temp) {
        case 'f_show_price':
          this.f_show_price = false
          break;
        default:
          break;
      }
      switch (temp) {
        case 'f_show_supporter':
          this.f_show_supporter = false
          break;
        default:
          break;
      }
      switch (temp) {
        case 'f_show_event_setting':
          this.f_show_event_setting = false
          break;
        default:
          break;
      }
      this.f_show_send_gcoin = false,

      this.f_show_user_profile = false,

      this.f_show_invite = false,

      this.f_show_host_view = false,

      this.f_show_price = false,

      this.f_show_supporter = false,

      this.f_show_event_setting = false
    },
    showUserProfile() {
        if (!this.isAddingCoin) {
            this.f_show_user_profile = true;
            this.modalStack.push('f_show_user_profile');
        } else {
            this.isAddingCoin = true
        }
    },
    showSendGcoin() {
      this.f_show_send_gcoin = true;
      this.modalStack.push('f_show_send_gcoin');
    },
    showHostView() {
      this.f_show_host_view = true;
    },
    showInvite() {
      this.f_show_invite = true;
    },
    showPrice() {
        this.f_show_price = true;
        this.modalStack.push('f_show_price');
    },
    showSupporter() {
        this.f_show_supporter = true;
        this.modalStack.push('f_show_supporter');
    },
    showEventSetting() {
        this.f_show_event_setting = true;
        this.modalStack.push('f_show_event_setting');
    },
    ttt() {
      this.f_show_upcoming_event = true; // showing child
      this.f_show_invite = false;
      // this.$emit('close'); // disable myself to parent
    },
    closeEventSetting() {
        this.f_show_event_setting = false;
    },

    closeInviteModal() {
        this.f_show_invite = false;
    },
    closeUpcomingEvent() {
      this.f_show_upcoming_event = false;
    },
  },
  computed: {
    imgSrc: function () {
      return this.imgClicked ? 'Mic_Mute.png' : 'mute_large.png'
    },
  },
  created () {
    this.killLoading();
  },
  closeModal() {
      this.f_show_host_view = false;
      this.isModalVisible = false;
  },
}
</script>
<style>
  .participant_img {
    position: absolute;
    bottom: 47px;
    right: 10px;
  }
  .handsup_modal {
    position: absolute;
    top: 50px;
    right: 20px;
  }
</style>
