<template>
  <div class="myName">
    <p class="title-name">Nizam Özdemir</p>
    <p class="title-desc">Bsc Informatik Fokus Digital Ideation</p>
    <div class="navigation">
      <a class="title-txt" id="title-txt-right" @click="scrollToProjects('first-video')">Zu den Projekten</a>
      <nuxt-link to="/about" class="title-txt" id="title-txt-left">Über mich</nuxt-link>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    scrollToProjects(target) {
      const element = document.getElementById(target);
      const isMobile = window.innerWidth <= 600;
      const mobileOffset = window.innerHeight / 2 - element.clientHeight / 2;
      const desktopOffset = (window.innerHeight / 2 - element.clientHeight / 2) - 180;
      const offset = isMobile ? mobileOffset : desktopOffset; 
      const bodyRect = document.body.getBoundingClientRect().top;
      const elementRect = element.getBoundingClientRect().top;
      const elementPosition = elementRect - bodyRect;
      const offsetPosition = elementPosition - offset;

      window.scrollTo({
        top: offsetPosition,
        behavior: 'smooth'
      });
    }
  },
}
</script>

<style>
*{
  font-family: sans-serif;
}

.myName{
  height: 100vh;
  text-align: center;
}

.title-name{
  font-size: 120px;
  font-weight: bold;
  margin-top: 10%;
}

.title-desc{
  font-size: 40px;
  font-weight: bold;
}

.navigation{
  display: flex;
  justify-content: center;
  margin-top: 7%;
}

.title-txt {
  font-size: 25px;
  margin: 0 10px;
  text-decoration: none; 
  color: inherit;
  color: rgb(252, 117, 68);
  position: relative;
  overflow: hidden;
  padding: 10px 10px;
  display: inline-block;
  cursor: pointer;
  width: 20%;
  transition: border 0.3s ease-in-out;
}

.title-txt:hover {
  outline: 2px solid rgb(252, 117, 68);
}

.title-txt::before {
  content: "";
  position: absolute;
  width: 0;
  height: 2px;
  bottom: 0;
  left: 0;
  background-color: rgb(252, 117, 68);
  visibility: hidden;
  transition: all 0.3s ease-in-out;
}

.title-txt::after {
  content: "";
  position: absolute;
  width: 2px;
  height: 0;
  right: 0;
  bottom: 0;
  background-color: rgb(252, 117, 68);
  visibility: hidden;
  transition: all 0.3s ease-in-out;
}

.title-txt:hover::before {
  width: 100%;
  visibility: visible;
}

.title-txt:hover::after {
  height: 100%;
  visibility: visible;
}

@media (min-width: 1024px) and (max-height: 1080px) and (max-width: 1920px){
  .title-txt {
    font-size: 20px;
  }
}

@media only screen and (max-width: 1024px) {
  .title-name{
    font-size: 80px;
    margin: 5% 0;
    margin-top: 2em;
  }

  .navigation{
    margin-top: 30em;
  }

  .title-desc{
    font-size: 40px;
    margin: 2.5% 0;
  }

  .title-txt {
    font-size: 25px;
    font-family: sans-serif;
    margin: 0 10px;
    text-decoration: none; 
    color: inherit;
    color: rgb(252, 117, 68);
    position: relative;
    overflow: hidden;
    padding: 10px 10px;
    display: inline-block;
    cursor: pointer;
    width: 40%;
    transition: border 0.3s ease-in-out;
  }
}

@media only screen and (max-width: 600px) {
  .title-name{
    font-size: 60px;
    margin: 5% 0;
  }

  .title-desc{
    font-size: 30px;
    margin: 2.5% 0;
  }
  .title-txt {
    font-size: 17px;
  }

  .navigation{
    display: flex;
    margin-top: 8em;
  }

  .myName{
    height: 100vh;
    text-align: left;
  }
}
</style>
