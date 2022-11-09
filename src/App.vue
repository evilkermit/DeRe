<template>
  <router-view />
</template>

<script>
// Check out https://github.com/vuejs/rfcs/blob/script-setup-2/active-rfcs/0000-script-setup.md
import MainPage from './pages/main/main.vue';

export default {
  components: {
    MainPage,
  },
  created(){
    window.addEventListener('mousemove', e => {
      document.body.style.cursor = 'default';
      this.emitter.emit('mousemove', e);
    });
    window.addEventListener('mouseup', e => {
      document.body.style.cursor = 'default';
      this.emitter.emit('mouseup', e);
    });
    window.addEventListener("mousedown", e => {
      this.emitter.emit('mousedown', e);
    });
  }
};

</script>

<style>
* {
  box-sizing: border-box;
}

html {
  margin: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
</style>
