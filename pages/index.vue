<template>
 <Landing />
</template>
<style>
@import url('https://fonts.googleapis.com/css2?family=Oswald:wght@400;500;600&family=Roboto:ital,wght@0,300;0,400;0,500;0,700;1,300;1,400;1,500&display=swap');

.v-tabs__div {
  cursor: pointer;
}
#bigButton {
  position: absolute;
  right: 1rem;
  z-index: 888;
  top: 6.7em;
  /* first drop shadow handles the v light shadow and the second handles the sharper shadow drop-shadow(1px 14px 6px rgba(15, 13, 2, 0.07)) */
  filter: drop-shadow(1px 5px 3px rgba(15, 13, 2, 0.2)) drop-shadow(0px -5px 5px rgb(173, 39, 15, .2));
  -webkit-filter: drop-shadow(1px 5px 3px rgba(15, 13, 2, 0.2)) drop-shadow(0px -5px 5px rgb(173, 39, 15, .2));
}
/* #bigButton:hover {
  filter: drop-shadow(1px 14px 14px rgba(15, 13, 2, 0.2)) drop-shadow(1px 8px 10px rgba(15, 13, 2, 0.25));
  -webkit-filter: drop-shadow(1px 14px 14px rgba(15, 13, 2, 0.2)) drop-shadow(1px 8px 10px rgba(15, 13, 2, 0.25));
} */
footer {
  /* position: absolute; */
  background-color: rgb(222, 222, 222);
  height: 15em;
  width: 97%;
  bottom: 10px;
  color: #3e3830;
  margin: 0 auto;
  padding: 16px;
  border-radius: 3px;
  display: block;
  margin-bottom: 5.5px;
}
#logoLink {
  z-index: 777;
  position: relative;
  top: .3em;
  float: right;
  filter: drop-shadow(0 2px 3px rgba(60, 63, 76, 0.46));
	-webkit-filter: drop-shadow(0 2px 3px rgba(60, 63, 76, 0.46));
  /* -webkit-filter: drop-shadow(4px 4px 0 #A57F70);
    filter:drop-shadow(4px 4px 0 #A57F70)*/
}
html {
  background: rgb(243, 241, 240) url( "../static/stripes.svg" ) no-repeat center center fixed;
  min-height: 100vh;
  box-sizing: border-box;
  background-size: cover;
  /* box-shadow: 0 0 10px inset */
}
*, *:before, *:after {
  box-sizing: inherit;
}

.v-tabs {
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
}
#app {
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  width: 46rem;
  margin: auto;
  margin-top: 1.5em;
  margin-bottom: 1.5em;
  text-align: center;
  box-shadow: 0 1px 1px rgba(141, 118, 111, 0.13), 
              0 2px 2px rgba(141, 118, 111,0.14), 
              0 4px 4px rgba(141, 118, 111,0.15), 
              0 8px 8px rgba(141, 118, 111,0.16);
  border-bottom: 2px solid rgba(0, 0, 0, 0.008);
  position: relative;
  border-radius: 3px;
}
#overviewMarquee {
  font-size: 200%;
  color: #5b524a;
  font-family: 'Roboto', sans-serif;
  text-align: left;
  margin-bottom: .5em;
  text-shadow: 0px 2px 4px rgba(0,0,0,0.2);
  font-weight: 500;
  letter-spacing: .08em;
  padding-left: .4em;
}

a:hover {
  text-decoration: none !important;
}

body {
  margin: 0;
  padding: 0;
  /* 👇 the color behind the 'page' element */
  min-height: 100vh;
  display: block;
}

a {
  text-decoration: none !important;
}
a:visited {
  color: #5b524a !important;
  text-decoration: none !important;
}

h1 {
  font-size: 34px;
  line-height: 40px;
  margin: 0;
  padding: 0;
}

h2 {
  font-size: 25px;
}

input, input:focus {
  border: none;
  outline: none;
}
#takeMeOmh:visited, #takeMeOmhDaddy:visited {
  color: #5b524a !important;
}
#e9_texte {
  font-size: 1.5rem;
  font-family: 'Karla', sans-serif;
}
/* loading modal below this line ================================= */
/* The modal-loader below created by Alex Rutherford >>> https://codepen.io/Ruddy/pen/RNRybN */
.v--modal {
  border-radius: 100% !important;
  box-sizing: none !important;
  position: relative;
}
.image {
  width: 100px;
  height: 160px;
  font-size: 40px;
  text-align: center;
  transform-origin: bottom center;
  animation: 3s rotate infinite !important;
  opacity: 0;
  color: blue;
  top: 2.1rem;
  left: 3.2rem;
  position: relative;
}
.v--modal-box span {
  color: white;
  display: block;
  font-size: 115%;
  width: 100%;
  text-align: center;
  position: absolute !important;
  z-index: 778;
  bottom: 50px;
}
@media screen and (min-width: 376px) and (max-width: 432px) {
  footer {
    bottom: 8px !important;
  }
}
@media screen and (min-width: 432px) and (max-width: 750px) {
  footer {
    margin-bottom: 2.5px !important;
  }
}
@media only screen and (max-width: 750px) {
  #app {
    width: 100vw;
    min-height: 100vh !important;
    margin-bottom: 0px !important;
    margin-top: 0px;
    box-shadow: 0 0 0 0 rgba(0,0,0, .0);
    border-radius: 0px;
  }
  #overviewNoticeWrapper {
    height: 225px;
  }
  #overviewMarquee {
    font-size: 250%;
    margin-bottom: .3em;
  }
  #overviewNotice {
    padding-right: 3em;
    padding-left: .2em;
  }
  footer {
    width: 95%;
    margin: 0 auto;
    position: relative;
  }
}
@media only screen and (max-width: 380px) {
  html, body {
    background: rgb(253, 253, 253) !important;
    min-height: 100vh;
  }
}
@media only screen and (max-width: 375px) {
  footer {
    width: 95%;
    margin-bottom: 8px;
  }
  #logoLink {
    top: .7em;
  }
  #overviewNoticeWrapper {
    height: 175px;
  }
}
</style>
