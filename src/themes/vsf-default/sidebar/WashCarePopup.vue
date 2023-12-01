<template>
    <div class="popup-overlay" @click="closePopup">
      <div class="popup" @click.stop>
        <!-- Add a cancel icon in the top-right corner -->
        <button class="popup-cancel" @click="closePopup">&#10005;</button>
        <div class="popup-content">
          <h3 class="popup-head">Wash Care</h3>
        <ul class="popup-text">
          <li>Following the right wash care instructions and methods are essential to preserve the condition and functionality of the products, reducing environmental impact and utility costs.</li>
          <li>Full load machine (avoid less clothes or over all loaded machine washes).</li>
          <li>Wash in low temperature (at or below 30C).</li>
          <li>Wash in cold temperature - Washing clothes on a hot cycle uses 75% more energy than cold water and warm water is also more likely to break down dyes and cause shrinkage.</li>
          <li>Low spin wash - reduces pilling and saves energy.</li>
          <li>Turn clothes inside out while washing to avoid damage to the print on the T-shirts.</li>
          <li>Preferably hand wash in cold water if it is embroidered or has beadwork.</li>
          <li>Do not bleach.</li>
          <li>Secret tip - Air out your clothes - you don't have to always wash a garment, instead just let it soak in the sun or brush it.</li>
        </ul>
        </div>
      </div>
    </div>
  </template>
  
  <script>
  import popup from './popup.css';
  export default {
    name: 'WashCarePopup',
    methods: {
      closePopup() {
        this.$emit('close-popup');
      },
    },
  };
  </script>
  
  <style scoped>
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
  .popup-head {
    display: flex;
    justify-content: center;
}
  
  .popup {
    background: #fff;
    padding: 60px;
    max-width: 47%;
    border-radius: 10px;
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
    font-size: 24px;
    margin-bottom: 10px;
  }
  
  .popup-text {
    color: #333;
    font-size: 17px;
    font-family: 'PoppinsRegular';
    line-height: 31px;
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


}
  </style>
  