<template>
    <div class="popup-overlay" @click="closePopup">
      <div class="popup" @click.stop>
        <!-- Add a cancel icon in the top-right corner -->
        <button class="popup-cancel" @click="closePopup">&#10005;</button>
        <div class="popup-content">            
            <div class="heading-bg-img-pop">
              <h3 class="popup-head">Extra Care</h3>
          </div>
        <ul class="popup-text">
          <li>To avoid pilling, wash inside out / use lint remover </li>
          <li>Iron at low temperature </li>
          <li>Turn clothes inside out while ironing to avoid damage to the print or embroidery</li>
          <li>Opt for wet cleaning service instead of dry cleaning as it is considered to be more sustainable because it does not involve the use of hazardous solvents</li>
        </ul>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import './popup.css';
  export default {
    name: 'ExtraCarePopup',
    methods: {
      closePopup() {
        this.$emit('close-popup');
      },
    },
  };
  </script>
  
  <style scoped>
      .heading-bg-img-pop {
    padding: 24px;
    background-image: url('/assets/patch_img.jpg');
    background-repeat: no-repeat;
    background-size: cover;
    background-position: center;
}
    .popup-head {
    display: flex;
    justify-content: center;
}
  .popup-overlay {
    display: none;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background: rgba(0, 0, 0, 0.7);
    z-index: 1000;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer; /* Show pointer cursor */
  }
  
  .popup {
    background: #fff;
    max-width: 47%;
    position: relative; /* Added to position the cancel button */
  }
  
  .popup-cancel {
    position: absolute;
    top: 10px;
    right: 10px;
    background: #fff;
    border: none;
    font-size: 24px;
    cursor: pointer;
    color: #999;
  }
  
  .popup-head {
    color: #000;
    font-size: 34px;
    margin-bottom: 10px;
  }
  
  .popup-text {
    color: #333;
    font-size: 17px;
    font-family: 'PoppinsRegular';
    line-height: 31px;
    padding: 20px 71px !important;
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
          .popup{
            padding: 49px;
            max-width: 75%;
        }
             
}

@media only screen and (min-device-width: 768px) and (max-device-width: 991px) {
  .popup{
    background: #fff;
    padding: 54px;
    max-width: 78%;
    border-radius: 10px;
    position: relative;
}


}

@media only screen and (min-device-width: 320px) and (max-device-width: 767px) {
  .popup-content {
    max-height: 500px;
    overflow: scroll;
}
.popup {
    background: #fff;
    padding: 15px;
    max-width: 80%;
    border-radius: 10px;
    position: relative;
}
.popup-text {
    padding-left: 30px !important;
    padding-right: 30px !important;
}


}
  </style>
  