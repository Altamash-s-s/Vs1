<template>
  <div class="dv3 winter_collection">
    <div class="dv3_inner">
      <!-- 1 -->
      <div class="bg bg1 bg_sec">
        <!-- <h1 class="collection-hd">Human Abstract</h1> -->
        <img class="head-img-cl" src="../../assets/collection/ha_text.svg">
        <a href="./ha-winter-23-24.html" class="section_btn">
          <div class="">
            <p>See All</p>
          </div>
        </a>
        <img class="model_img" src="../../assets/collection/collection-2.png" />
      </div>
      <div class="bg bg1 bg_sec">
         <!-- <h1 class="collection-hd">Human Abstract</h1> -->
         <img class="head-img-cl" src="../../assets/collection/ha_text.svg">
        <a href="ha-winter-23-24.html" class="section_btn">
          <div class="">
            <p>See All</p>
          </div>
        </a>
        <img class="model_img" src="../../assets/collection/collection-2.png" />
      </div>
      <div class="bg bg1 bg_sec">
         <!-- <h1 class="collection-hd">Human Abstract</h1> -->
         <img class="head-img-cl" src="../../assets/collection/ha_text.svg">
        <a href="ha-winter-23-24.html" class="section_btn">
          <div class="">
            <p>See All</p>
          </div>
        </a>
        <img class="model_img" src="../../assets/collection/collection-2.png" />
      </div>
    
      <!-- 2 -->
      <div class="bg bg2 bg_sec">
         <!-- <h1 class="collection-hd">Human Abstract</h1> -->
         <img class="head-img-cl" src="../../assets/collection/ha_text.svg">
        <a href="ha-winter-23-24.html" class="section_btn">
          <div class="">
            <p>See All</p>
          </div>
        </a>
        <img class="model_img" src="../../assets/collection/collection-5.png" />
      </div>
      <div class="bg bg2 bg_sec">
         <!-- <h1 class="collection-hd">Human Abstract</h1> -->
         <img class="head-img-cl" src="../../assets/collection/ha_text.svg">
        <a href="ha-winter-23-24.html" class="section_btn">
          <div class="">
            <p>See All</p>
          </div>
        </a>
        <img class="model_img" src="../../assets/collection/collection-5.png" />
      </div>
      <div class="bg bg2 bg_sec">
         <!-- <h1 class="collection-hd">Human Abstract</h1> -->
         <img class="head-img-cl" src="../../assets/collection/ha_text.svg">
        <a href="ha-winter-23-24.html" class="section_btn">
          <div class="">
            <p>See All</p>
          </div>
        </a>
        <img class="model_img" src="../../assets/collection/collection-5.png" />
      </div>
      <!-- 5 -->
 
      <!-- 6 -->
  
    </div>
  </div>
</template>
<script>
export default {
};
</script>
<style>
body {
  margin: 0;
}
.dv3 .winter_collection {
  width: 100%;
  min-height: 100vh;
  position: relative;
}
.dv3_inner {
  top: 0;
  position: sticky;
  position: -webkit-sticky;
  
  width: 100%;
  height: 100vh;
  background:url('../../assets/collection/collection_bg1 (2).png');
  background-size: cover;
  background-repeat: no-repeat;
  background-position: center;
}
.bg {
  width: 100%;
  height: 100%;
  position: absolute;
  top: 0;
  left: 0;
  opacity: 0;
  transition: opacity 0.3s;
}
.bg.active {
  opacity: 1;
}
.bg .model_img{
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: top;
  position: absolute;
  top: 0;
  z-index: -1;
}
h1.collection-hd {
  position: absolute;
  top: 45%;
  left: 90px;
  color: #FFFF;
  font-size: 67px;
}
.section_btn {
  background-color: #FFF;
  border-color: #fff;
  border: 1px solid #FFF;
  backdrop-filter: blur(2px);
  color: #000;
  font-weight: 400;
  padding: 16px 30px;
  width: -moz-fit-content;
  width: fit-content;
  font-size: 15px;
  text-transform: uppercase;
  letter-spacing: 1px;
  display: block;
  margin: auto;
  margin-top: 30px;
  position: relative;
  overflow: hidden;
  width: 100%;
  max-width: 92px;
  position: absolute;
  top: 57%;
  left: 15%;
}
.section_btn:hover {
  background: #00000029;
  color: #FFF;
  border: 1px solid #FFF;
}
.section_btn div {
  width: 100%;
  float: left;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}
.section_btn div p {
  margin: 0;
  margin-left: 12px;
  transition: all 0.4s;
}
.section_btn:hover div p {
  margin-left: -6px;
}
.section_btn div img {
  width: 20px;
  margin-left: 7px;
  display: none;
}
.section_btn div::after {
  content: '';
  background-image: url('../../assets/icons/chevron-1.svg');
  position: absolute;
  width: 20px;
  height: 20px;
  top: -2px;
  right: -12px;
  background-size: cover;
  opacity: 0;
  transition: all 0.4s;
}
.section_btn:hover div::after {
  opacity: 1;
}
.head-img-cl {
    width: 700px !important;
    z-index: 10;
    position: absolute;
    top: 50%;
    left: 3%;
    height: auto !important; 
}
@media only screen and (min-device-width: 1281px) and (max-device-width: 1369px) {
}
@media only screen and (min-device-width: 1370px) and (max-device-width: 1440px) {
}
@media only screen and (min-device-width: 1441px) and (max-device-width: 1536px) {
}
@media only screen and (min-device-width: 1537px) and (max-device-width: 1600px) {

}
@media only screen and (min-device-width: 992px) and (max-device-width: 1199px) {
  .head-img-cl {
    width: 600px !important;
  }
  .section_btn {
    top: 60%;
    left: 23%;
  }
  .dscrpt-txt{
    font-size: 19px !important;
    line-height: 32px !important;
}
.parallax-section {
    height: 60vh !important;
}
.bg .model_img {
    object-fit: fill;
    object-position: right;
}
}
@media only screen and (min-device-width: 768px) and (max-device-width: 991px) {
  .bg .model_img {
    object-position: right;
  }
  .head-img-cl {
    width: 550PX !important;
    left: 17%;
    bottom: 15% !important;
    top: auto;
  }
  .section_btn div p {
    margin-left: 0px;
  }
  .section_btn {
    padding: 14px 24px;
    top: auto;
    left: 42%;
    bottom: 35px;
}
.parallax-section{
    height: 45vh !important;
}
}

@media only screen and (min-device-width: 320px) and (max-device-width: 767px) {

  .parallax-section{
    height: 25vh !important;
  }
  .bg .model_img {
    object-position: right;
  }
  .head-img-cl {
    width: 372px !important;
    left: 6%;
    bottom: 12%;
    top: auto;
  }
  .section_btn {
    top: auto;
    bottom: 22px;
    left: 31%;
}


}
</style>