<template>
  <div id="app">
    <header class="site-header"><div>Header</div></header>
    <main class="site-main">
      <h1>Popup Modal Challenge</h1>
      <p>
        This is my submission for the popup modal challenge. The submission is a
        vue app started using vue cli's <code>vue create</code> command. I used
        a custom preset with Yarn, Babel, ESLint + Prettier, and node-sass.
      </p>
      <p>
        After the site loads, wait three seconds and the popup modal will
        appear. After dismissing the modal with the "x" button, a value is
        stored in <code>localStorage</code> to ensure the modal does not open
        again unless the user clears the browser cache.
      </p>
      <h2>Tested On</h2>
      <ul>
        <li>macOS - Chrome</li>
        <li>macOS - Safari</li>
        <li>macOS - Firefox</li>
        <li>iOS - Chrome</li>
        <li>iOS - Safari</li>
      </ul>
      <h2>Known Issues</h2>
      <ul>
        <li>Scrolling the modal is a little weird on iOS</li>
      </ul>
    </main>
    <footer class="site-footer"><div>Footer</div></footer>
    <transition name="fade">
      <Modal class="modal" @dismiss="dismissModal()" v-if="modalShown" />
    </transition>
  </div>
</template>

<script>
import Modal from "./components/Modal/Modal.vue";

export default {
  name: "app",
  components: {
    Modal
  },
  data() {
    return {
      modalShown: false
    };
  },
  created() {
    this.initModal();
  },
  methods: {
    initModal() {
      if (!localStorage.modalDismissed) {
        setTimeout(() => {
          this.modalShown = true;
        }, 3000);
      } else {
        return;
      }
    },
    dismissModal() {
      localStorage.modalDismissed = true;
      this.modalShown = false;
    }
  },
  computed: {
    modalInfo() {
      if (localStorage.modalDismissed && !this.modalShown) {
        return "Modal has been dismissed.";
      }
      return "Please wait for modal.";
    }
  }
};
</script>

<style lang="scss">
@import url("https://fonts.googleapis.com/css?family=Didact+Gothic&display=swap");
@import "./scss/variables.scss";
@import "./scss/global.scss";
@import "./scss/transitions.scss";

#app {
  min-height: 100vh;
  position: relative;
}

.site-header {
  display: flex;
  align-items: center;
  justify-content: flex-start;
  margin-bottom: $spacing-lg;
  padding: 0 2rem;
  width: 100%;
  height: 4rem;

  background: $accent-color;
  color: $bg-color;
}

.site-main {
  margin: 0 auto;
  padding: 0 2rem 8rem;
  max-width: $max-content;
}

.site-footer {
  position: absolute;
  bottom: 0;
  display: flex;
  align-items: center;
  justify-content: flex-start;
  width: 100%;
  height: 8rem;
  padding: 0 2rem;
  background: $footer-color;
}

.modal {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
}
</style>
