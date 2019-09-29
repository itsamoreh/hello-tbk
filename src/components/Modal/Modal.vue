<template>
  <div class="modal-overlay" v-on:scroll="animateDecorations">
    <aside
      class="modal-content"
      role="dialog"
      aria-labelledby="modal-title1 modal-title2"
    >
      <header class="modal-header">
        <button class="modal-dismiss" @click="$emit('dismiss')">
          <img
            width="10"
            height="10"
            alt="Close"
            src="../../assets/close.svg"
          />
        </button>
        <h1 id="modal-title1" class="text-subtitle">
          You are cordially invited to the launch
        </h1>
        <p>of the</p>
        <h2 id="modal-title2" class="h1 text-display">
          New <span class="text-accent">company</span> website
        </h2>
        <p>
          Lorem ipsum dolor sit amet, vix suas liber conclusionemque eu. Ad quo
          esse purto eros, nemore volutpat ut quo, copiosae concludaturque nam
          in.
        </p>
      </header>
      <section class="modal-section">
        <h2 class="text-subtitle">Ad est odio noster:</h2>
        <ul>
          <li>Ex vis amet graeci accumsan</li>
          <li>Civibus iracundia quo ad</li>
          <li>Eu impetus feugiat civibus qui</li>
          <li>Mel in mucius argumentum, an accumsan petentium vim</li>
          <li>Vim at rationibus interesset</li>
        </ul>
      </section>
      <footer class="modal-footer">
        <h2>Get your foot in the door.</h2>
        <p>Know the moment our new website goes live.</p>
        <form
          id="signup-form"
          aria-label="Get notified when our new website goes live"
          autocomplete="on"
          action=""
        >
          <input
            id="name"
            name="name"
            autocomplete="name"
            autocorrect="off"
            type="text"
            placeholder="Name"
          />
          <input
            id="email"
            name="email"
            autocomplete="email"
            autocapitalize="off"
            autocorrect="off"
            spellcheck="false"
            type="text"
            placeholder="Email"
          />
          <input value="Submit" type="submit" />
          <div class="terms-input">
            <input type="checkbox" id="terms" name="agreeTerms" value="agree" />
            <label for="terms"
              >Lorem ipsum dolor sit amet, consectetuer adipiscing elit. Donec
              odio. Quisque volutpat mattis eros. Nullam malesuada erat ut
              turpis. Suspendisse urna nibh, viverra non, semper suscipit,
              posuere a, pede.</label
            >
          </div>
        </form>
      </footer>

      <img
        class="chisel"
        ref="chisel"
        alt="Chisel decoration"
        src="../../assets/chisel.png"
      />
      <img
        class="shaving"
        ref="shaving"
        alt="Wood shaving decoration"
        src="../../assets/shaving.png"
      />
    </aside>
  </div>
</template>

<script>
export default {
  name: "Modal",
  methods: {
    animateDecorations(event) {
      const translateY = event.target.scrollTop / 4;
      this.$refs.chisel.style.transform = `translateY(-${translateY}px)`;
      this.$refs.shaving.style.transform = `translateY(${translateY}px)`;
    }
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">
@import "../../scss/variables";

.modal-overlay {
  padding: 8rem 0;
  width: 100%;
  background-color: $overlay;
  overflow: auto;
}

.modal-content {
  width: 90%;
  position: relative;
  max-width: $max-content;
  margin: 0 auto;
  background: $bg-color;

  .chisel {
    position: absolute;
    top: 50rem;
    left: -18rem;
    width: 400px;
  }

  .shaving {
    position: absolute;
    top: 12rem;
    right: -6rem;
  }

  @include for-tablet-portrait-only {
    .chisel {
      left: -20rem;
    }
    .shaving {
      right: -9rem;
    }
  }

  @include for-phone-only {
    .chisel,
    .shaving {
      display: none;
    }
  }

  &:before {
    content: url("../../assets/long-rectangle.svg");
    position: absolute;
    top: -3rem;
    left: 50%;
    margin-left: -80px;
    width: 160px;

    @include for-phone-only {
      margin-left: -66px;
      width: 132px;
    }
  }

  &:after {
    content: url("../../assets/short-rectangle.svg");
    position: absolute;
    bottom: -3rem;
    left: 50%;
    margin-left: -80px;
    width: 160px;
  }
}

.modal-dismiss {
  position: absolute;
  top: 0;
  right: 0;
  margin: 0.5rem;
  padding: 0.5rem;

  border: 0;
  background: transparent;
  cursor: pointer;
}

.modal-header {
  padding: $spacing-lg $spacing-sm 0 $spacing-sm;
  position: relative;
  text-align: center;

  .text-subtitle {
    max-width: 300px;
  }

  .text-display {
    margin-bottom: $spacing-lg;
    max-width: 400px;
    text-transform: uppercase;

    @include for-phone-only {
      max-width: 250px;
    }
  }

  p {
    margin: 0 auto $spacing-sm auto;
    padding: 0 $spacing-xs;
    max-width: 500px;
  }

  &:after {
    content: "";
    display: block;
    margin: $spacing-md auto $spacing-sm auto;
    max-width: 75px;
    border-width: 1px;
    border-style: solid;
    border-color: $accent-color;
  }
}

.modal-section {
  margin-bottom: $spacing-md;
  padding: $spacing-sm;
  text-align: center;

  p {
    text-transform: uppercase;
  }

  ul {
    margin: 0 auto;
    max-width: 500px;
    text-align: left;
    list-style: none;

    li {
      margin-bottom: 0.4em;
    }

    li:before {
      content: "\2022";
      color: $accent-color;
      display: inline-block;
      width: 1em;
      margin-left: -1em;
    }
  }
}

.modal-footer {
  padding: $spacing-lg $spacing-sm;
  text-align: center;
  background: $accent-color;
  color: $text-light;

  h2 {
    margin-bottom: 0;
    text-transform: uppercase;
  }

  @include for-phone-only {
    input[type="text"],
    input[type="submit"] {
      margin-left: auto;
      margin-right: auto;
      display: block;
    }
  }

  .terms-input {
    margin: 0 auto;
    padding: 0 $spacing-xs;
    max-width: 400px;
    text-align: left;
    font-size: 14px;
  }
}
</style>
