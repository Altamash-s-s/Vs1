<template>
  <div id="about" class="cstm-page-layout">
    <div class="head-section">
      <img class="hd-img" src="../assets/home/hs1.png">
    </div>

    <div class="main-section">
      <h2 class="hd-heading">ABOUT HUMAN ABSTRACT</h2>
    </div>

    <div class="content-section">
   
        <div class="tab">
          <button class="tablinks" @click="activateTab('firstTab')" :class="{ active: activeTab === 'firstTab' }">TEAM</button>
          <button class="tablinks" @click="activateTab('secondTab')" :class="{ active: activeTab === 'secondTab' }">BRAND VISION</button>
          <button class="tablinks" @click="activateTab('thirdTab')" :class="{ active: activeTab === 'thirdTab' }">ABOUT US</button>
        </div>

        <div id="firstTab" class="tabcontent" v-show="activeTab === 'firstTab'">
          
          <h3 class="heading-para">TEAM</h3>
          <img class="tab-img" src="../assets/home/hs11.png">
          <p class="para-text">It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using 'Content here, content here', making it look like readable English. Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a search for 'lorem ipsum' will uncover many web sites still in their infancy. Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).</p>
          <p class="para-text">It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using 'Content here, content here', making it look like readable English. Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a search for 'lorem ipsum' will uncover many web sites still in their infancy. Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).</p>
        </div>

        <div id="secondTab" class="tabcontent" v-show="activeTab === 'secondTab'">
          <h3 class="heading-para">BRAND VISION</h3>
          <img class="tab-img" src="../assets/home/hs13.png">
          <p class="para-text">It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using 'Content here, content here', making it look like readable English. Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a search for 'lorem ipsum' will uncover many web sites still in their infancy. Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).</p>
          <p class="para-text">It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using 'Content here, content here', making it look like readable English. Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a search for 'lorem ipsum' will uncover many web sites still in their infancy. Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).</p>
        </div>

        <div id="thirdTab" class="tabcontent" v-show="activeTab === 'thirdTab'">
          <h3 class="heading-para">ABOUT US</h3>
          <img class="tab-img" src="../assets/home/hs2.png">
          <p class="para-text">It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using 'Content here, content here', making it look like readable English. Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a search for 'lorem ipsum' will uncover many web sites still in their infancy. Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).</p>
          <p class="para-text">It is a long established fact that a reader will be distracted by the readable content of a page when looking at its layout. The point of using Lorem Ipsum is that it has a more-or-less normal distribution of letters, as opposed to using 'Content here, content here', making it look like readable English. Many desktop publishing packages and web page editors now use Lorem Ipsum as their default model text, and a search for 'lorem ipsum' will uncover many web sites still in their infancy. Various versions have evolved over the years, sometimes by accident, sometimes on purpose (injected humour and the like).</p>
        </div>
      </div>
  
  </div>
</template>

<script>
import '../css/cstm-page-layout.css';


export default {
  name: 'about',
  components: {},
  data() {
    return {
      activeTab: 'firstTab', // Set the default active tab
    };
  },
  methods: {
    activateTab(tabName) {
      this.activeTab = tabName;
    },
  },
};
</script>
<style>
.tab-img {
  width: 100%;
  padding-bottom: 15px;
}

* {box-sizing: border-box}


.tab {
float: left;
border: 1px solid #000;
width: 20%;
height: 250px;

}

.tab button {
display: block;
background-color: inherit;
color: black;
padding: 22px 16px;
width: 90%;
border: none;
outline: none;
text-align: left;
cursor: pointer;
transition: 0.3s;
font-size: 17px;
margin: 5%;
border-radius: 4px;
}

.tab button.active {
  color: #717171;
}

.tabcontent {
  float: left;
  padding: 0px 0px;
  width: 75%;
  border-left: none;
  margin-left: 62px;
}
.para-text{
  color: #302A2A;
  font-size: 15px;
  font-style: normal;
  font-weight: 400;
  line-height: 27px; 
  padding-bottom: 15px;
}
.heading-para{
  color: #302A2A;
  font-size: 18px;
  font-style: normal;
  font-weight: 400;
  line-height: normal;
  padding-bottom: 37px;
}
</style>