<template>
  <ErrorModal v-if="error" @close-modal="closeModal" />
  <form @submit.prevent="handleSubmit">
    <div>
      <label for="title" class="title-label">Title</label>
      <input 
        type="text"
        id="title"
        v-model="title"
        :class="isTitleSelected && 'selected'"
        @click="toggleSelection(true, false, false)"
        @focus="toggleSelection(true, false, false)"
        @blur="toggleSelection(false, false, false)"
        ref="title"
      />
    </div>
    <div>      
      <label for="description">Description</label>
      <textarea 
        type="text"
        id="description"
        v-model="description"
        :class="isDescriptionSelected && 'selected'"
        @click="toggleSelection(false, true, false)"
        @focus="toggleSelection(false, true, false)"
        ref="description"
      />
    </div>
    <div>
      <label for="link">Link</label>
      <input 
        type="url"
        id="link"
        v-model="link"
        :class="isLinkSelected && 'selected'"
        @click="toggleSelection(false, false, true)"
        @focus="toggleSelection(false, false, true)"
        ref="link"
      />
    </div>
    <button @focus="toggleSelection(false, false, false)">Add Resource</button>
  </form>
</template>

<script>
import ErrorModal from './ErrorModal.vue'

export default {
  components: {
    ErrorModal
  },
  data() {
    return {
      isTitleSelected: false,
      isDescriptionSelected: false,
      isLinkSelected: false,
      title: '',
      description: '',
      link: '',
      error: false
    }
  },
  methods: {
    toggleSelection(isTitle, isDescription, isLink) {
      this.isTitleSelected = isTitle
      this.isDescriptionSelected = isDescription
      this.isLinkSelected = isLink
    },
    handleSubmit() {
      this.checkInputs()
      if (!this.error) {
        const newResource = {
          id: Date.now(),
          title: this.title,
          description: this.description,
          link: this.link
        }
        this.addResource(newResource)
        this.resetButtonSelection(true, false, 'Resources')
      }
    },
    checkInputs() {
      if (!this.title || !this.link || !this.description) {
        this.error = true
      }
    },
    closeModal() {
      this.error = false
    }
  },
  inject: ['addResource', 'toggleComponent', 'resetButtonSelection']
}
</script>

<style scoped>
form {
  display: flex;
  flex-direction: column;
  justify-content: space-around;
  margin-top: 5vh;
  padding: 10px;
  box-shadow: 0.5px 1px 5px 1px grey;
  width: 40%;
  height: auto;
  border-radius: 10px;
  font-size: 18px;
}

div {
  display: flex;
  flex-direction: column;
  width: 100%;
  margin-left: 0.5vw;
}

input,
textarea {
  width: 95%;
  margin-bottom: 2vh;
}

textarea {
  font-family: 'Roboto', sans-serif;
  height: 10vh;
  width: 95%;
}

.title-label {
  margin-top: 2vh;
}

label {
  font-weight: 900;
  margin-bottom: 0.5vh;
}

button {
  align-self: left;
  width: 20%;
  height: 4vh;
  background-color: #3a0061;
  color: #FFF;
}

button:hover {
  cursor: pointer;
}

.selected {
  background-color: rgb(225, 201, 225);
}
</style>