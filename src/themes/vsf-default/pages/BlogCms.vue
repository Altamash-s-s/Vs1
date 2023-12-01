<template>
    <div id="Blog" class="cstm-page-layout">
      <div class="head-section">
        <img class="hd-img" src="../assets/home/img-1.png">
      </div>
  
      <div class="blog-section">
        <div class="blog-grid">


            <div class="blog-one img-one">
              <div class="content">
                <h4 class="hd-bg">Hello World</h4>
                <p class="bg-para">Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum enim quis repudiandae</p>
              <button class="rd-mr-btn">Read More</button>
              </div>
            </div>

            <div class="blog-one img-two">
              <div class="content">
                <h4 class="hd-bg">Hello World</h4>
              <p class="bg-para">Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum enim quis repudiandae</p>
              <button class="rd-mr-btn">Read More</button>
              </div>
            </div>

            <div class="blog-one img-three">
              <div class="content">
                <h4 class="hd-bg">Hello World</h4>
                <p class="bg-para">Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum enim quis repudiandae</p>
              <button class="rd-mr-btn">Read More</button>
              </div>
            </div>

            <div class="blog-one img-four">
              <div class="content">
                <h4 class="hd-bg">Hello World</h4>
                <p class="bg-para">Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum enim quis repudiandae</p>
              <button class="rd-mr-btn">Read More</button>
              </div>
            </div>

        </div>
      </div>

      <div class="blog-section second-section">
        <div class="blog-grid">


            <div class="blog-one img-five">
              <div class="content">
                <h4 class="hd-bg">Hello World</h4>
                <p class="bg-para">Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum enim quis repudiandae</p>
              <button class="rd-mr-btn">Read More</button>
              </div>
            </div>

            <div class="blog-one img-six">
              <div class="content">
                <h4 class="hd-bg">Hello World</h4>
              <p class="bg-para">Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum enim quis repudiandae</p>
              <button class="rd-mr-btn">Read More</button>
              </div>
            </div>

            <div class="blog-one img-seven">
              <div class="content">
                <h4 class="hd-bg">Hello World</h4>
                <p class="bg-para">Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum enim quis repudiandae</p>
              <button class="rd-mr-btn">Read More</button>
              </div>
            </div>

            <div class="blog-one img-eight">
              <div class="content">
                <h4 class="hd-bg">Hello World</h4>
                <p class="bg-para">Lorem ipsum dolor sit amet consectetur adipisicing elit. Nostrum enim quis repudiandae</p>
              <button class="rd-mr-btn">Read More</button>
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
    name: 'BlogCms',
    components: {
      CmsBlock,
    },

  };
  </script>
  
  <style scoped>

.blog-one {
    position: relative;
    padding: 20px;  
    height: 95%;
    display: flex;
    flex-direction: column; 
    justify-content: flex-end; 
  }

  .blog-one::before {
    content: '';
    position: absolute;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.5);
    z-index: 1;
  }

  .content {
    z-index: 2; 
    color: #fff;
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
  .blog-one.img-one{
    background-image: url('../assets/home/hs1.png');
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
.blog-one.img-two{
    background-image: url('../assets/home/hs2.png');
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
.blog-one.img-three{
    background-image: url('../assets/home/img-1.png');
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
.blog-one.img-four{
    background-image: url('../assets/home/img-2.png');
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
.blog-one.img-five{
    background-image: url('../assets/home/hs1.png');
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
.blog-one.img-six{
    background-image: url('../assets/home/hs13.png');
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
.blog-one.img-seven{
    background-image: url('../assets/home/img-1.png');
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
.blog-one.img-eight{
    background-image: url('../assets/home/hs1.png');
    background-position: center;
    background-repeat: no-repeat;
    background-size: cover;
}
.blog-section {
    margin-bottom: 100px;
    margin-top: 100px;
}
.content {
    padding-top: 175px;
}
.hd-bg {
    color: #FFFF;
    font-size: 25px;
}
.bg-para {
    color: #FFFF;
}
button.rd-mr-btn {
    background-color: #FFF;
    border: 0;
    padding: 10px;
    border-radius: 10px;
}
button.rd-mr-btn:hover {
    color: #FFFF;
    background-color: #4d4c4c44;
    border: 0;
    padding: 10px;
    border-radius: 10px;
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
    margin-top: 100px;
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
  