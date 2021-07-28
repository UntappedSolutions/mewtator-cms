<template>
  <g-link to="/" class="logo" title="Back to home">
    <div>
    <g-image src="~/assets/img/logo-trans.png" alt="logo" />
    </div>
  </g-link>
</template>

<script>
export default {
  props: {
    color: {
      type: String,
      required: true
    }
  }
}
</script>

<style lang="scss" scoped>
.logo {
  width: 200px;
  display: block;
  transition: color .15s ease-in-out;
  color: $textBright;
  position: relative;
  perspective: 200px;

  div {
    width: 200px;
    position: absolute;
    top: 0;
    left: 0;
  }

  img {
    width: 100%;
    height: auto;
  }
}

.theme-enter-active, .theme-leave-active {
  transition: opacity .15s ease-in-out;
}
.theme-enter, .theme-leave-to /* .fade-leave-active below version 2.1.8 */ {
  opacity: 0;
}
</style>


