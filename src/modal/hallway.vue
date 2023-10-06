<template>
  <transition name="modal-fade">
    <div class="modal-backdrop" v-on:click.self="userProfileBackdrop">
      <div class="modal_event_transform"
        role="dialog"
        aria-labelledby="modalTitle"
        aria-describedby="modalDescription"
      >
        <header
          class="host_view_position"
          id="modalTitle"
        >
            <div class="invite_modal">
                <p class="invite_title">Invite People to this Event<span><img src="share.png">SHARE</span></p>
                <div class="invite_find">
                        <input type="search" placeholder="Find People" class="form-control">
                        <img src="Search_modal.png">
                </div>
                <div class="invite_users">
                  <div v-for="(item, index) in HostData" :key="index" class="invite_user">
                    <img :src="`${item.host_img}`">
                    <span>{{item.host_name}}</span>
                  </div>
                </div>
            </div>
        </header>
      </div>
    </div>
  </transition>
</template>

<script>
  export default {
    name: 'Hallway',
    data () {
        return {
            HostData: [
                {
                    host_img: "Ray_big_on.png",
                    host_name: "Joseph Merk",
                },
                {
                    host_img: "Ray_big_on.png",
                    host_name: "Joseph Merk",
                },
                {
                    host_img: "Ray_big_on.png",
                    host_name: "Joseph Merk",
                },
                {
                    host_img: "Ray_big_on.png",
                    host_name: "Joseph Merk",
                },
                {
                    host_img: "Ray_big_on.png",
                    host_name: "Joseph Merk",
                },
                {
                    host_img: "Ray_big_on.png",
                    host_name: "Joseph Merk",
                },
                {
                    host_img: "Ray_big_on.png",
                    host_name: "Joseph Merk",
                },
                {
                    host_img: "Ray_big_on.png",
                    host_name: "Joseph Merk",
                },
                {
                    host_img: "Ray_big_on.png",
                    host_name: "Joseph Merk",
                },
                {
                    host_img: "Ray_big_on.png",
                    host_name: "Joseph Merk",
                },
                {
                    host_img: "Ray_big_on.png",
                    host_name: "Joseph Merk",
                },
                {
                    host_img: "Ray_big_on.png",
                    host_name: "Joseph Merk",
                },
            ]
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
    },
  };
</script>
<style>
    .hallway_find {
        height: 50px;
        border: 1px solid #AEE2FF;
        border-radius: 16px !important;
        padding-left: 30px !important;
        padding-right: 70px !important;
        position: relative;
    }
</style>
