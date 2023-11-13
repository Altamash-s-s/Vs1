<template>
    <div id="career" class="cstm-page-layout">
        <div class="head-section">
            <img class="hd-img" src="../assets/home/hs1.png">

        </div>
        <div class="cr-head">
            <h3 class="inside-hd">Embark on a Journey of Innovation: Join HUMAN ABSTRACT</h3>
            <P class="inside-para">At HUMAN ABSTRACT, we're not just building careers; we're crafting a future. Our DNA
                thrives on audacious
                ideas, relentless collaboration, and a culture that values the
                extraordinary. If you're weary of the mundane and seek a professional adventure, you've found your tribe.
            </P>
            <h3 class="inside-hd">Why Us?</h3>
            <P class="inside-para">Picture a workplace where innovation is a daily ritual, not an exception. We celebrate
                the rebels, the
                dreamers, and those unafraid to challenge the status quo. Here, you're
                not an employee; you're a co-author of our success story.
            </P>
            <h3 class="inside-hd">Beyond the Desk</h3>
            <P class="inside-para">Work-life balance isn't a myth here—it's a commitment. Flexible schedules, remote
                possibilities, and an environment that nurtures personal growth are the pillars of HUMAN ABSTRACT's ethos.
                We don't just want you to fit into our culture; we want you to enhance it.
            </P>
            <h3 class="inside-hd">Join the Movement</h3>
            <P class="inside-para">Our team isn't just a collection of individuals; we're a force. Join us on a mission
                where your ideas matter,
                your voice resonates, and your career takes flight. This is not just a
                job; it's a passport to a future shaped by passion, innovation, and shared success. Click on APPLY NOW and
                start you success journey with us at HUMAN ABSTRACT

            </P>
        </div>
        <div class="apply-btn">
            <button>
                APPLY NOW
                <div class="arrow-wrapper">
                    <div class="arrow"></div>

                </div>
            </button>

            

        </div>
    </div>
</template>
<script>
import '../css/cstm-page-layout.css';

export default {
    name: 'career',
    components: {

    },

};
</script>

<style>
.apply-btn {
    display: flex;
    justify-content: center;
    padding: 30px 0px 30px 0px;
}
button {
  --primary-color: #444444;
  --secondary-color: #fff;
  --hover-color: #444444;
  --arrow-width: 10px;
  --arrow-stroke: 2px;
  box-sizing: border-box;
  border: 0;
  color: var(--secondary-color);
  padding: 1em 1.8em;
  background: var(--primary-color);
  display: flex;
  transition: 0.2s background;
  align-items: center;
  gap: 0.6em;
  font-weight: bold;
  font-weight: 400;
  letter-spacing: 2px;
  cursor: pointer;
}

button .arrow-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
}

button .arrow {
  margin-top: 1px;
  width: var(--arrow-width);
  background: var(--primary-color);
  height: var(--arrow-stroke);
  position: relative;
  transition: 0.2s;
}

button .arrow::before {
  content: "";
  box-sizing: border-box;
  position: absolute;
  border: solid var(--secondary-color);
  border-width: 0 var(--arrow-stroke) var(--arrow-stroke) 0;
  display: inline-block;
  top: -3px;
  right: 3px;
  transition: 0.2s;
  padding: 3px;
  transform: rotate(-45deg);
}

button:hover {
  background-color: var(--hover-color);
}

button:hover .arrow {
  background: var(--secondary-color);
}

button:hover .arrow:before {
  right: 0;
}


</style>