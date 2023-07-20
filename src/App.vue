<template>
  <div style="heigth: 100%">
    <my-header :isMenuHide="isMenuHide" :isProfileHide="isProfileHide" @update-parent-profile="updateParentValueProfile"
               @update-parent="updateParentValue"></my-header>
    <div style="display: flex">
      <my-menu :isMenuHide="isMenuHide" :isHome="isHome" :isProfileHide="isProfileHide"
               @update-parent-profile="updateParentValueProfile" @update-home="updateHomeValue"
               @update-parent="updateParentValue"></my-menu>
      <div style="width: 100%; margin-top: 15px">
        <router-view></router-view>
        <div>
          <div style="padding: 0;"
               :class="[{'activeMenuHide': isMenuHide || isProfileHide}, {'activeNoMenuHide': !isMenuHide || !isProfileHide}, {'displayNone': isHome}]">

            <div id="content" style="margin: 0px 15px;">
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import MyHeader from './components/header/header.js';
import MyMenu from './components/menu/menu.js';
import MyHome from './components/home/home.js';
import Breadcrumbs from './components/loader/loader.js';

export default {
  name: 'App',
  components: {
    'my-header': MyHeader,
    'my-home': MyHome,
    'my-menu': MyMenu,
    'breadcrumbs': Breadcrumbs,
  },
  data() {
    return {
      isHome: window.location.hash == "#/home1",
      isMenuHide: false,
      isProfileHide: true,
    };
  },
  methods: {
    updateParentValue(newValue) {
      console.log(this.isMenuHide)
      this.isMenuHide = newValue;
    },
    updateParentValueProfile(newValue) {
      console.log(this.isMenuHide)
      this.isProfileHide = newValue;
    }, updateHomeValue(newValue) {
      this.isHome = newValue;
    },
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
