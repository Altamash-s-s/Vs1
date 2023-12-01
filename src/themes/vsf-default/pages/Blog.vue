<template>
  <div id="Blog" class="cstm-page-layout">
    <div class="head-section">
      <img class="hd-img" src="../assets/home/blog.png">
    </div>

    <div class="blog-section">
      <div class="blog-grid">


          <div class="blog-one img-one">
            <img class="blog_img" src="../inside-blog/Blog-Images/BLOG PAGES-HOPE.jpg">
            <div class="content">
              <h4 class="hd-bg">Hope Blog</h4>
              <p class="bg-para">In the vast canvas of life, where challenges and uncertainties often paint our experiences,</p>
            <button  class="rd-mr-btn" @click="navigateTo('hopeblog')">Read More</button>
            </div>
          </div>

          <div class="blog-one img-two">
            <img class="blog_img" src="../inside-blog/Blog-Images/BLOG PAGES-ABSTRACT FACES.jpg">
            <div class="content">
              <h4 class="hd-bg">Abstract Human Faces</h4>
            <p class="bg-para">In a world that often seems to be moving at the speed of light, there is something.</p>
            <button  class="rd-mr-btn" @click="navigateTo('abstract')">Read More</button>
            </div>
          </div>

          <div class="blog-one img-three">
            <img class="blog_img" src="../inside-blog/Blog-Images/BLOG PAGES-CODE LIFE.jpg">
            <div class="content">
              <h4 class="hd-bg">CODE LIFE</h4>
              <p class="bg-para">In the digital realm, an intriguing life unfolds, hidden in plain sight—a life known intimately</p>
            <button class="rd-mr-btn" @click="navigateTo('codelife')">Read More</button>
            </div>
          </div>

          <div class="blog-one img-four">
            <img class="blog_img" src="../inside-blog/Blog-Images/BLOG PAGES-HUMAN X AI.jpg">
            <div class="content">
              <h4 class="hd-bg">Human x AI</h4>
              <p class="bg-para">In an age where artificial intelligence (AI) seems to be infiltrating every facet of our lives,</p>
            <button class="rd-mr-btn" @click="navigateTo('humanai')">Read More</button>
            </div>
          </div>

      </div>
    </div>

    <div class="blog-section second-section">
      <div class="blog-grid">


          <div class="blog-one img-five">
            <img class="blog_img" src="../inside-blog/Blog-Images/BLOG PAGES-WHO CARES.jpg">
            <div class="content">
              <h4 class="hd-bg">Who Cares?</h4>
              <p class="bg-para">In a world where conformity often takes precedence, a quiet revolution is underway.</p>
            <button class="rd-mr-btn" @click="navigateTo('whocare')">Read More</button>
            </div>
          </div>

          <div class="blog-one img-six">
            <img class="blog_img" src="../inside-blog/Blog-Images/BLOG PAGES-DRAGONFLY.jpg">
            <div class="content">
              <h4 class="hd-bg">Dragonfly Blog #9</h4>
            <p class="bg-para">In a world that relentlessly rushes by, where chaos and noise have become the prevailing norm,</p>
            <button class="rd-mr-btn" @click="navigateTo('dragonfly')">Read More</button>
            </div>
          </div>

          <div class="blog-one img-seven">
            <img class="blog_img" src="../inside-blog/Blog-Images/BLOG PAGES-HA BRANDING.jpg">
            <div class="content">
              <h4 class="hd-bg">HA Branding Blog #11</h4>
              <p class="bg-para">In a world saturated with conformity, Human Abstract emerges as a beacon</p>
            <button class="rd-mr-btn" @click="navigateTo('habranding')">Read More</button>
            </div>
          </div>

          <div class="blog-one img-eight">
            <img class="blog_img" src="../inside-blog/Blog-Images/BLOG PAGES-HAND GESTURES.jpg">
            <div class="content">
              <h4 class="hd-bg">HAND GESTURES</h4>
              <p class="bg-para">In a world where words wield immense power, being our most profound source of connection,</p>
            <button class="rd-mr-btn" @click="navigateTo('handgestures')">Read More</button>
            </div>
          </div>

      </div>
    </div>

    <div class="blog-section second-section">
      <div class="blog-grid">


          <div class="blog-one img-five">
            <img class="blog_img" src="../inside-blog/Blog-Images/BLOG PAGES-LOVE WITHOUT LIMITS.jpg">
            <div class="content">
              <h4 class="hd-bg">Love Without Limits Blog</h4>
              <p class="bg-para">Today, where simplicity often proves elusive, a profound beauty exists in embracing</p>
            <button class="rd-mr-btn" @click="navigateTo('lovewithoutlimits')">Read More</button>
            </div>
          </div>

          <div class="blog-one img-six">
            <img class="blog_img" src="../inside-blog/Blog-Images/BLOG PAGES-I'S.jpg">
            <div class="content">
              <h4 class="hd-bg">Multiple I’s</h4>
            <p class="bg-para">Amidst the ceaseless energy, where life moves at a frenzied pace– whispers are hushed.</p>
            <button class="rd-mr-btn" @click="navigateTo('multipleIs')">Read More</button>
            </div>
          </div>

          <div class="blog-one img-seven">
            <img class="blog_img" src="../inside-blog/Blog-Images/BLOG PAGES-NOT LAZY.jpg">
            <div class="content">
              <h4 class="hd-bg">Not Lazy, Just Resting Blog</h4>
              <p class="bg-para">In the relentless rhythm of today's world, each tick of the clock resonates with the hustle</p>
            <button class="rd-mr-btn" @click="navigateTo('notlazy')">Read More</button>
            </div>
          </div>

          <div class="blog-one img-eight">
            <img class="blog_img" src="../inside-blog/Blog-Images/BLOG PAGES-WARM EMBRACE.jpg">
            <div class="content">
              <h4 class="hd-bg">Warm Embrace</h4>
              <p class="bg-para">In a world brimming with myriad emotions and experiences, we often seek ways to convey</p>
            <button class="rd-mr-btn" @click="navigateTo('warmembrace')">Read More</button>
            </div>
          </div>

      </div>
    </div>

    <div class="blog-section second-section">
      <div class="blog-grid">


          <div class="blog-one img-five">
            <img class="blog_img" src="../inside-blog/Blog-Images/BLOG PAGES-HOT NOT SPICY.jpg">
            <div class="content">
              <h4 class="hd-bg">You are Hot, Not Spicy</h4>
              <p class="bg-para">Amidst the vivacious pulse of a bustling city, we set out to uncover an unspoken treasure</p>
            <button class="rd-mr-btn" @click="navigateTo('hotspicy')">Read More</button>
            </div>
          </div>

      </div>
    </div>
  </div>
