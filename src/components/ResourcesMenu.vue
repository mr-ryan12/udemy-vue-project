<template>
  <section class="resources-container">
    <section class="button-container">
      <button :class="toggleStoredButtonStyling" @click="toggleSelection(true, false, 'Resources')">Stored Resources</button>
      <button :class="toggleAddButtonStyling" @click="toggleSelection(false, true, 'Form')">Add Resources</button>
    </section>
  </section>
</template>

<script>
  export default {
    props: {
      toggleButtonSelection: Function,
      storedButtonSelected: Boolean,
      addButtonSelected: Boolean
    },
    methods: {
      toggleSelection(isStoredButtonActive, isAddButtonActive, component) {
        this.$emit('toggle-button-selection', isStoredButtonActive, isAddButtonActive, component)
      }
    },
    computed: {
      toggleStoredButtonStyling() {
        return this.storedButtonSelected ? 'selected' : 'not-selected'
      },
      toggleAddButtonStyling() {
        return this.addButtonSelected ? 'selected' : 'not-selected'
      }
    },
    inject: ['toggleComponent']
  }
</script>

<style scoped>
.resources-container {
  margin-top: 5vh;
  width: 40%;
  height: 5vh;
  padding: 10px;
  border-radius: 10px;
  border: none;
  box-shadow: 0.5px 1px 5px 1px grey;
  display: flex;
  align-items: center;
}

button {
  margin: 5px;
  padding: 10px;
  background: none;
  border: none;
  cursor: pointer;
}

.selected {
  background-color: #3a0061;
  color: white;
}

.not-selected:hover {
  background-color: rgba(58, 0, 97, 0.25)
}
</style>