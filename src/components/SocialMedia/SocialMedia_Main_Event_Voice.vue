<template>
  <div>
    <div class="container">
      <div class="loading_screen" v-show="isloading" >
        <img src="loading_logo.png">
      </div>
      <div class="welcome_dialog loading_screen" v-if="gcoin_tap">
        <div class="welcome_dialog_content" @click="killGcoinTap">
          <img src="Won Gcoins.png">
          <p class="welcome_coin_title">
            <span class="welcome_dialog_title">Congratulations!</span>
            <span class="welcome_dialog_price">You received 20 G-Coins</span>
          </p>
        </div>
      </div>
      <div class="phone sociallogin" v-show="!isloading">
          <div class="event_body_title">
            <p class="event_favicon_img">
              <router-link to="/socialmedia/community/socialmedia_community">
                  <img src="triangle.png" class="favicon_img">MAKING BIG TIME MONEY 101
              </router-link>
              <img src="lock.png" class="event_room_lock">
            </p>
            <p class="event_desc">Let’s All win the Market!! Start<br>Learning today!</p>
            
              <p class="event_back">
                <router-link to="/socialmedia/socialmedia_main_event_hallway">
                  <img src="event_back.png">Hallway
                </router-link>
              <span @click="showEventSetting"><img src="img/dots.png"></span></p>
          </div>
          <div class="event_body">
            <p class="promotional_text">Promotional text goes here</p>
            <div class="event_users">
                <span class="blink_span">
                    <img v-if="isAddingCoin" class="blink-img"  :class="{'blinking': isBlink1 == true}" src="coin_10.png"  @click="showBlink1">
                    <img src="Jean.png" class="event_users_img" @click="showUserProfile">Jean
                </span>
                <span class="blink_span gcoin_animation">
                    <img src="50k_coin.png" class="event_coin" @click="showGCoinGrab" />

                    <img src="coin_animation.png" class="moving" v-if="gcoin_animation" />
                    <img src="coin_animation.png" class="moving" v-if="gcoin_animation" />
                    <img src="coin_animation.png" class="moving" v-if="gcoin_animation" />
                    <img src="coin_animation.png" class="moving" v-if="gcoin_animation" />
                    <img src="coin_animation.png" class="moving" v-if="gcoin_animation" />
                    <img src="coin_animation.png" class="moving" v-if="gcoin_animation" />
                    <img src="coin_animation.png" class="moving" v-if="gcoin_animation" />
                    <img src="coin_animation.png" class="moving" v-if="gcoin_animation" />

                    <button>00:14:59</button>
                </span>
                <div class="event_para_group">
                    <p>
                        <img src="user_count_grey.png"><span>25.2K</span>
                        <img src="msg_count_grey.png"><span>198</span>
                    </p>
                    <p><span>13.9 K</span><img src="event_voice_dia.png"></p>
                    <p><span>625.4 K</span><img src="event_coin.png"></p>
                    <p><img src="logo_group.png" class="event_voice_logo"></p>
                </div>
            </div>
            <div class="event_user_group">
              <div v-for="(item, index) in datas" :key="index" class="event_each_user">
                <div class="event_icon">
                    <img v-if="isAddingCoin" class="blink-img"  :class="{'blinkingUser': item.blink == true}" src="coin_10.png"  @click="showBlinkItem(index)">
                    <img v-if="!isAddingCoin" class="diamond-img"  :class="{'diamondAppear': item.diamondActive == true}" src="frame_diamond2.png" @dblclick="showDiamondItem(index)">
                    <img :src="`${item.image_url}`" :class="{'user_logo_border': item.active == true}">
                    <div>
                        <img src="pink_star.png" v-if="item.star" class="event_star">
                        <img src="mute.png" v-if="item.mute" class="event_mute">
                        <img src="diamond.png" v-if="item.diamond" class="event_diamond">
                    </div>
                </div>
                <p class="coin_letter" @click="showPrice"><img src="event_user_coin.png" class="event_user_coin"><span>{{item.event_user_coin}}K</span></p>
                <p class="coin_letter" @click="showPrice"><img src="event_user_diamond.png" class="event_user_coin"><span>{{item.event_user_diamond}}</span></p>
                <p>{{item.name}}</p>
              </div>
            </div>
            <div class="event_ranking">
              <button class="audience_btn" :class="{'border_btn': isAudience || (!isAudience&&!isSpeakers)}" @click="showAudience"><b>Audience</b></button>
              <button class="speakers_btn" :class="{'border_btn': isSpeakers|| (!isAudience&&!isSpeakers)}" @click="showSpeakers"><b>Speakers</b></button>
            </div>
            <div v-if="isAudience || isSpeakers">
              <div v-if="isAudience == true" class="coin_letter">
                <p class="event_ranking_title">Top 18 GCoins sent by audience</p>
              </div>
              <div v-if="isSpeakers == true" class="coin_letter">
                <p class="event_ranking_title">Top 5 GCoins sent by speakers</p>
              </div>

              <div v-if="isAudience == true">
                <div v-for="(item, index) in rangking1" :key="index" class="rangking_data">
                  <img :src="`${item.rangking_image}`">
                  <p>{{item.rangking_name}}<span>{{item.rangking_coin}}</span></p>
                </div>
              </div>
              <div v-if="isSpeakers == true">
                <div v-for="(item, index) in rangking2" :key="index" class="rangking_data">
                  <img :src="`${item.rangking_image}`">
                  <p>{{item.rangking_name}}<span>{{item.rangking_coin}}</span></p>
                </div>
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
                <button class="audio_circle_btn figure_btn"  @click="imgClicked = !imgClicked" v-bind:class="{'hand_orange': !clicked, 'hand_black': clicked}" v-on:click ="clicked = !clicked">
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
            <Invite 
                v-show="f_show_invite"
                @user-backdrop="removeFlagFromStack"
                @close="closeInviteModal"
                @share="ttt"
            >
            </Invite>
            <Price 
                v-show="f_show_price"
                @user-backdrop="removeFlagFromStack"
            >
            </Price>
            <EventSetting 
                v-show="f_show_event_setting"
                @close="closeEventSetting"
                @user-backdrop="removeFlagFromStack"
                @ShowGcoinPot="showGcoinPot"
                @ShowReport="showReport"
            >
            </EventSetting>
            <UpcomingEvent 
                v-show="f_show_upcoming_event"
                @close="closeUpcomingEvent"
                @view-backdrop="closeUpcomingEvent"
            >
            </UpcomingEvent>
            <GcoinPot 
                v-show="f_show_gcoin_pot"
                @user-backdrop="closeModal"
                @close="closeGcoinPot"
                @share1="ttt1"
            >
            </GcoinPot>
            <GcoinQueue 
                v-show="f_show_gcoin_queue"
                @close="closeGcoinQueue"
                @view-backdrop="closeGcoinQueue"
                @user-backdrop="closeModal"
                @disable-self="removeFlagFromStack"
                @showGcoinPot="showGcoinPot"
            >
            </GcoinQueue>
            <Report 
                v-show="f_show_report"
                @user-backdrop="closeModal"
                @close="closeReport"
                @share2="ttt2"
            >
            </Report>
            <ReportDetail
                v-show="f_show_report_detail"
                @close="closeReportDetail"
                @view-backdrop="closeReportDetail"
                @user-backdrop="closeModal"
                @disable-self="removeFlagFromStack"
                @share3="ttt3"
            >
            </ReportDetail>
            <ReportSuccess 
                v-show="f_show_report_success"
                @close="closeReportSuccess"
                @view-backdrop="closeReportSuccess"
                @user-backdrop="closeModal"
                @disable-self="removeFlagFromStack"
            >
            </ReportSuccess>
      </div>
    </div>
  </div>

