
<template>
  <div>
    <div class="alertsBox" v-show="alert || balert">
      <v-alert
        type="warning"
        prominent
        border="left"
        colored-border
        class="alert alert--unsupported"
        dismissible
        icon="mdi-api-off"
        v-model="alert"
      >
        The Voter's Companion is currently unsupported and is displaying
        information for an example voter.
      </v-alert>
      <v-alert
        border="left"
        colored-border
        color="blue darken-1"
        class="alert alert--unsupported"
        dismissible
        prominent
        icon="mdi-map-marker"
        v-model="balert"
      >
        Showing info for:
        <br />
        <strong>
          4153 Mercier St.<br />
          Kansas City, MO 64111
        </strong>
      </v-alert>
    </div>
    <v-tabs right color="#668ee4" class="topNavvy" v-model="tab">
      <a class="logo" href="/"
        ><span>THE</span> V<span>OTER'S</span> C<span>OMPANION</span></a
      >
      <v-spacer></v-spacer>
      <v-tabs-slider color="blue"></v-tabs-slider>

      <v-tab v-for="item in items" :key="item">
        {{ item }}
      </v-tab>
    </v-tabs>
    <a
      href="https://www.sos.mo.gov/elections/goVoteMissouri/register"
      target="_blank"
      class="registerBadge"
      ><img src="registerBadge.png"
    /></a>

    <v-tabs-items v-model="tab">
      <v-tab-item :key="i">
        <Timeline />
      </v-tab-item>
      <v-tab-item :key="ii">
        <Resources />
      </v-tab-item>
      <v-tab-item :key="iii">
        <Officials />
      </v-tab-item>
    </v-tabs-items>

    <footer>
      <a id="logoLink" href="https://www.usvotefoundation.org/" target="_blank">
        <img src="voteFoundationBadge.png" />
      </a>
    </footer>
  </div>
</template>

<script>
export default {
  name: 'TopNav',
  data() {
    return {
      seen: true,
      alert: true,
      balert: true,
      tab: null,
      text: 'Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut aliquip ex ea commodo consequat.',
      i: 'Timeline',
      ii: 'Resources',
      iii: 'Officials',
      items: ['Timeline', 'Resources', 'Officials'],
    }
  },
}
</script>

<style>
.alertsBox {
  position: absolute;
  width: 100%;
  right: -50vw;
  transform: translateX(-15px);
  bottom: 5px;
  height: 100%;
  z-index: 999;
}
.v-alert {
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.04), 0 2px 2px rgba(0, 0, 0, 0.05),
    0 4px 4px rgba(0, 0, 0, 0.06), 0 8px 8px rgba(0, 0, 0, 0.07),
    0 16px 16px rgba(0, 0, 0, 0.08), 0 32px 32px rgba(0, 0, 0, 0.09) !important;
}
.alert {
  transition: all 0.3s ease;
  width: 50%;
  position: sticky;
  bottom: 0px;
}
.alert--unsupported {
}
.registerBadge {
  position: absolute;
  top: 7.5rem;
  right: 1rem;
  z-index: 7;
}
.registerBadge::after {
  content: '';
  height: 150px;
  width: 150px;
  border-radius: 10000px;
  position: absolute;
  top: 20px;
  right: 10px;
  z-index: -1;
  box-shadow: 0 5px 40px rgba(0, 0, 0, 0.253);
}
.registerBadge::before {
  content: '';
  height: 150px;
  width: 150px;
  border-radius: 10000px;
  position: absolute;
  top: 20px;
  right: 10px;
  z-index: -1;
  box-shadow: 0 5px 20px rgba(0, 0, 0, 0.397);
}
.topNavvy .v-item-group .v-slide-group__wrapper {
  background-color: #dde0e7;
}
.v-tabs__item {
  font-family: 'Roboto', sans-serif;
  color: white !important;
  letter-spacing: 0.065em;
  font-weight: 500;
}
.v-tabs__container {
  height: 55px;
}
a.logo {
  margin: 0;
  position: absolute;
  left: 0.7em;
  top: 50%;
  height: 2.5rem;
  width: auto;
  font-size: 1.3rem;
  font-weight: 500;
  line-height: 2.5rem;
  transform: translateY(-50%);
  font-family: 'Oswald', sans-serif;
  color: black;
  transition: all 0.3s ease;
}

