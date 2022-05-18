<template>
  <section class="main-app">
    <Header />
    <ResourcesMenu @toggle-button-selection="toggleButtonSelection" :stored-button-selected="storedButtonSelected" :add-button-selected="addButtonSelected"/>
    <component :is="selectedComponent"></component>
  </section>
</template>

<script>
import Header from './components/Header'
import ResourcesMenu from './components/ResourcesMenu.vue'
import Resources from './components/Resources.vue'
import Form from './components/Form.vue'

export default {
  components: {
    Header,
    ResourcesMenu,
    Resources,
    Form
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
      ],
      selectedComponent: 'Resources',
      storedButtonSelected: true,
      addButtonSelected: false
    }
  },
  methods: {
    toggleComponent(component) {
      this.selectedComponent = component
    },
    addResource(resource) {
      this.resources.unshift(resource)
    },
    toggleButtonSelection(isStoredButtonActive, isAddButtonActive, component) {
      this.storedButtonSelected = isStoredButtonActive
      this.addButtonSelected = isAddButtonActive
      this.toggleComponent(component)
    },
    deleteResource(id) {
      const foundIndex = this.resources.findIndex(resource => resource.id === id)
      this.resources.splice(foundIndex, 1)
    }
  },
  provide() {
    return {
      resources: this.resources,
      addResource: this.addResource,
      toggleComponent: this.toggleComponent,
      resetButtonSelection: this.toggleButtonSelection,
      deleteResource: this.deleteResource
    }
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@400;700&display=swap');

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

button {
  cursor: pointer;
}
</style>