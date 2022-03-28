<template>
  <div ref="wrap" class="wrap">
    <ul
      ref="content"
      class="content"
      :class="animationClass"
      :style="contentStyle"
      @animationend="onAnimationEnd"
      @webkitAnimationEnd="onAnimationEnd"
    >
      <li v-for="(item, index) in content" :key="index">
        <span class="title" v-text="item.title"></span>
        <span class="date" v-text="item.date"></span>
      </li>
    </ul>
  </div>
</template>
<script>
export default {
  props: {
    content: {
      default: "",
    },
    delay: {
      type: Number,
      default: 0.5,
    },
    speed: {
      type: Number,
      default: 100,
    },
  },
  mounted() {},
  data() {
    return {
      wrapHeight: 0, //父盒子宽度
      firstRound: true, //判断是否
      duration: 0, //css3一次动画需要的时间
      offsetHeight: 0, //子盒子的宽度
      animationClass: "", //添加animate动画
    };
  },
  computed: {
    contentStyle() {
      return {
        //第一次从头开始,第二次动画的时候需要从最右边出来所以宽度需要多出父盒子的宽度
        paddingTop: (this.firstRound ? 0 : this.wrapHeight) + "px",
        //只有第一次的时候需要延迟
        animationDelay: (this.firstRound ? this.delay : 0) + "s",
        animationDuration: this.duration + "s",
      };
    },
  },
  watch: {
    content: {
      //监听到有内容,从后台获取到数据了,开始计算宽度,并计算时间,添加动画
      handler() {
        this.$nextTick(() => {
          const { wrap, content } = this.$refs;
          const wrapHeight = wrap.getBoundingClientRect().height;
          const offsetHeight = content.getBoundingClientRect().height;
          this.wrapHeight = wrapHeight;
          this.offsetHeight = offsetHeight;

          if (offsetHeight > wrapHeight) {
            this.duration = offsetHeight / this.speed;
            this.animationClass = "animate";
          }
        });
      },
      immediate: true,
    },
  },
  methods: {
    //这个函数是第一次动画结束的时候,第一次没有使用infinite,第一次动画执行完成后开始使用添加animate-infinite动画
    onAnimationEnd() {
      this.firstRound = false;
      //这是时候样式多出了padding-left:this.wrapHeight;所以要想速度一样需要重新计算时间
      this.duration = (this.offsetHeight + this.wrapHeight) / this.speed;
      this.animationClass = "animate-infinite";
    },
  },
};
</script>
<style scoped>
.wrap {
  height: 100%;
  overflow: hidden;
  position: relative;
  background: rgba(211, 125, 066, 1);
  position: relative;
  padding: 0;
}

.wrap .content {
  position: absolute;
  white-space: nowrap;
  width: 100%;
  padding: 1vw;
}

.content li {
  height: 6vh;
  line-height: 6vh;
  display: flex;
  justify-content: space-between;
  font-size: 1.5vw;
  color: #fff;
}

.animate {
  animation: paomadeng linear;
}

.animate-infinite {
  animation: paomadeng-infinite linear infinite;
}

@keyframes paomadeng {
  to {
    transform: translate3d(0, -100%, 0);
  }
}

@keyframes paomadeng-infinite {
  to {
    transform: translate3d(0, -100%, 0);
  }
}
</style>
