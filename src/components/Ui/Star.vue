<template>
<span class="star" :class="{lg: overallRaiting}">
  <svg version="1.1" id="Layer_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
	width="100%" height="100%" viewBox="0 0 512 512" enable-background="new 0 0 512 512" xml:space="preserve">
<polygon :fill="active || !overallRaiting ? '#40918C' : '#DCDCDC'" stroke-width="37.6152" stroke-linecap="round" stroke-linejoin="round" stroke-miterlimit="10" points="
	259.216,29.942 330.27,173.919 489.16,197.007 374.185,309.08 401.33,467.31 259.216,392.612 117.104,467.31 144.25,309.08 
	29.274,197.007 188.165,173.919 "/>
</svg>
</span>
</template>

<script>
  export default {
    name: 'Star', 
    props: {
      active: {
        type: Boolean,
        default: false
      },

      overallRaiting: {
        type: Boolean,
        default: false
      },
    },
  }
</script>

<style lang="scss" scoped>
    .star{
      cursor: pointer;
      max-width: 6.5%!important;
      &.lg{
        max-width: 14%!important;
      }
    }
</style>