<template>
  <transition name="modal-fade">
    <div class="modal-backdrop bg-view-mask" v-on:click.self="viewProfileBackdrop">
      <div class="bg-view-mask user_modal_width" v-on:click.self="viewProfileBackdrop">
        <div class="modal community_post_report_modal"
          role="dialog"
          aria-labelledby="modalTitle"
          aria-describedby="modalDescription"
        >
          <header
            class="swtich_account_header"
            id="modalTitle"
          >
              <div class="manage_area">
                <p class="manage_content">Hide this Post</p>
                <hr class="manage_hr">
                <p class="manage_content">Report this Post</p>
                <hr class="manage_hr">
                <p class="manage_content">I don't want to see post from Amanda Page</p>
              </div>
          </header>
        </div>
      </div>
    </div>
  </transition>
</template>

<script>
  export default {
    name: 'Community_Post-Report',
    components: {
    },  
    data () {
      return {
        f_show_view_profile: false,

      }
    },
    methods: {
      closeModal() {
        this.$emit('close');
      },
      viewProfileBackdrop(evt) {
        if(evt.target.classList.length > 0 && "bg-view-mask"){
          this.$emit('view-backdrop');
        }
      },
      close() {
        this.$emit('close');
      },
      userProfileBackdrop(evt) {
        if(evt.target.classList.length > 0 && "bg-mask"){
          this.$emit('user-backdrop');
        }
      },
      showIndustrySystem1() {
        this.$emit('showIndustrySystem1');
      },
      closeViewProfile() {
        this.f_industry_system1 = false;
      },
    },
  }
</script>
<style>
  .community_post_report_flex {
    display: flex;
    margin: 5px auto;
    padding: 10px 20px;
  }
  .community_post_report_flex img {
    margin: 2px 10px auto 0;
  }
  .community_post_report_modal {
    height: auto !important;
    max-width: 414px !important;
    width: calc(100% - 130px) !important;
    transform: translate3d(0, 0, 0) !important;
    border-radius: 16px !important;
    margin: auto 40px auto 90px;
  }
</style>
