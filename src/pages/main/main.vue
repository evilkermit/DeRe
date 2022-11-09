<template>
  <div id="container">
    <!--<u-i-bar/>!-->
    <loom-u-i>
      <loom-manager 
        :directory=directory
        :modifier_directory=modifier_directory 
      />
    </loom-u-i>
    
  </div>
</template>

<script>
// import UIBar from './components/UIBar/UIBar.vue'
import loomManager from './components/loom/loomManager.vue'
import loomUI from './components/loom/loomUI.vue'

export default {
  name: 'MainPage',
  beforeCreate: () => {
    document.body.className = 'viewer';
  },
  components: {
    // UIBar,
    loomManager,
    loomUI,
  },
  data: function(){
    const modifier_directory = 'https://raw.githubusercontent.com/branson2015/DeRe_Apps/main/demos/demos';
    // const baseURL = 'https://raw.githubusercontent.com/branson2015/DeRe_Apps/main/RVA';
    const baseURL = `//${window.location.hostname}:5577/rva`;
    
    return {
      directory: baseURL,
      modifier_directory,
    };
  },
}
</script>

<style>
body.viewer, body.viewer #app {
  height: 100vh;
  width: 100vw;
  margin: 0px;
}

body.viewer {
  overflow: hidden;
}

#container {
  height: 100%;
}
</style>
