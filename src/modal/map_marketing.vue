<template>
  <transition name="modal-fade">
    <div class="modal-backdrop">
      <div class="modal"
        role="dialog"
        aria-labelledby="modalTitle"
        aria-describedby="modalDescription"
      >
        <header
          class="modal-header"
          id="modalTitle"
        >
          <slot name="header">
              Add Branch
          </slot>
          <button
            type="button"
            class="close_btn"
            @click="close"
            aria-label="Close modal"
          >
            <i class="fa fa-times-circle" aria-hidden="true"></i>
          </button>
        </header>

        <section
          class="modal-body"
          id="modalDescription"
        >
          <slot name="body">
              <div class="form-group">
                <select class="form-control" id="">
                  <option>Business Role</option>
                  <option>2</option>
                  <option>3</option>
                  <option>4</option>
                  <option>5</option>
                </select>
              </div>
              <div class="form-group">
                <select class="form-control" id="">
                  <option>Choose Address</option>
                  <option>2</option>
                  <option>3</option>
                  <option>4</option>
                  <option>5</option>
                </select>
              </div>
              <div class="form-group">
                <input
                  type="text"
                  class="form-control"
                  id="distributors"
                  aria-describedby="distributors"
                  placeholder="Number of Distributors"
                />
              </div>
              <div class="form-group">
                <input
                  type="text"
                  class="form-control"
                  id="contact_name"
                  aria-describedby="contact_name"
                  placeholder="Contact Name"
                />
              </div>
          </slot>
        </section>

        <footer class="modal-footer">
          <slot name="footer">
            <button
              type="button"
              class="save_btn"
              @click="close"
              aria-label="Close modal"
            >SAVE</button>
          </slot>
        </footer>
      </div>
    </div>
  </transition>
</template>

<script>
  export default {
    name: 'Map_Marketing',
    methods: {
      close() {
        this.$emit('close');
      },
    },
  };
</script>

<style>
</style>