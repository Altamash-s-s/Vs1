<template>
    <div>
      <div class="overlay" @click="closeSidebar" v-if="isOpen"></div>
      <div class="right-sidebar" :class="{ open: isOpen }">
        <!-- Sidebar content goes here -->
        <button class="close_btn" @click="closeSidebar">
          <img class="close_icon" src="../assets/icons/close.svg">
        </button>
        <div class="main-form main-form" style="height: calc(100% - 80px); overflow-y: auto;" >
          <h2 class="main-hd main-hd">Collabration Form</h2>
          <collabrationForm  /> 
        </div>
      </div>
    </div>
  </template>
  
  <script>
import collabrationForm from './collabrationForm.vue';

  export default {
    name: 'collabrationSidebar',
    components: {
        collabrationForm,
    },
    data() {
        return {
            isOpen: false,
        };
    },
    created() {
        // Add a click event listener to the document to close the sidebar
        document.addEventListener('click', this.handleDocumentClick);
    },
    destroyed() {
        // Remove the event listener when the component is destroyed
        document.removeEventListener('click', this.handleDocumentClick);
    },
    methods: {
        openSidebar() {
            this.isOpen = true;
        },
        closeSidebar() {
            this.isOpen = false;
        },
    },
};
  </script>
  
  <style scoped>
  .overlay {
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    height: 100%;
    background-color: rgba(0, 0, 0, 0.5); /* Semi-transparent background color */
    z-index: 999; /* Place it below the sidebar */
    pointer-events: none; /* Make the overlay non-interactive */
  }
  
  .right-sidebar {
    position: fixed;
    top: 0;
    right: -300px;
    width: 300px;
    height: 100%;
    background-color: #fff;
    box-shadow: 0 0 10px rgba(0, 0, 0, 0.2);
    transition: right 0.3s;
    z-index: 999;
  }
  
  .right-sidebar.open {
    right: 0;
    width: 700px;
  }
  
  .sidebar-content {
    padding: 20px;
  }
     /* Form Css start here  */
 .main-hd{
    margin-left: 35px;
    margin-top: 0;
    font-family: 'PoppinsRegular';
 }
.close_btn {
    background: #FFF;
    display: block;
    margin: auto;
    margin-right: 27px;
}
.close_icon {
    width: 6%;
    height: 6%;
    display: block;
    margin: 0 auto;
    float: right;
}
@media only screen and (min-device-width: 320px) and (max-device-width: 767px) {
  .right-sidebar.open {
    right: 0;
    width: auto;
}
}
@media only screen and (max-width: 767px) {
    .right-sidebar.open {
        right: 0 !important;
        width: auto !important;
        padding: 0 20px !important;
    }
    
    .main-hd{
        margin-left: 0;
        margin-top: 0;
        font-family: 'PoppinsRegular';
    }
    
    .close_btn {
        background: #FFF;
        display: block;
        margin: auto;
        margin-right: 0;
        padding-right: 0px;
        padding-top: 15px;
    }
    
    .inside-hd {
        margin-top: 20px;
        font-size: 26px;
        line-height: 36px;
        margin-bottom: 0;
    }
    }




     /* Form Css start end here  */

  </style>
  