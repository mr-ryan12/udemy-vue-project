<template>
  <section class="main-app">
    <Header/>
    <ResourcesMenu/>
    <Resources :resources="resources"/>
  </section>
</template>

<script>
import Header from './components/Header'
import ResourcesMenu from './components/ResourcesMenu.vue'
import Resources from './components/Resources.vue'

export default {
  components: {
    Header,
    ResourcesMenu,
    Resources
  },
  data() {
    return {
      resources: [
        {
          id: 1,
          title: 'Official Vue Guide',
          description: 'The official Vue.js documentation',
          link: 'https://vuejs.org/'
        },
        {
          id: 2,
          title: 'Google',
          description: 'Learn to google...',
          link: 'https://google.org/'
        }
      ]
    }
  }
}
</script>

<style>
* {
  margin: 0;
}

#app {
  font-family: 'Roboto', sans-serif;
}

.main-app {
  display: flex;
  flex-direction: column;
  align-items: center;
  height: 100vh;
  width: 100vw;
}
</style>