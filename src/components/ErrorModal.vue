<template>
  <section class="modal-container">
    <section class="modal">
      <h2 class="modal-header">Invalid Entry</h2>
      <p>Unfortunately, at least one input value is invalid.</p>
      <p>
        Please check all inputs and make sure you enter at least a few characters into each input field
      </p>
      <button @click="$emit('close-modal')">Okay</button>
    </section>
  </section>
</template>

<script>
export default {
  props: {
    closeModal: Function
  }
}
</script>

<style scoped>
.modal-container {
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  overflow: auto;
  background-color: rgba(0, 0, 0, 0.5);
  display:flex;
  justify-content: center;
  align-items: center;
}

.modal {
  position: relative;
  display: block;
  height: 40%;
  width: 35%;
  background-color: #FFF;
  /* line-height: 131px; */
  font-size: 16px;
  border-radius: 20px;
}

.modal-header {
  padding: 20px;
  display: flex;
  align-items: center;
  background-color: #3a0061;
  color: #FFF;
  text-align: left;
  height: 5vh;
  border-top-left-radius: 20px;
  border-top-right-radius: 20px;
}

p {
  padding: 20px;
}

button {
  position: absolute;
  right: 1vw;
  bottom: 1vh;
  height: 4vh;
  width: 7vw;
  background-color: #3a0061;
  color: #FFF;
  font-size: 16px;
  border-radius: 10px;
}

</style>