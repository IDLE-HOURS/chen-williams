<template lang="pug">
  router-link(to="/")
    img.z2(src='../../assets/logo.svg', :class="{'nav-logo--condensed': condensed}", alt="Chen Williams Logo")
</template>

<script>
export default {
  name: 'NavLogo',
  props: ['condensed']
}
</script>

<style lang="scss" scoped>
@import '../../style/variables';

// Mobile
@include mobile {
  img{
    width: 2rem;
    position: fixed;
    left: 1rem;
    bottom: 1.5rem;
    z-index:100;
  }
}

// Desktop
@include grid9 {
  img{
    position: absolute;
    width:50%;
    top:rem(-6px); 
    left:rem(-6px);
    // transform:translateX(rem(-6px)) translateY(rem(-6px));
    will-change:transform;
    transition: transform $navCondenseDuration;
    transform-origin:top left;
    &.nav-logo--condensed{
      transform:scale(0.66,0.66);
    }
  }
}
</style>