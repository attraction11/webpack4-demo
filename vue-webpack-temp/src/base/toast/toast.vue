<template>
    <transition name="mint-toast-pop">
        <div class="mint-toast" v-show="visible" :class="customClass"
             :style="{ 'padding': iconClass === '' ? '10px' : '20px' }">
            <i class="mint-toast-icon" :class="iconClass" v-if="iconClass !== ''"></i>
            <span class="mint-toast-text"
                  :style="{ 'padding-top': iconClass === '' ? '0' : '10px' }">{{ message }}</span>
        </div>
    </transition>
</template>

<script type="text/babel">
  export default {
    props: {
      message: String,
      className: {
        type: String,
        default: ''
      },
      position: {
        type: String,
        default: 'middle'
      },
      iconClass: {
        type: String,
        default: ''
      }
    },
    data() {
      return {
        visible: false
      };
    },
    computed: {
      customClass() {
        var classes = [];
        switch (this.position) {
          case 'top':
            classes.push('is-placetop');
            break;
          case 'bottom':
            classes.push('is-placebottom');
            break;
          default:
            classes.push('is-placemiddle');
        }
        classes.push(this.className);
        return classes.join(' ');
      }
    }
  };
</script>

<style scoped lang="stylus" rel="stylesheet/stylus">
    @import "~common/stylus/variable"
    .mint-toast
        position fixed
        max-width 80%
        border-radius 5px
        background rgba(0, 0, 0, 0.7)
        color #fff
        box-sizing border-box
        text-align center
        z-index 1000
        text-align center
        transition opacity .3s linear
        left 50%
        top 50%
        transform translate(-50%, -50%)
        .mint-toast-icon
            display block
            text-align center
            font-size 56px
        .mint-toast-text
            font-size 14px
            display block
            text-align center
</style>
