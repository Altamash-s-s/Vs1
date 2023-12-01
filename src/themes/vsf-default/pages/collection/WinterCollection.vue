<template>
    <div>
        <div class="video-element">
            <div class="parallax-section snap">
                <div class="parallax-image section5">
                    <!-- <video src="../static/homepage/home-video.mp4" playsinline autoplay muted loop></video> -->
                    <img class=top-img src="../../assets/collection/ONE LINER COLLECTION PAGE TOP FOLD-01.jpg">
                </div>
            </div>
            
        </div>
        <div class="description-container">
            <p class="dscrpt-txt">In publishing and graphic design, &amp;Lorem ipsum is a placeholder text commonly used to
                    demonstrate <br> The visual form of a document or a typeface without relying on meaningful content. <br>Lorem
                    ipsum may be used as a placeholder before final copy is available</p>
        </div>
        <div class="collection-section">
            <WinterCollectionSlider></WinterCollectionSlider>
        </div>
    </div>
</template>
  
<script>
import WinterCollectionSlider from './WinterCollectionSlider.vue';
export default {
    name: 'WinterCollection',
    data() {
        return {
            loading: true
        };
    },
    components: {
        WinterCollectionSlider
    },
    mounted () {
        //------------------------------------- Custom JS Code START Here
        var pathname = window.location.pathname;
        if(pathname === '/collection'){
            $('#app').css('overflow-x','clip');
            $('#viewport').css('overflow-x','clip');
        }
        else if(pathname === '/Collection'){
            $('#app').css('overflow-x','clip');
            $('#viewport').css('overflow-x','clip');
        }
        else if(pathname != '/collection'){ 
            $('#app').css('overflow-x','hidden');
            $('#viewport').css('overflow-x','hidden');
        }
        const items = $('.bg_sec');
        let currentItemIndex = 0;
        // Function to remove the active class from all items
        function removeActiveClass() {
            items.removeClass('active');
        }
        // Function to add the active class to the current item
        function setActiveClass() {
            items.eq(currentItemIndex).addClass('active');
        }
        // Initial set active class
        setActiveClass();
        // Mouse wheel scroll event listener
        $('.dv3_inner').on('mousewheel', function (e) {
            // Check if the user scrolled up or down
            if (e.originalEvent.deltaY > 0) {
                // Scrolled down
                console.log('going down');
                if (currentItemIndex < items.length - 1) {
                    currentItemIndex++;
                    removeActiveClass();
                    setActiveClass();
                }
            } else {
                // Scrolled up
                if (currentItemIndex > 0) {
                    currentItemIndex--;
                    removeActiveClass();
                    setActiveClass();
                }
            }
        });
        $('#audio-control').click(function () {
            if ($("#banner_video").prop('muted')) {
                $("#banner_video").prop('muted', false);
                $('.mute_icon').show();
                $('.unmute_icon').hide();
            } else {
                $("#banner_video").prop('muted', true);
                $('.mute_icon').hide();
                $('.unmute_icon').show();
            }
        });
        const videoElement = document.querySelector('#banner_video');
        const playPauseButton = document.querySelector('.video-control');
        playPauseButton.addEventListener('click', () => {
            playPauseButton.classList.toggle('playing');
            if (playPauseButton.classList.contains('playing')) {
                videoElement.pause();
            }
            else {
                videoElement.play();
            }
        });
        videoElement.addEventListener('ended', () => {
            playPauseButton.classList.remove('playing');
        });
        window.addEventListener('load', videoScroll);
        window.addEventListener('scroll', videoScroll);
        function videoScroll() {
            var videoElements = document.querySelectorAll('#banner_video[autoplay]');
            if (videoElements.length > 0) {
                var windowHeight = window.innerHeight;
                videoElements.forEach(function (thisVideoEl) {
                    var videoElement = thisVideoEl;
                    var videoHeight = videoElement.clientHeight;
                    var videoClientRect = videoElement.getBoundingClientRect().top;
                    if (videoClientRect <= (windowHeight - videoHeight * 0.10) && videoClientRect >= -videoHeight * 0.10) {
                        videoElement.play();
                    } else {
                        videoElement.pause();
                    }
                });
            }
        }
        //------------------------------------- Custom JS Code END Here
    },
    methods: {
    openFullScreenVideo() {
        const videoElement = document.getElementById("banner_video");
        if (videoElement) {
            if (videoElement.requestFullscreen) {
                videoElement.requestFullscreen();
            }
        }
    },
},
};
</script>
<style scoped>
.mute_icon {
    display: none;
}
.video-container {
    position: relative;
    width: 100%;
    height: 100%;
}
.video-abs {
    width: 100%;
    height: 100%;
    object-fit: cover;
}
img.play-img {
    width: 50px;
    position: absolute;
    bottom: 4px;
    left: 0px;
    cursor: pointer;
}
img.pause-img {
    width: 50px;
    position: absolute;
    bottom: 4px;
    left: 0px;
    cursor: pointer;
}
button.video-control {
    border: 0;
    background-color: #0000;
}
.video-control.show {
    display: block;
}
img.mute_icon {
    position: absolute;
    right: 25px;
    width: 24px;
    bottom: 15px;
    cursor: pointer;
}
img.unmute_icon {
    position: absolute;
    right: 25px;
    width: 24px;
    bottom: 15px;
    cursor: pointer;
}
.video-control:not(.playing) .video-control-play, .video-control.playing .video-control-pause {
    display: none;
}
.parallax-section .parallax-content {
    -webkit-box-align: center;
    -moz-box-align: center;
    -o-box-align: center;
    -ms-flex-align: center;
    -webkit-align-items: center;
    align-items: center;
    color: #fff;
    font-size: 2rem;
    letter-spacing: 0.1em;
    -webkit-box-pack: center;
    -moz-box-pack: center;
    -o-box-pack: center;
    -ms-flex-pack: center;
    -webkit-justify-content: center;
    justify-content: center;
    height: 100%;
    position: relative;
    z-index: 2;
}
.head-text {
    position: absolute !important;
    bottom: 30px;
    left: 40%;
}
h2.text-hd {
    margin-left: 6px;
}
.section_btn {
    background-color: rgba(25, 17, 11, .2);
    border-color: #fff;
    border: 1px solid #FFF;
    backdrop-filter: blur(2px);
    color: #FFF;
    font-weight: 400;
    padding: 16px 22px;
    width: -moz-fit-content;
    width: fit-content;
    font-size: 15px;
    text-transform: uppercase;
    letter-spacing: 1px;
    display: block;
    margin: auto;
    margin-top: 22px;
    position: relative;
    overflow: hidden;
    width: 100%;
    max-width: 8rem;
    cursor: pointer;
    margin-left: 35px;
}
.section_btn:hover {
    background: #00000029;
    color: #FFF;
    border: 1px solid #FFF;
    cursor: pointer;
}
.section_btn div {
    width: 100%;
    float: left;
    display: flex;
    align-items: center;
    position: relative;
}
.section_btn div p {
    margin: 0;
    margin-left: 7px;
    transition: all 0.4s;
}
.parallax-section {
    height: 90vh;
    overflow: visible;
    position: relative;
}
.parallax-image {
    position: relative;
}
.video-container {
    position: relative;
    width: 100%;
    height: 100%;
}
video {
    width: 100%;
    /* Ensure the video takes the full width of its container */
    height: 100%;
    /* Ensure the video takes the full height of its container */
    object-fit: cover;
    /* Maintain aspect ratio and cover the entire container */
}
.parallax-section::before {
    content: '';
    position: absolute;
    top: 1px;
    left: 0;
    width: 100%;
    height: 100%;
    z-index: 2;
    transition: opacity .3s cubic-bezier(.39, .575, .565, 1);
}
.parallax-section .parallax-image {
    background-repeat: no-repeat;
    -webkit-background-size: cover;
    -moz-background-size: cover;
    background-size: cover;
    height: 100%;
    left: 0;
    opacity: 1.5;
    -ms-filter: "progid:DXImageTransform.Microsoft.Alpha(Opacity=50)";
    filter: alpha(opacity=50);
    position: absolute;
    top: 0;
    -webkit-transform: translateZ(0);
    -moz-transform: translateZ(0);
    -o-transform: translateZ(0);
    -ms-transform: translateZ(0);
    transform: translateZ(0);
    width: 100%;
    z-index: 1;
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
    background-image: url('/assets/icons/chevron-1.svg');
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
.description-container {
    padding: 9.2% 0 9.2%;
    background-color: #000;
}
p.dscrpt-txt {
    color: #FFF;
    text-align: center;
    font-size: 24px;
    line-height: 34px;
    font-weight: 300;
}
.top-img{
    width: 100%;
    height: 100%;
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
    .head-text{
       left: 35%;
    }
    p.dscrpt-txt{
    font-size: 14px;
    line-height: 25px;
    padding: 38px;
}
}
@media only screen and (min-device-width: 320px) and (max-device-width: 767px) {
    .head-text{
        left: 20%;
    }
    p.dscrpt-txt{
    font-size: 14px;
    line-height: 17px;
    padding: 50px;
    }
.head-img-cl {
    left: 6%;
    bottom: 80px;
    width: 381px;
    }
    h2.text-hd{
    margin-left: 16px;
    font-size: 35px;
}
}
</style>