</template>

<script>
import { default as Vuedals, Component as Vuedal, Bus as VuedalsBus } from 'vuedals';
import UserProfile from "../../modal/user_profile.vue";
import SendGcoin from "../../modal/send_gcoin.vue";
import Invite from "../../modal/invite.vue";
import Price from "../../modal/price.vue";
import EventSetting from "../../modal/event_setting.vue";
import UpcomingEvent from "../../modal/event_invite.vue";
import GcoinPot from "../../modal/gcoin_pot.vue";
import GcoinQueue from "../../modal/gcoin_pot_queue.vue";
import Report from "../../modal/report.vue";
import ReportDetail from "../../modal/report_detail.vue";
import ReportSuccess from "../../modal/report_success.vue";

export default {
  name: 'Event_Voice',
  components: {
      Vuedal,
      UserProfile,
      SendGcoin,
      Invite,
      Price,
      EventSetting,
      UpcomingEvent,
      GcoinPot,
      GcoinQueue,
      Report,
      ReportDetail,
      ReportSuccess
  },
  data () {
    return {
        gcoin_tap: false,
        gcoin_animation: false,
        isAddingCoin: false,
        isBlink: false,
        isDiamond: false,
        isBlink1: false,
        isloading: true,
        isModalVisible: false,
        clicked: false,
        imgClicked: false,
        isAudience: false,
        isSpeakers: false,
        f_show_user_profile: false,
        f_show_send_gcoin: false,
        f_show_invite: false,
        f_show_price: false,
        f_show_event_setting: false,
        f_show_upcoming_event: false,
        modalStack: [],
        f_show_gcoin_pot: false,
        f_show_gcoin_queue: false,
        f_show_report: false,
        f_show_report_detail: false,
        f_show_report_success: false,
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
              mute_user: "Ronald",
            },
            {
              mute_image: "Wendy.png",
              mute_user: "Cameron",
            },
            {
              mute_image: "Irma.png",
              mute_user: "Brandon",
            },
            {
              mute_image: "Wendy.png",
              mute_user: "Randall",
            },
            {
              mute_image: "Irma.png",
              mute_user: "Jorge",
            },
            {
              mute_image: "Wendy.png",
              mute_user: "Dustin",
            },
            {
              mute_image: "Irma.png",
              mute_user: "Regina",
            },
            {
              mute_image: "Wendy.png",
              mute_user: "Gloria",
            },
            {
              mute_image: "Irma.png",
              mute_user: "Harold",
            },
            {
              mute_image: "Wendy.png",
              mute_user: "Francisco",
            },
            {
              mute_image: "Irma.png",
              mute_user: "Julie",
            },
            {
              mute_image: "Wendy.png",
              mute_user: "Savannah",
            },
            {
              mute_image: "Wendy.png",
              mute_user: "Calvin",
            },
            {
              mute_image: "Irma.png",
              mute_user: "Dwight",
            },
            {
              mute_image: "Wendy.png",
              mute_user: "Ann",
            },
            {
              mute_image: "Irma.png",
              mute_user: "Arlene",
            },
        ]
    }
  },
  
  methods: {
    closeModal() {
        // this.f_show_host_view = false;
        // this.isModalVisible = false;
        this.f_show_gcoin_pot = false;
        this.f_show_gcoin_queue = false;
        this.f_show_report = false;
        this.f_show_report_success = false;
    },
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

      // setTimeout(() => {
      //     this.gcoin_animation = true
      // }, 3500)

      // setTimeout(() => {
      //     this.gcoin_tap = true
      // }, 7000)
    },
    showGCoinGrab() {
      this.gcoin_animation = true
      setTimeout(() => {
          this.gcoin_animation = false
          this.gcoin_tap = true
      }, 3500)
    },
    killGcoinTap() {
      // this.gcoin_animation = false
      this.gcoin_tap = false
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
      this.isAudience = !this.isAudience;
      if (this.isSpeakers) {
        this.isSpeakers = false;
      }
    },
    showSpeakers() {
      this.isSpeakers = !this.isSpeakers;
      if (this.isAudience) {
        this.isAudience = false;
      }
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
    closeGcoinPot() {
        this.f_show_gcoin_pot = false;
        this.f_show_gcoin_queue = true;
    },
    closeGcoinQueue() {
        this.f_show_gcoin_queue = false;
    },
    closeReport() {
        this.f_show_report = false;
    },
    closeReportSuccess() {
        this.f_show_report_success = false;
    },
    closeReportDetail() {
        this.f_show_report_detail = false;
    },
    removeFlagFromStack() {

      let temp = this.modalStack.pop(-1);

      switch (temp) {
        case 'f_show_send_gcoin':
          this.f_show_send_gcoin = false
          break;
        case 'f_show_user_profile':
          this.f_show_user_profile = false
          break;
        default:
          break;
      }
      switch (temp) {
        case 'f_show_invite':
          this.f_show_invite = false
          break;
        default:
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
        case 'f_show_event_setting':
          this.f_show_event_setting = false
          break;
        default:
          break;
      }
      this.f_show_send_gcoin = false,

      this.f_show_user_profile = false,

      this.f_show_invite = false,

      this.f_show_price = false,

      this.f_show_event_setting = false,

      this.f_show_gcoin_queue = false,

      this.f_show_gcoin_pot = false,

      this.f_show_report = false,

      this.f_show_report_detail = false,

      this.f_show_report_success = false
    },
    showUserProfile() {
        if (!this.isAddingCoin) {
            this.f_show_user_profile = true;
            this.modalStack.push('f_show_user_profile');
        } else {
            this.isAddingCoin = true;
        }
    },
    showSendGcoin() {
      this.f_show_send_gcoin = true;
      this.modalStack.push('f_show_send_gcoin');
    },
    showInvite() {
      this.f_show_invite = true;
    },
    showPrice() {
        this.f_show_price = true;
        this.modalStack.push('f_show_price');
    },
    showEventSetting() {
        this.f_show_event_setting = true;
        // this.modalStack.push('f_show_event_setting');
    },
    showGcoinPot() {
      this.f_show_gcoin_pot = true;
      this.f_show_gcoin_queue = false;
      this.f_show_event_setting = false;
    },
    showGcoinQueue() {
      this.f_show_gcoin_queue = true;
      this.f_show_gcoin_pot = false;
    },
    showReport() {
      this.f_show_report = true;
      this.f_show_report_success = false;
      this.f_show_event_setting = false;
    },
    showReportDetail(index) {
        this.f_show_report_detail = true;
        this.f_show_report = false;
    },
    showReportSuccess() {
        this.f_show_report_success = true;
        this.f_show_report = false;
        this.f_show_report_detail = false;
    },
    ttt() {
      this.f_show_upcoming_event = true; // showing child
      this.f_show_invite = false;
      // this.$emit('close'); // disable myself to parent
    },
    ttt1() {
      this.f_show_gcoin_queue = true; // showing child
      this.f_show_gcoin_pot = false;
      // this.$emit('close'); // disable myself to parent
    },
    ttt2() {
      this.f_show_report_success = false; // showing child
      this.f_show_report = false;
      this.f_show_report_detail = true;
      // this.$emit('close'); // disable myself to parent
    },
    ttt3() {
      this.f_show_report_success = true; // showing child
      this.f_show_report = false;
      this.f_show_report_detail = false;
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
    removeDetailFlagFromStack() {
        this.f_show_report_detail = !this.f_show_report_detail;
    },
  },
  computed: {
    imgSrc: function () {
      return this.imgClicked ? 'figure_orange.png' : 'figure.png'
    },
  },
  created () {
    this.killLoading();
  },
};
</script>

