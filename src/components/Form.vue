<template>
  <form>
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
        type="text"
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
export default {
  data() {
    return {
      isTitleSelected: false,
      isDescriptionSelected: false,
      isLinkSelected: false,
      title: '',
      description: '',
      link: ''
    }
  },
  methods: {
    toggleSelection(isTitle, isDescription, isLink) {
      this.isTitleSelected = isTitle
      this.isDescriptionSelected = isDescription
      this.isLinkSelected = isLink
    }
  }
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