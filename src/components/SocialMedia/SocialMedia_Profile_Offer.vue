<template>
  <div>
    <div class="container">
      <div class="profile_phone profile_each_size">
        
            <div class="header_modal profile_modal">
                <router-link to="/socialmedia/socialmedia_bs_profile" class="header_arrow"><img src="img/header_arrow.png"></router-link>
                <a>Brand Name Title</a>
            </div>
            <div class="profile_each_titile">
                <img src="profile/massage.png">
                <p>Relaxology</p>
                <p class="profile_title_desc">Relaxology brand is a brand under the business name. This is only a sample description you are reading.</p>
            </div>
            <div class="profile_each_session">
                <hooper group="group1" :itemsToShow="4" :centerMode="true" class="profile_hooper_btn profile_offer_btn">
                    <slide class="swiperslide_btn">
                    <button @click=setCurrentCarouselIndex(0)>Products</button>
                    </slide>
                    <slide class="swiperslide_btn">
                    <button @click=setCurrentCarouselIndex(1)>Business Chain</button>
                    </slide>
                    <slide class="swiperslide_btn">
                    <button @click=setCurrentCarouselIndex(2)>Certifications</button>
                    </slide>
                    <slide class="swiperslide_btn">
                    <button @click=setCurrentCarouselIndex(3)>Reviews</button>
                    </slide>
                    <slide class="swiperslide_btn">
                    <button @click=setCurrentCarouselIndex(4)>Marketing Future Trends</button>
                    </slide>
                </hooper>
                <hr class="profile_hr">
                <hooper group="group1" ref="carousel" class="profile_hooper_content">
                    <slide class="slide_block">
                        <!-- Offers -->
                        <p class="profile_relax"><b>Foot</b></p>
                        <div class="profile_relax_detail">
                            <img src="profile/pressure.png" class="relax_chair">
                            <div class="relax_massage">
                                <p class="profile_relax_msg"><b>Foot Air Pressure Leg Massager Body Massager</b></p>
                                <table class="profile_table">
                                    <tr>
                                        <th>Price</th>
                                        <th>Payout</th>
                                        <th>CPC</th>
                                    </tr>
                                    <tr>
                                        <td>$85.99</td>
                                        <td>$6</td>
                                        <td>5 GCoins</td>
                                    </tr>
                                </table>
                                <button class="relax_buy">BUY NOW</button>
                            </div>
                        </div>
                        <div class="relax_link">
                            <div>
                                <img src="profile/copy_link.png">
                                <p>Copy Link</p>
                            </div>
                            <div>
                                <img src="profile/videos.png" @click="showVideo">
                                <p>Videos</p>
                            </div>
                            <div>
                                <img src="profile/banners.png" @click="showBanner">
                                <p>Banners</p>
                            </div>
                            <div>
                                <img src="profile/detail.png" @click="showDetail">
                                <p>Detail</p>
                            </div>
                            <div>
                                <img src="profile/reviews.png" @click="showReview">
                                <p>Reviews</p>
                            </div>
                        </div>
                        <hr class="profile_hr">
                        <div class="profile_relax_detail">
                            <img src="profile/electric.png" class="relax_chair">
                            <div class="relax_massage">
                                <p class="profile_relax_msg"><b>Electric Massager Leg Foot Massager 3 Modes</b></p>
                                <table class="profile_table">
                                    <tr>
                                        <th>Price</th>
                                        <th>Payout</th>
                                        <th>CPC</th>
                                    </tr>
                                    <tr>
                                        <td>$99.99</td>
                                        <td>$8</td>
                                        <td>8 GCoins</td>
                                    </tr>
                                </table>
                                <button class="relax_buy">BUY NOW</button>
                            </div>
                        </div>
                        <div class="relax_link">
                            <div>
                                <img src="profile/copy_link.png">
                                <p>Copy Link</p>
                            </div>
                            <div>
                                <img src="profile/videos.png" @click="showVideo">
                                <p>Videos</p>
                            </div>
                            <div>
                                <img src="profile/banners.png" @click="showBanner">
                                <p>Banners</p>
                            </div>
                            <div>
                                <img src="profile/detail.png" @click="showDetail">
                                <p>Detail</p>
                            </div>
                            <div>
                                <img src="profile/reviews.png" @click="showReview">
                                <p>Reviews</p>
                            </div>
                        </div>
                        <p class="profile_relax"><b>Full Body</b></p>
                        <div class="profile_relax_detail">
                            <img src="profile/relax_chair.png" class="relax_chair">
                            <div class="relax_massage">
                                <p class="profile_relax_msg"><b>Full Body Massage Cushion</b></p>
                                <table class="profile_table">
                                    <tr>
                                        <th>Price</th>
                                        <th>Payout</th>
                                        <th>CPC</th>
                                    </tr>
                                    <tr>
                                        <td>$129.95</td>
                                        <td>$10</td>
                                        <td>10 GCoins</td>
                                    </tr>
                                </table>
                                <button class="relax_buy">BUY NOW</button>
                          </div>
                        </div>
                        <div class="relax_link">
                            <div>
                                <img src="profile/copy_link.png">
                                <p>Copy Link</p>
                            </div>
                            <div>
                                <img src="profile/videos.png" @click="showVideo">
                                <p>Videos</p>
                            </div>
                            <div>
                                <img src="profile/banners.png" @click="showBanner">
                                <p>Banners</p>
                            </div>
                            <div>
                                <img src="profile/detail.png" @click="showDetail">
                                <p>Detail</p>
                            </div>
                            <div>
                                <img src="profile/reviews.png" @click="showReview">
                                <p>Reviews</p>
                            </div>
                        </div>
                        <hr class="profile_hr">
                    </slide>
                    <slide class="swiperslide_btn">
                        <!-- Business Chain -->
                        <div class="profile_services">
                            <p class="bs_relax_desc" v-for="(item, index) in industry" :key="index"><b>{{item.title1}}</b><br>{{item.property1}}<br>{{item.property2}}<br>{{item.property3}}<br>{{item.property4}}<br>{{item.property5}}</p>
                            <p class="relax_desc" v-for="(item, index) in internal" :key="index"><b>{{item.title2}}</b><br>{{item.property6}}<br>{{item.property7}}<br>{{item.property8}}<br>{{item.property9}}<br>{{item.property10}}<br>{{item.property11}}<br>{{item.property12}}<br>{{item.property13}}</p>
                        </div>
                    </slide>
                    <slide class="swiperslide_btn">
                        <!-- Certifications -->
                        <p class="profile_relax"><b>Trademark Certificates (2)</b></p>
                        <div class="certificate_desc" v-for="(item, index) in BScertificationdata" :key="index">
                            <img :src="`${item.image_url}`">
                            <p class="relax_desc"><b>Certification Type:</b><br>{{item.type}}<br><b>Certification Number:</b><br>{{item.number}}<br><b>Authority of Issue:</b><br>{{item.issue}}<b><br>Issue Date: </b>{{item.issuedate}}<br><b>Expiration Date: </b>{{item.date}}<br><b>Description:</b><br>{{item.desc}}</p>
                        </div>
                    </slide>
                    <slide class="swiperslide_btn">
                        <!-- Reviews -->
                        <p class="profile_commun"><b>Latest Reviews</b></p>
                        <div class="profile_services" v-for="(item, index) in BSreviewdata" :key="index">
                            <img src="profile/review_star.png">
                            <img src="profile/review_star.png">
                            <img src="profile/review_star.png">
                            <img src="profile/review_star.png">
                            <img src="profile/review_star.png">
                            <p class="relax_desc">{{item.review_title}}</p>
                            <p class="relax_desc_review">{{item.review_date}}</p>
                            <div class="review_user">
                                <img :src="`${item.review_user}`">
                                <p><b>{{item.review_name}}</b><br>{{item.review_address}}</p>
                            </div>
                            <hr class="review_hr">
                        </div>
                    </slide>
                    <slide class="swiperslide_btn">
                        <!-- Marketing Future Trends -->
                            <p class="profile_commun"><b>Marketing Future Trends</b></p>
                            <p class="future_maps">2 Headquarters<span>10 Branches</span></p>
                            <img src="profile/future_maps.png" class="trends_map">
                            <p class="profile_commun"><b>Existing Branches</b></p>
                            <p class="future_maps">2 Headquarters</p>
                            <p class="future_maps">1 Chain Store</p>
                            <p class="future_maps">1 Country</p>
                            <p class="future_maps">2 Franchisee</p>
                            <p class="future_maps">2 Other</p>
                    </slide>
                </hooper>
          </div>
      </div>
      <Video 
        v-show="f_show_video"
        @close="closeModal"
        @user-backdrop="removeFlagFromStack"
      >
      </Video>
      <Banner 
        v-show="f_show_banner"
        @close="closeModal"
        @user-backdrop="removeFlagFromStack"
      >
      </Banner>
      <Detail 
        v-show="f_show_detail"
        @close="closeModal"
        @user-backdrop="removeFlagFromStack"
      >
      </Detail>
      <Review 
        v-show="f_show_review"
        @close="closeModal"
        @user-backdrop="removeFlagFromStack"
      >
      </Review>
    </div>
  </div>
