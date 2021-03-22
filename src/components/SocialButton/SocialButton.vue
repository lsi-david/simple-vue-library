<template>
  <button
    type="button"
    class="social-btn"
    :style="{'background-color': background}"
  >
    <i :class="`social-btn-icon ${icon}`"></i>
  </button>
</template>

<script>
export default {
  name: 'SocialButton',
  props: {
    icon: String,
    background: String,
    onClick: {
      type: Function,
      required: true,
      default() {
        return () => true;
      },
    },
  },
};
</script>

<style scoped>
.social-btn {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 70px;
  width: 70px;
  border-radius: 50%;
  border: none;
  transition-duration: 0.5s;
  transform: rotateX(45deg);
  box-shadow: 0px 10px 5px rgba(0, 0, 0, 0.3);
  cursor: pointer;
}

.social-btn:hover {
  transform: scale(1.2);
  box-shadow: none;
}

.social-btn-icon {
  font-size: 33px;
  letter-spacing: 0.1em;
  color: #fff;
}
</style>