</template>

<script>
import '../css/cstm-page-layout.css';
import CmsBlock from 'theme/components/core/blocks/Cms/Block';

export default {
  name: 'blog',
  components: {
    CmsBlock,
  },
  methods: {
    navigateTo(route) {
      this.$router.push(route);
    },
  },

};
</script>

<style scoped>

.blog-one {
    position: relative;
  }

  /* Initially hide the button */
  .rd-mr-btn {
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    display: none;
    color: #fff; 
    padding: 10px; 
    border: none;
    cursor: pointer;
    background-color: #0000;
    z-index: 2;
  }

  /* Show the button when the parent container is hovered */
  .blog-one:hover .rd-mr-btn {
    display: block;
  }

  /* Add a transparent overlay on hover */
  .blog-one::before {
    content: "";
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.75); /* Set your desired transparent color */
    display: none;
  }

  /* Show the overlay on hover */
  .blog-one:hover::before {
    display: block;
  }

.blog-one {
  position: relative;
  display: flex;
  flex-direction: column; 
  justify-content: flex-end; 
  border: 1px solid #00000026;
  cursor: pointer;
}

.content {
  color: #fff;
  padding: 20px;
  background-color: #000;
}
.blog-grid {
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  gap: 20px; 
}
.blog-section.second-section {
  margin-top: 0;
  margin-bottom: 50px;
}

.blog-grid-item {
  cursor: pointer;
}

.blog-section {
  margin-bottom: 50px;
  margin-top: 100px;
}
.hd-bg {
  color: #FFF;
  font-size: 19px;
  margin: 0;
}
.bg-para {
  color: #FFF;
  font-size: 15px;
}
button.rd-mr-btn {
  color: #FFF;
  font-size: 20px;

}
.blog_img {
    width: 100%;
    height: auto;
}
@media only screen and (min-device-width: 1200px) and (max-device-width: 1280px) {
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
}

@media only screen and (min-device-width: 768px) and (max-device-width: 991px) {
.blog-grid {
  display: grid;
  grid-template-columns: repeat(2, 1fr);
  gap: 40px;
}
.blog-section{
  margin-bottom: 38px;
  margin-top: 50px;
}
}

@media only screen and (min-device-width: 320px) and (max-device-width: 767px) {
.blog-grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 30px;
}
.blog-section{
  margin-bottom: 30px;
  margin-top: 50px;
}
}




</style>