</template>
<script>
import Video from "../../modal/video.vue";
import Banner from "../../modal/banner.vue";
import Detail from "../../modal/detail.vue";
import Review from "../../modal/review.vue";
import { Hooper, Slide } from 'hooper';
import 'hooper/dist/hooper.css';

export default {
  name: 'Profile_Offers',
  components: {
    Video,
    Banner,
    Detail,
    Review,
    Hooper,
    Slide
  },
  data () {
    return {
      f_show_video: false,
      f_show_banner: false,
      f_show_detail: false,
      f_show_review: false,
      modalStack: [],
      currentCarouselIndex: 0,
      followData: [
        {
          follow: true
        }
      ],
      BScertificationdata: [
        {
          image_url: "profile/profile_doc.png",
          type: "Brandname Certification",
          number: "86831221",
          issue: "US Patent & Trademark Office",
          issuedate: "03/01/2017",
          date: "04/15/2017",
          desc: "Trade Mark Certificate \n for Relaxxology"
        },
        {
          image_url: "profile/profile_doc.png",
          type: "Brandname Certification",
          number: "86831221",
          issue: "US Patent & Trademark Office",
          issuedate: "03/01/2017",
          date: "04/15/2017",
          desc: "Trade Mark Certificate \n for Relaxxology"
        }
      ],
      industry: [
        {
          title1: "Industry Business Chain",
          property1: "Manufactures 1",
          property2: "Distributors 0",
          property3: "Wholesalers 0",
          property4: "Retailers 0",
          property5: "Others 0",
        },
      ],
      internal: [
        {
          title2: "Internal Business Chain",
          property6: "Headquarters 9",
          property7: "Chain Stores 9",
          property8: "Franchisee 1",
          property9: "Global Distributors 2",
          property10: "Nationwide Distributor 0",
          property11: "Wholesale Dealer 12",
          property12: "Retail Dealer 0",
          property13: "Others 1",
        }
      ],
      BSreviewdata: [
        {
          review_title: "Good Business!",
          review_date: "Reviewed on October 14, 2021",
          review_user: "profile/review_user.png",
          review_name: "Willy Williams",
          review_address: "San Diego, California",
        },
        {
          review_title: "Good perfumes! the scents are memorable!",
          review_date: "Reviewed on October 14, 2021",
          review_user: "recommendation/recom_user5.png",
          review_name: "Jack Hugh",
          review_address: "Los Angeles, California",
        },
      ],
      BSbrandsdata: [
        {
          title: "Brands Owned"
        },
        {
          title: "Brands Carried"
        }
      ],
      swiperOption: {
          slidesPerView: 'auto',
          spaceBetween: 10,
      }
    }
  },
  watch: {
    currentCarouselIndex () {
      this.$refs.carousel.slideTo(this.currentCarouselIndex);
    }
  },
  methods: {
    selectFollow(index) {
      this.followData[index].follow = false
    },
    closeModal() {
      this.f_show_video = false;
      this.f_show_banner = false;
      this.f_show_detail = false;
      this.f_show_review = false;
      this.isModalVisible = false;
    },
    showVideo() {
      this.f_show_video = true;
    },
    showBanner() {
      this.f_show_banner = true;
    },
    showDetail() {
      this.f_show_detail = true;
    },
    showReview() {
      this.f_show_review = true;
    },
    removeFlagFromStack() {

      let temp = this.modalStack.pop(-1);
      switch (temp) {
        case 'f_show_video':
          this.f_show_video = false
          break;
        default:
          break;
      }
      switch (temp) {
        case 'f_show_banner':
          this.f_show_banner = false
          break;
        default:
          break;
      }
      switch (temp) {
        case 'f_show_detail':
          this.f_show_detail = false
          break;
        default:
          break;
      }
      switch (temp) {
        case 'f_show_review':
          this.f_show_review = false
          break;
        default:
          break;
      }
      this.f_show_video = false
      this.f_show_banner = false,
      this.f_show_detail = false,
      this.f_show_review = false
    },
    setCurrentCarouselIndex(index) {
      this.currentCarouselIndex = index;
    },
  }
}
</script>
<style>
  .profile_each_size {
    display: block !important;
  }
  .profile_each_session {
    margin: 0 25px;
    width: calc(100% - 50px);
    max-width: 414px;
  }
  .profile_each_titile {
    max-width: 414px;
    width: 100%;
    margin-top: 80px;
  }
  .profile_title_desc {
    margin: 0 25px;
    text-align: left;
    font-size: 14px;
  }
  .profile_btn_orange button {
    background-color: #FFB803 !important;
    color: white !important;
  }
  .brands_owned div {
    width: 33.33%;
  }
  .profile_offer_btn .is-current{
    background-color: #FFB803 !important;
  }
  .profile_offer_btn .is-current button {
    color: white;
  }
  .relax_desc_review {
    text-align: left;
    margin: 5px 20px 5px 0;
    font-size: 14px;
  }
</style>
