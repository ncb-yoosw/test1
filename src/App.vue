<template>

  <div class="black-bg" v-if="modal_flg == true">
    <div class="white-bg">
      <h4>상세페이지</h4>
      <p>상세페이지 내용</p>
    <button @click="modal_flg = false"> X  </button>
    </div>
  </div>

  <div class = "menu">
    <a v-for="A in Headermenu" :key="A"> {{ A }}</a>
  </div>

  <!-- <div v-for="B in products" :key="B">
    <h4 class = "red" :style="style1">{{B}}</h4>
    <p>{{ price1 }} 만원</p>
  </div> -->
  <div>
    <img :src = "room[0].image" class="room-img">
    <h4 @click="modal_flg = true" class = "red" :style="style1">{{room[0].title}}</h4>
    <p> {{room[0].price}} 원</p>
    <button @click = "increase">허위매물신고</button> <span> 신고수 : {{reportCnt}}</span>
  </div>
</template>

<script>

import roomData from './assets/data.js';

export default {
  name: 'App',
  data() {
    return {
      //데이터보관 오브젝트
       room : roomData,
       modal_flg : false,
       reportCnt: 0,
       Headermenu : ['Home','Shop','About1'],
       products : ['역삼동원룸1','역삼동원룸2','역삼동원룸3']
    }
  },
  methods: {
    increase(){
      this.reportCnt += 1;
    }
  },
  components: {
  }
}
</script>

<style>

body {
  margin :0
}
div {
  box-sizing: border-box;
}
.black-bg {
  width: 100%; height: 100%;
  background: rgba(0, 0, 0, 0.5);
  position: fixed; padding: 20px;
}
.white-bg {
  width: 100%; background: white;
  border-radius: 8px;
  padding: 20px;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

.menu {
  background: darkblue;
  padding: 15px;
  border-radius: 5px;
}
.menu a {
  color: white;
  padding: 15px;
}
.room-img {
  width: 100%;
  margin-top: 40px;
}
</style>