<style>
  .event_body {
    margin: 130px 20px 150px;
    background: white;
    width: 100%;
    border-radius: 16px;
  }
  .figure_btn {
    width: 85px;
    height: 85px;
    bottom: 35px;
    left: calc(50vw - 40px);
  }
  .figure_btn img{
    margin-right: 3px;
  }
  .main_event {
    margin: 0 20px;
  }
  .event_body_title {
    position: absolute;
    text-align: left;
    width: 100%;
    max-width: 414px;
    z-index: 1;
  }
  .event_body_title .event_favicon_img{
    margin: 20px 20px 0;
    letter-spacing: 0.08em;
    font-size: 14px;
  }
  .event_favicon_img img{
    margin-right: 8px;
  }
  .event_body_title .event_desc {
    font-size: 20px;
    margin: 0 20px 0;
    letter-spacing: 0.02em;
  }
  .event_body_title .event_back {
    margin: 0 20px;
  }
  .event_body_title .event_back img {
    margin: 0 5px 2px;
  }
  .event_body_title .event_back span {
    float: right;
  }
  .event_users {
    display: flex;
    padding: 15px 10px;
  }
  .event_users span {
    width: 100%;
  }
  .event_users_img {
    width: 96px;
    height: 96px;
    border-radius: 50%;
  }
  .event_coin {
    width: 82px;
    height: 80px;
    border-radius: 50%;
  }
  .event_users span button {
    background: #FFB803;
    border-radius: 16px;
    color: white;
    letter-spacing: 0.1em;
    padding: 0 10px;
    margin-top: 10px;
  }
  .event_para_group {
    width: 100%;
    letter-spacing: 0.08em;
    font-size: 14px;
    line-height: 26px;
  }
  .event_para_group p {
    margin: 4px 0;
    text-align: right;
    display: flex;
  }
  .event_para_group p span {
    margin: auto;
  }
  .event_para_group p img {
    margin: auto 0 auto 5px;
    height: 100%;
  }
  .event_user_group {
    display: flex;
    flex-wrap: wrap;
    letter-spacing: ;
  }
  .event_each_user {
    width: 33.33%;
    margin: 10px 0 20px;
  }
  .event_icon {
    position: relative;
    height: 90px;
  }
  .event_star {
    position: absolute;
    left: 20px;
    top: 0;
  }
  .event_mute {
    top: 48px;
    left: 20px;
    position: absolute;
  }
  .event_diamond {
    position: absolute;
    top: 48px;
    right: 15px;
  }
  .event_each_user p {
    margin: 0;
  }
  .coin_letter {
    letter-spacing: 0.08em;
    font-size: 13px;
    text-align: left;
  }
  .coin_letter span {
    margin: auto auto auto 10px;
  }
  .event_user_coin {
    margin: auto auto auto 20px;
  }
  .event_ranking button{
    width: calc(50% - 40px);
    padding: 5px 10px;
  }
  .rangking_data {
    display: flex;
    margin: 10px 50px;
  }
  .rangking_data img {
    width: 32px;
    height: 32px;
    border-radius: 50%;
  }
  .rangking_data p {
    margin: auto auto auto 15px;
    width: 100%;
    text-align: left;
  }
  .rangking_data span {
    float: right;
  }
  .border_btn {
    border-bottom: 4px solid #EF8200;
  }
  .event_ranking_title {
    margin: 20px 50px;
    text-align: left;
  }
  .event_mute_group {
    display: flex;
    flex-wrap: wrap;
    padding: 0 10px;
    margin-top: 20px;
  }
  .mute_user {
    width: 25%;
    margin-bottom: 20px;
  }
  .mute_icon {
    position: relative;
    height: 60px;
  }
  .mute_user p {
    margin: 0;
  }
  .mute_user_img {
    border-radius: 50%;
    width: 56px;
    height: 56px;
  }
  .hand_orange {
    background-color: #E8F1FA;
    transition-duration: 1s;
    transition-property: background-color;
  }
  .hand_black {
    background-color: #3B3E51;
    transition-duration: 1s;
    transition-property: background-color;
  }
  .loading_screen {
    width: 100%;
    height: 100vh;
  }
  .loading_screen > img {
    position: absolute;
    top: 0;
    bottom: 0;
    right: 0;
    left: 0;
    margin: auto;
  }

  .charge_select {
    color: #808695;
  }
  .footer_modal_border {
    border-top: 3px solid #E8F1FA;
    margin: auto;
    max-width: 414px;
    width: 100%;
    display: flex;
  }
  .footer_modal_border button {
    margin: 20px auto;
  }
  .charge_close {
    margin: auto 20px auto auto;
    float: right;
    text-align: center;
    display: grid;
  }
  .charge_close img {
    margin: auto;
  }
  .charge_close span {
    padding-top: 5px !important;
    color: #FFB803 !important;
  }
  .footer_modal_border .send_coin_btn {
    height: 35px;
    margin: auto 20px !important;
  }
  .user_logo_border {
    border: 3px solid #ffb803;
    border-radius: 50%;
    padding: 2px;
  }
  /* Animation coin  */
  @keyframes blinkingFrames {
    0% {opacity: 0.00;}
    50% {opacity: 1.00;}
    100% {opacity: 0.00;}
    from {bottom: 80px;}
    to {bottom: 90px;}
  }

  .blinking {
      animation-name: blinkingFrames;
      animation-duration: 0.5s;
  }
  .blinkingUser {
        animation-name: blinkingFramesUser;
        animation-duration: 0.5s;
  }
  @keyframes blinkingFramesUser {
    0% {opacity: 0.00;}
    50% {opacity: 1.00;}
    100% {opacity: 0.00;}
    from {bottom: 50px;}
    to {bottom: 60px;}
  }
  .diamondAppear {
        animation-name: diamondFramesUser;
        animation-duration: 1s;
    }
    @keyframes diamondFramesUser {
    0% {opacity: 0.00;}
    25% {opacity: 0.75;}
    75% {opacity: 1.00;}
    100% {opacity: 0.00;}
    from {bottom: 25px;}
    to {bottom: 25px;}
  }
  .blink-img {
    opacity: 0;
    position: absolute;
    left: 0;
    right: 0;
    margin: 20px auto;
    width: 55px;
    height: 55px;
  }
  .diamond-img {
    opacity: 0;
    position: absolute;
    left: 0;
    right: 0;
    bottom: 0;
    margin: 27px auto;
    width: 50px;
    height: 40px;
  }
  .blink_span {
    position: relative;
  }
  .welcome_dialog {
    max-width: 414px;
    position: absolute;
    top: 0;
    z-index: 100;
    background: rgba(195, 195, 195, 0.2);
    position: fixed;
  }
  .welcome_dialog p {
    margin: 10px auto 0;
  }
  .welcome_dialog_content {
    text-align: center;
    background: white;
    width: 100%;
    max-width: 414px;
    margin: auto;
    position: relative;
  }
  .welcome_dialog_content > img {
    width: 100%;
    padding: 10px;
  }
  .welcome_dialog_title {
    font-size: 20px;
  }
  .welcome_dialog_price {
    font-size: 16px;
    color: #EF8200;
    font-weight: 600;
  }
  .welcome_dialog_btn {
    font-size: 13px;
  }
  .gcoin_animation {
    position: relative;
  }
    @keyframes floatBubble1 {
        0% { left:calc(50% - 30px); top: 10px; opacity: 1; } 40% {opacity: 0.8;} 70% {opacity: 1;} 100% { left: calc(50% - 30px); top: -55px; }
    }
    @keyframes floatBubble2 {
        0% { left:calc(50% - 30px); top: 10px; opacity: 1; } 40% {opacity: 0.8;} 70% {opacity: 1;} 100% { left: calc(50% + 20px); top: -40px; }
    }
    @keyframes floatBubble3 {
        0% { left:calc(50% - 30px); top: 10px; opacity: 1; } 40% {opacity: 0.8;} 70% {opacity: 1;} 100% { left: calc(50% + 40px); top: 10px; }
    }


    @keyframes floatBubble4 {
        0% { left:calc(50% - 30px); top: 10px; opacity: 1; } 40% {opacity: 0.8;} 70% {opacity: 1;} 100% { left: calc(50% + 10px); top: 60px; }
    }
    @keyframes floatBubble5 {
        0% { left:calc(50% - 30px); top: 10px; opacity: 1; } 40% {opacity: 0.8;} 70% {opacity: 1;} 100% { left: calc(50% - 30px); top: 75px; }
    }
    @keyframes floatBubble6 {
        0% { left:calc(50% - 30px); top: 10px; opacity: 1; } 40% {opacity: 0.8;} 70% {opacity: 1;} 100% { left: calc(50% - 80px); top: 60px; }
    }


    @keyframes floatBubble7 {
        0% { left:calc(50% - 30px); top: 10px; opacity: 1; } 40% {opacity: 0.8;} 70% {opacity: 1;} 100% { left: calc(50% - 100px); top: 10px; }
    }
    @keyframes floatBubble8 {
        0% { left:calc(50% - 30px); top: 10px; opacity: 1; } 40% {opacity: 0.8;} 70% {opacity: 1;} 100% { left: calc(50% - 80px); top: -40px; }
    }

    /*@keyframes floatBubble9 {
        0% { left:calc(50% - 30px); top: 10px; opacity: 1; } 100% { left: calc(50% - 60px); top: -3px; }
    }
    @keyframes floatBubble10 {
        0% { left:calc(50% - 30px); top: 10px; opacity: 1; } 100% { left: calc(50% - 0px); top: 20px; }
    }
    @keyframes floatBubble11 {
        0% { left:calc(50% - 30px); top: 10px; opacity: 1; } 100% { left: calc(50% - 10px); top: 25px; }
    }*/
    .moving {
      position: absolute;
      top: 10px;
      left: calc(50% - 30px);
      opacity: 0;
      width: 60px;
      height: 60px;
    }
    .moving:nth-of-type(2) { animation: floatBubble1 2s ; animation-delay: 0.5s;}
    .moving:nth-of-type(3) { animation: floatBubble2 2s ; animation-delay: 0s; }
    .moving:nth-of-type(4) { animation: floatBubble3 2s ; animation-delay: 0.68s;}
    .moving:nth-of-type(5) { animation: floatBubble4 2s ; animation-delay: 0.2s;}
    .moving:nth-of-type(6) { animation: floatBubble5 2s ; animation-delay: 0.88s;}
    .moving:nth-of-type(7) { animation: floatBubble6 2s ; animation-delay: 1.2s;}
    .moving:nth-of-type(8) { animation: floatBubble7 2s ; animation-delay: 0.3s;}
    .moving:nth-of-type(9) { animation: floatBubble8 2s ; animation-delay: 1s;}
    /*.moving:nth-of-type(10) { animation: floatBubble9 2s infinite  normal ease-out; }
    .moving:nth-of-type(11) { animation: floatBubble10 2s infinite  normal ease-out; }
    .moving:nth-of-type(12) { animation: floatBubble11 2s infinite  normal ease-out; }*/
    .promotional_text {
      color: #13C8FF;
      border-radius: 8px;
      border: 1px solid #CDE1FF;
      margin: 10px 10px 0;
    }
    .welcome_coin_title {
      position: absolute;
      top: 10px;
      left: 140px;
      display: grid;
    }
    .event_room_lock {
      position: fixed;
      margin: auto 10px !important;
      z-index: 1040;
    }
    .event_voice_logo {
      margin: auto 0 auto auto !important;
    }
</style>
 