.v-tabs__div {
  cursor: pointer;
}
#bigButton {
  position: absolute;
  right: 1rem;
  z-index: 888;
  top: 6.7em;
  /* first drop shadow handles the v light shadow and the second handles the sharper shadow drop-shadow(1px 14px 6px rgba(15, 13, 2, 0.07)) */
  filter: drop-shadow(1px 5px 3px rgba(15, 13, 2, 0.2))
    drop-shadow(0px -5px 5px rgb(173, 39, 15, 0.2));
  -webkit-filter: drop-shadow(1px 5px 3px rgba(15, 13, 2, 0.2))
    drop-shadow(0px -5px 5px rgb(173, 39, 15, 0.2));
}
footer {
  /* position: absolute; */
  background-color: rgb(222, 222, 222);
  height: 15em;
  width: 97%;
  bottom: 0px;
  color: #3e3830;
  margin: 0 auto;
  padding: 16px;
  border-radius: 3px;
  display: block;
  margin-bottom: 5.5px;
  position: relative;
}
#logoLink {
  z-index: 777;
  position: absolute;
  top: 52%;
  right: 2.5rem;
  transform: translateY(-50%);
  filter: drop-shadow(0 2px 3px rgba(60, 63, 76, 0.46));
}
html {
  /* background: linen url( "https://cl.ly/image/381U2k0A3L3S/bg.png" );
  min-height: 100vh;
  box-sizing: border-box; */
  background: rgb(243, 241, 240) url('../static/stripes.svg') no-repeat center
    center fixed;
  min-height: 100vh;
  box-sizing: border-box;
  background-size: cover;
}

*,
*:before,
*:after {
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
  margin-bottom: 2em;
  text-align: center;
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.04), 0 2px 2px rgba(0, 0, 0, 0.05),
    0 4px 4px rgba(0, 0, 0, 0.06), 0 8px 8px rgba(0, 0, 0, 0.07),
    0 16px 16px rgba(0, 0, 0, 0.08);
  min-height: 52em;
  position: relative;
  border-radius: 3px;
  padding-bottom: 4px;
  background: white;
}
#overviewNotice {
  color: #1a76d2;
  font-size: 1.5rem;
  width: 20rem;
  text-align: left;
  line-height: 120%;
  height: 12rem;
  padding-left: 0.7em;
  font-weight: 450;
}
#overviewNoticeWrapper {
  background-color: #f7f7f7;
  background-image: radial-gradient(
      circle farthest-corner at top left,
      rgba(239, 242, 243, 0.822) 0%,
      rgba(190, 205, 226, 0) 50%
    ),
    radial-gradient(
      circle farthest-side at top right,
      rgba(198, 209, 224, 0.11) 0%,
      rgba(193, 202, 176, 0) 10%
    ),
    radial-gradient(
      ellipse at bottom center,
      #1a76d21a 0%,
      rgba(229, 227, 233, 0) 80%
    );
  font-family: 'Roboto', sans-serif;
  width: 100%;
  padding-left: 2rem;
  padding-top: 2.2rem;
  padding-bottom: 1rem;
  position: relative;
  margin-bottom: 0em;
}
#overviewMarquee {
  font-size: 200%;
  font-family: 'Roboto', sans-serif;
  text-align: left;
  margin-bottom: 0.5em;
  text-shadow: 0px 2px 4px rgba(0, 0, 0, 0.2);
  font-weight: 500;
  letter-spacing: 0.08em;
  padding-left: 0.4em;
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
  color: rgb(54, 54, 54) !important;
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

