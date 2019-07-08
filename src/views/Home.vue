<template lang='pug'>
  .home
    img(alt="Vue logo" src="../assets/logo.png")
    Form(v-bind:fields='fields' v-model='fields')
    transition(name="slide-fade" mode='out-in')
      BussinessCard(:name='fields.name' v-if='mode===0')
      Resume(:name='fields.name' :experience='fields.experience' v-if='mode===1')
    button(v-on:click='pre') ←
    button(@click='next') →
</template>

<script>
// @ is an alias to /src
import Form from '../components/Form.vue'
import BussinessCard from '@/components/BussinessCard.vue'
import Resume from '@/components/Resume.vue'
export default {
  name: "home",
  data() {
    return {
      fields: {
        name: 'Rainforest',
        experience: [
          {
            date: '2016.07',
            title: '台大土木CAE暑期實習',
            description: '負責 Coursera 影片剪輯、石化管線資料庫視覺化網站的修改、以及拿災害相關文獻做斷詞及詞頻統計以建立語料庫'
          },
          {
            date: '2016.09',
            title: '畢業專題遊戲開發',
            description: '負責遊戲中戰鬥機制程式編寫'
          },
          {
            date: '2018.07',
            title: '衛武資訊研發部門 研發工程師',
            description: '負責產品 iOS, 網頁端開發'
          }
        ]
      },
      mode: 0
    }
  },
  mounted() {
    window.addEventListener('wheel', (event) => {
      if(event.deltaY > 0) {this.pre()}
      else if(event.deltaY < 0) {this.next()}
    })
  },
  methods: {
    pre(event) {
      this.mode = (2+this.mode-1)%2
    },
    next() {
      this.mode = (this.mode+1)%2
    }
  },
  components: {
    Form,
    BussinessCard,
    Resume
  }
};
</script>
<style lang="scss">
.slide-fade-enter-active {
  transition: all .3s ease;
}
.slide-fade-leave-active {
  transition: all .8s cubic-bezier(1.0, 0.5, 0.8, 1.0);
}
.slide-fade-enter, .slide-fade-leave-to
/* .slide-fade-leave-active below version 2.1.8 */ {
  transform: translateX(10px);
  opacity: 0;
}
</style>

