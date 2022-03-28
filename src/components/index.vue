<template>
  <div>
    <PaoMaDeng :delay="0.5" :speed="100" :content="arr">
      <span v-for="(item, index) in arr" :key="index">{{item}}</span>
    </PaoMaDeng>
    <Marquee :delay="0.5" :speed="100" :content="listData"></Marquee>
  </div>
</template>

<script>
  import PaoMaDeng from 'heyushuo-marquee';
  import Marquee from 'Marquee';
  export default {
    components: {
      PaoMaDeng,
      Marquee
    },
    name: 'HelloWorld',
    mounted() {
      this.arr = ['手机用户:151****013获得二等奖', "科比:获得一个篮球", "网友:获得现金5元"]
    },
    data() {
      return {
        arr: [],
              listData: [
        {
          title: "无缝滚动第一行111111",
          date: "2017-12-16",
        },
        {
          title: "第二行无缝滚动第二行",
          date: "2017-12-16",
        },
        {
          title: "无缝滚动第三行无缝滚动第三行",
          date: "2017-12-16",
        },
        {
          title: "无缝滚动第四行无缝滚动第四行",
          date: "2017-12-16",
        },
        {
          title: "无缝滚动第五行无缝滚动第五行",
          date: "2017-12-16",
        },
        {
          title: "无缝滚动第六行无缝滚动第六行",
          date: "2017-12-16",
        },
        {
          title: "无缝滚动第七行无缝滚动第七行",
          date: "2017-12-16",
        },
        {
          title: "无缝滚动第八行无缝滚动第八行",
          date: "2017-12-16",
        },
        {
          title: "第九行无缝滚动第九行",
          date: "2017-12-16",
        },
        {
          title: "无缝滚动第一行",
          date: "2017-12-16",
        },
        {
          title: "第二行无缝滚动第二行",
          date: "2017-12-16",
        },
        {
          title: "无缝滚动第三行无缝滚动第三行",
          date: "2017-12-16",
        },
        {
          title: "无缝滚动第四行无缝滚动第四行",
          date: "2017-12-16",
        },
        {
          title: "无缝滚动第五行无缝滚动第五行",
          date: "2017-12-16",
        },
        {
          title: "无缝滚动第六行无缝滚动第六行",
          date: "2017-12-16",
        },
        {
          title: "无缝滚动第七行无缝滚动第七行",
          date: "2017-12-16",
        },
        {
          title: "无缝滚动第八行无缝滚动第八行",
          date: "2017-12-16",
        },
        {
          title: "第九行无缝滚动第九行222222",
          date: "2017-12-16",
        },
      ],
      }
    },
    computed: {},
  }
</script>
<style scoped>
  span {
    font-size: 12px;
    margin-right: 20px;
  }
</style>