input,
input:focus {
  border: none;
  outline: none;
}
#takeMeOmh:visited,
#takeMeOmhDaddy:visited {
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

/* The loader below created by Alex Rutherford >>> https://codepen.io/Ruddy/pen/RNRybN  */
@keyframes rotate {
  0% {
    transform: rotate(90deg);
  }
  10% {
    opacity: 0;
  }
  35% {
    transform: rotate(0deg);
  }
  55% {
    opacity: 1;
  }
  65% {
    transform: rotate(0deg);
    opacity: 1;
  }
  75% {
    opacity: 0;
  }

  100% {
    transform: rotate(-90deg);
  }
}

.v--modal-overlay .v--modal-box {
  overflow: visible !important;
  position: relative !important;
  background-color: #acb4c5;
  box-shadow: 0px 8px 12px rgba(58, 68, 41, 0.2),
    0px 12px 20px rgba(0, 0, 0, 0.1), 0px 0px 17px rgba(0, 0, 0, 0.14) !important;
  border-color: white;
  border-style: solid;
  border-width: 5px;
}

.v--modal-overlay {
  background-color: rgba(0, 0, 0, 0.4);
  border-radius: 0px;
  /* width: 100vw;
  height: 100vh; */
  border-style: none;
}
.scale-enter-active,
.scale-leave-active {
  /* transition: all 0.5s; */
}
.scale-enter,
.scale-leave-active {
  opacity: 0;
  /* transform: scale(0.3) translateY(24px); */
}
@media screen and (max-width: 570px) {
  .v-tab {
    padding-right: 2px;
    padding-left: 2px;
  }
  .v-tabs {
    margin-right: 5px !important;
  }
  .v-slide-group__content {
    margin-right: 8px;
  }
}
@media screen and (min-width: 376px) and (max-width: 432px) {
  footer {
    bottom: 8px !important;
  }
}
@media screen and (min-width: 432px) and (max-width: 750px) {
  footer {
    margin-bottom: 8px !important;
  }
}
@media only screen and (max-width: 750px) {
  .registerBadge {
    position: absolute;
    top: 7rem;
    right: 1rem;
    z-index: 7;
  }
  a.registerBadge img {
    height: 160px !important;
    width: 160px;
  }
  .registerBadge::after {
    height: 115px;
    width: 115px;
  }
  .registerBadge::before {
    height: 115px;
    width: 115px;
  }
  #app {
    width: 100vw;
    min-height: 100vh !important;
    margin-bottom: 0px !important;
    margin-top: 0px;
    box-shadow: 0 0 0 0 rgba(0, 0, 0, 0);
    border-radius: 0px;
  }
  #overviewNoticeWrapper {
    height: 225px;
  }
  #overviewMarquee {
    font-size: 250%;
    margin-bottom: 0.3em;
  }
  #overviewNotice {
    padding-right: 3em;
    padding-left: 0.2em;
  }
  footer {
    width: 95%;
    margin: 0 auto;
    position: relative;
  }
}
@media only screen and (max-width: 380px) {
  html,
  body {
    /* background: rgb(253, 253, 253) !important;
    min-height: 100vh; */
  }
}
@media only screen and (max-width: 375px) {
  footer {
    width: 95%;
    margin-bottom: 8px;
  }
  #logoLink {
    top: 0.7em;
  }
  #overviewNoticeWrapper {
    height: 175px;
  }
}
@media only screen and (max-width: 750px) {
  .v-tabs {
    border-top-left-radius: 0px;
    border-top-right-radius: 0px;
  }
}
@media only screen and (max-width: 330px) {
  .v-tabs__item {
    font-size: 0.9em;
  }
}
@media only screen and (max-width: 700px) {
  .v-tabs__item {
    padding: 6px 6px !important;
  }
  .v-tabs__div {
    margin-right: 0px !important;
  }
}
</style>
