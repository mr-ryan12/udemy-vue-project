<template>
  <form>
    <div>
      <label for="title" class="title-label">Title</label>
      <input 
        type="text"
        id="title"
        v-model="title"
        placeholder="Title"
      />
    </div>
    <div>      
      <label for="description">Description</label>
      <textarea 
        type="text"
        id="description"
        v-model="description"
        placeholder="Description"
      />
    </div>
    <div>
      <label for="link">Link</label>
      <input 
        type="text"
        id="link"
        v-model="link"
        placeholder="Link"
      />
    </div>
    <button>Add Resource</button>
  </form>
</template>

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
}
</style>