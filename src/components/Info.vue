<template lang="pug">
  article.info-overlay.fixed.overlay.h-100vh.z-overlay.bg-gray.backdrop-blur.overflow-y-scroll
    overlay-header.absolute.top-0.left-0.w-100(@close="$router.push({hash: null})", title="Info")   
    .relative.p2.pb-50vh.overflow-y-hidden
      transition(name="fade")
        .pt-1row.flex.mbl-block.left-align.underline-links(v-if="info")
          section.mb1.clear
            div.info-overlay__body.flex.flex-wrap.justify-between(v-html="$options.filters.richtext(info.main)")
          aside.mbl-mt3
            div.mb2
              div(v-html="$options.filters.richtext(info.subscribe_form_description)")
              subscribe.mt075
            div(v-html="$options.filters.richtext(info.sidebar)")
      background(color="gray").absolute.overlay.z_-1
</template>

<script>
import Background from '@/components/DotGrid'
import OverlayHeader from '@/components/OverlayHeader'
import Subscribe from '@/components/Subscribe'
export default {
  name: 'Info',
  components: { Background, OverlayHeader, Subscribe },
  computed: {
    info () {
      return this.$store.state.info
    }
  },
  beforeCreate () {
    this.$store.dispatch('getInfo')
  }
}
</script>

<style lang="scss" scoped>
@import '../style/variables';

@include grid9 {
  section{
    flex:0 0 cols(5,9);
    div{ padding-right: 20%; }
  }
  aside{
    flex:0 0 cols(3,9);
  }
}

@include grid12 {
  section{
    flex:0 0 cols(5,12); 
  }
  aside{
    flex:0 0 cols(4,12); 
  }
}

@include grid15 {
  section{
    flex:0 0 cols(5,15);
  }
  aside{
    flex:0 0 cols(4,15);
  }
}
</style>

<style lang="scss">
@import '../style/variables';
.info-overlay__body{
  > * {
    flex:1 0 100%;
    width:100%;
    max-width:100%;
    &.block-img {
      flex:0 0 25%;
      max-width:25%;
      padding-right: 1em;
      a {
        border-bottom:none;
      }

      @include mobile{
        flex:0 0 50%;
        max-width: 50%;
      }
    }
  }
}
</style>
