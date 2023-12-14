<template>
  <div>
    
    <div class="section" v-for="(imageClass, index) in imageClasses" :key="index" :class="{ 'active': index === activeSection }">
      <div class="image-container">
        <div :class="['image', imageClass]">

          <div class="collect_img_cnt">
            <img class="head-img-cl" src="../assets/collection/ha_text.svg">
            <a href="one-liner-winter-2023-24.html" class="section_btn">
              <div class="">
                <p>See All</p>
              </div>
            </a>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script lang="ts" type="module">
export default {
  name: 'collection',
  data() {
  return {
    imageClasses: ['img-1', 'img-2', 'img-3', 'img-4'],
    activeSection: 0, // Add activeSection to track the active section
  };
},
mounted() {
  window.addEventListener('scroll', this.changeImage);
  this.changeImage(); // Call it initially to set the initial state.
},
beforeDestroy() {
  window.removeEventListener('scroll', this.changeImage);
},
methods: {
  changeImage() {
    const scroll = window.scrollY + window.innerHeight / 4;
    this.imageClasses.forEach((imageClass, index) => {
      const el = document.querySelector(`.section:nth-child(${index + 1})`) as HTMLElement;
      if (!el) return;
      
      if (el.offsetTop <= scroll && el.offsetHeight + el.offsetTop > scroll) {
        this.activeSection = index; // Update the active section
      }
    });
  },
},
};
</script>
<style>
body {
margin: 0;
}
.img-1{
  background-image: url('../assets/collection/collection-3.png')
}
.img-2{
  background-image: url('../assets/collection/collection-4.png')
}
.img-3{
  background-image: url('../assets/collection/collection-6.png')
}
.img-4{
  background-image: url('../assets/collection/c1.png')
}

.section {
  display: flex;
  min-height: 100vh;
  position: relative;
}
.image-container {
  position: relative;
  display: flex;
}
.image {
  height: 100vh;
  position: fixed;
  width: 100%;
  top: 0;
  background-size: cover;
  background-position: bottom right;
  background-repeat: no-repeat;
  mix-blend-mode: multiply;
  opacity: 0;
  /* transition:  fade 0.5s ease; */
  transition: opacity .5s linear;
  z-index: -1;
}
.section.active .image {
  opacity: 1;
  transition: opacity .4s cubic-bezier(.25,.46,.45,.94);
}
h2.ha-head {
    position: sticky;
    top: 20rem;
    color: #FFF;
    z-index: 2;
    margin-left: 105px;
    font-size: 70px;
}
.collect_img_cnt {
    width: fit-content;
    position: absolute;
    top: 50%;
    transform: translateY(-50%);
    left: 5%;
}

.collect_img_cnt .section_btn {
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
  margin-top: 60px;
  position: relative;
  overflow: hidden;
  width: 100%;
  max-width: 92px;
}
.collect_img_cnt .section_btn:hover {
  background: #00000029;
  color: #FFF;
  border: 1px solid #FFF;
}
.collect_img_cnt .section_btn div {
  width: 100%;
  float: left;
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}
.collect_img_cnt .section_btn div p {
  margin: 0;
  margin-left: 12px;
  transition: all 0.4s;
}
.collect_img_cnt .section_btn:hover div p {
  margin-left: -6px;
}
.collect_img_cnt .section_btn div img {
  width: 20px;
  margin-left: 7px;
  display: none;
}
.collect_img_cnt .section_btn div::after {
  content: '';
  background-image: url('../assets/icons/chevron-1.svg');
  position: absolute;
  width: 20px;
  height: 20px;
  top: -2px;
  right: -12px;
  background-size: cover;
  opacity: 0;
  transition: all 0.4s;
}
.collect_img_cnt .section_btn:hover div::after {
  opacity: 1;
}
</style>