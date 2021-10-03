
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
    <v-tabs v-model="tab" right color="#363636" class="topNavvy">
      <a class="logo" href="/"
        ><span class="logoType">THE VOTER'S COMPANION</span
        ><img class="flagLogo" src="../static/flagLogo.svg"
      /></a>
      <v-spacer></v-spacer>
      <v-tabs-slider color="rgba(0, 0, 0, 0.54)"></v-tabs-slider>

      <v-tab v-for="item in items" :key="item">
        {{ item }}
      </v-tab>
    </v-tabs>
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
      <a
        href="https://www.sos.mo.gov/elections/goVoteMissouri/register"
        target="_blank"
        class="registerBadge"
        ><img src="registerBadge.png"
      /></a>
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
.flagLogo {
  height: 55%;
  top: 50%;
  left: 2px;
  transform: translateY(-50%);
  position: absolute;
  display: none;
}
.alertsBox {
  position: absolute;
  width: 100%;
  right: -50vw;
  transform: translateX(-15px);
  bottom: 5px;
  height: 100%;
  z-index: 999;
}
.logoType {
  font-family: 'Oswald', sans-serif;
}
.v-alert {
  box-shadow: 0 1px 1px rgba(0, 0, 0, 0.04), 0 2px 2px rgba(0, 0, 0, 0.05),
    0 4px 4px rgba(0, 0, 0, 0.06), 0 8px 8px rgba(0, 0, 0, 0.07),
    0 16px 16px rgba(0, 0, 0, 0.08), 0 32px 32px rgba(0, 0, 0, 0.09) !important;
}
.alert {
  width: 50%;
  position: sticky;
  bottom: 0px;
}
.registerBadge {
  position: absolute;
  top: 54%;
  transform: translateY(-50%);

  right: 12rem;
  z-index: 778;
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
  right: 2.2rem;
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
  color: #0077ee;
  font-size: 1.5rem;
  width: 20rem;
  text-align: left;
  line-height: 120%;
  height: 12rem;
  padding-left: 0.7em;
  font-weight: 450;
}
#overviewNoticeWrapper {
  background-color: #fcfcfc;
  background-size: cover;
  background-image: url('../static/07.png');
  font-family: 'Roboto', sans-serif;
  width: 100%;
  padding-left: 2rem;
  padding-top: 2.2rem;
  padding-bottom: 1rem;
  position: relative;
  margin-bottom: 0em;
  overflow: hidden;
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

@media screen and (max-width: 570px) {
  .v-tab {
    padding-right: 2px !important;
    padding-left: 2px !important;
  }
  .v-tabs {
    margin-right: 5px !important;
  }
}
@media only screen and (max-width: 750px) {
  .alertsBox {
    right: 0px;
    transform: translateX(0px);
  }
  .timelineContainer {
    margin-left: -0.5rem;
  }
  .alert {
    width: 95%;
    margin-right: auto;
    margin-left: auto;
    margin-top: 20px;
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
    margin-bottom: 10px;
  }
}
@media only screen and (max-width: 450px) {
  #overviewNoticeWrapper {
    padding-top: 1rem;
    padding-left: 1.4rem;
  }
  #overviewNotice {
    font-size: 1.4rem;
    width: 70%;
  }
  footer {
    margin-bottom: 5px;
  }
}
@media only screen and (max-width: 375px) {
  footer {
    width: 95%;
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
@media only screen and (max-width: 500px) {
  .logoType {
    display: none;
  }
  .flagLogo {
    display: inline;
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
@media only screen and (max-width: 470px) {
  a.logo {
    font-weight: 550;
    font-size: 1.5rem;
    left: 0.6rem;
    line-height: 2rem;
  }
  a.logo .THE {
    font-size: 0.7rem;
    vertical-align: super;
  }
}
</style>
