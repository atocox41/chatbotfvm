<template>
  <div>
    <div class="container">
        <div class="phone header_phone">
          <div class="header_modal">
            <router-link to="/usercenter/upgrade_gs_account" class="header_arrow"><img src="img/header_arrow.png">
            </router-link>
            <a href="#">HOW IT WORKS</a>
          </div>
          <div class="content left-content header_top">
            <p class="medium_1_title">How it works for our Marketing partners:</p>
            <ul>
              <li>Create your profile and show how you drive online traffic. Here you enter your social handle channels, audience size, professional reviews, and your campaign conversion rate.</li>
            </ul>
            <ul>
              <li>There is NO LIMIT to your Commission/Conversions …. The more conversions you make, the more you can earn with GOLD!  Once a purchase is made, the related Business for that sales commission will be released to your account, this is known as a “Conversion” or “Conversion Sale”  (please check GOLD Terms and Conditions).</li>
            </ul>
            <ul>
              <li>Check/accept campaign offers as follows:</li>
              <ul>
                <li>Enter keywords to search for business offers, get to the target business' company page and check that business' offer links, as well as their Commission and CPC G-Coin rates.</li>
                <li>Quick search for Offers: Search G-Coins Rewards on GOLD's homepage, click to view all G-Coin rewards; Click on one to view the promotion details and start initiating your marketing campaign using GOLD’s Social platform to drive all the traffic to your marketing offers; such as: Events for branding and building communities, connecting with other GS Marketers, and businesses, influencers and other members of your matrix.  Use our Social Media events to expand your social connections and build up your personal influence or brand.</li>
                <li>Remember, Use your Live events to achieve real time sales.  By pursuing a daily presence with your Live channels you will grow your followers and drive your sales ever higher.</li>
                <li>Share offers links across all media to make your conversion sales. Remember when the link gets clicked 5 times or more, the rewards will be released to your account.</li>
                <li>Offer details and requirements: All G-Coin rewards details; Different CPC G-coins rates for all offers; and then select the offers tailored to your needs and select your favorite offer rewards.</li>
              </ul>
            </ul>
            <ul>
              <li>Pay attention to Ad Content，banners, and videos</li>
              <ul>
                <li>Check earned revenues: When offers are converted into clicks or conversions, marketer can view conversion details and revenues earned.</li>
                <li>Share your invitation links via exclusive QR codes or referral code and invite businesses and marketers to register accounts on GOLD</li>
                <li>Enter emails in the Invite section on your GOLD account and send the invitations.</li>
              </ul>
            </ul>
            <div class="how_it_works_btn">
              <router-link to="/usercenter/upgrade_gs_account" class="how_it_works_back_btn">
                <button class="how_it_works_back_btn">
                  <img src="reg_next.png" class="reg_next_rotate">Back
                </button>
              </router-link>
              <button class="back_top_btn" @click="scrollToTop"><img src="img/top_arrow.png"></button>
            </div>
          </div>
        </div>
    </div>
  </div>
</template>
<script>

export default {
  name: "How_It_Works",
  components: {
  },
  methods: { 
    scrollToTop() {
      window.scrollTo(0,0);
    }
  }
}
</script>
<style>
  .header_phone {
    position: relative;
  }
  .header_top {
    margin: 80px 20px 20px 20px;
    border-radius: 12px;
    overflow: hidden;
    min-height: calc(100vh - 26px);
    padding: 10px 0;
  }
  .reg_next_rotate {
    transform: rotate(180deg);
    margin-right: 25px;
  }
  .rotate_btn {
    margin-top: 20px;
  }
  .how_it_works_btn {
    display: flex;
    margin: 10px 10px 10px 20px;
    width: calc(100% - 30px);
  }
  .how_it_works_btn button {
    background: #F4992D;
    border-radius: 12px;
    padding: 12px;
    color: white;
  }
  .back_top_btn {
    margin: auto 0 auto 5px;
  }
  .how_it_works_back_btn {
    width: 100%;
  }
</style>