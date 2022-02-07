<template>
  <div id="app">

    <div class="black-bg" v-if="모달창열렸니==true">
      <div class="white-bg">
        <img :src="require(`@/assets/${products[selIdx].imgPath}`)" class="room-smallImg" />
        <h4>{{products[selIdx].name}}</h4>
        <p>{{products[selIdx].price}}</p>
        <button @click="모달창열렸니=false">닫기</button>
      </div>
    </div>

    <div class ="menu">
      <a v-for="메뉴 in 메뉴들" :key="메뉴">
        {{메뉴}}
      </a>
    </div>

    <div v-for="(product, idx) in products" :key="idx">
      <img :src="require(`@/assets/${product.imgPath}`)" class="room-img" />
      <h4 @click="popupDlg(idx)">{{product.name}}</h4>
      <p>{{product.price}}</p>
      <button @click="increaseFake(idx)">허위매물신고</button> <span>신고수:{{product.신고수}}</span>
    </div>

  </div>
</template>

<script>

export default {
  name: 'app',
  data(){
    return {
      selIdx : -1,
      모달창열렸니: false,
      메뉴들 : ['Home', 'Shop', 'About '],
      products : [
        {
          imgPath : "image/oneRoom_1.jpg",
          name : '역삼동 원룸',
          price : 50,
          신고수 : 0 }
        ,{
          imgPath : "image/oneRoom_2.jpg",
          name : '천호동 원룸',
          price : '가격은 아무거나',
          신고수 : 0}
        , {
          imgPath : "image/oneRoom_3.jpg",
          name : '마포구 원룸',
          price : '가격은 아무거나',
          신고수 : 0}
      ]
    }
  },
  methods : {
    increaseFake( idx ){
      this.products[idx].신고수 += 1;
    },
    popupDlg( idx ){
      this.모달창열렸니=true;
      this.selIdx = idx;
    }
  },
  components: {

  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}

body{
  margin : 0
}

div {
  box-sizing : border-box;
}

.black-bg{
  width: 100%;
  height: 100%;
  background : rgba( 0,0,0,0.5);
  position: fixed;
  padding : 20px;
}

.white-bg{
  width: 100%;
  background: white;
  border-radius : 8px;
  padding : 20px;
}


.room-img{
  width : 100%;
  margin-top : 40px;
}

.room-smallImg{
  width : 50%;
  margin-top : 40px;
}

.menu{
  background : darkslateblue;
  padding : 15px;
  border-radious : 5px;
}

.menu a{
  color : white;
  padding: 10px;

}

</style>
