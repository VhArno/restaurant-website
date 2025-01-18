<script setup lang="ts">
import AppButton from '../atoms/AppButton.vue'

const model = defineModel<boolean>('isVisible')

const handleClose = () => {
  model.value = false
}

const handleSubmit = () => {}
</script>

<template>
  <dialog>
    <form>
      <div class="title">
        <h3>Maak een reservering</h3>
        <AppButton type="outlined" @click.prevent="handleClose">Close</AppButton>
      </div>

      <div>
        <label for="firstname">Voornaam</label>
        <input type="text" id="firstname" name="firstname" autocomplete="cc-given-name" />
      </div>

      <div>
        <label for="lastname">Achternaam</label>
        <input type="text" id="lastname" name="lastname" autocomplete="cc-family-name" />
      </div>

      <div>
        <label for="email">Email</label>
        <input type="text" id="email" name="email" autocomplete="email" />
      </div>

      <div>
        <label for="amount">Aantal personen</label>
        <input type="number" min="0" max="100" id="amount" name="amount" />
      </div>

      <div>
        <label for="date">Datum</label>
        <input type="date" id="date" name="date" />
      </div>

      <AppButton>Maak reservering</AppButton>
    </form>
  </dialog>
</template>

<style lang="css" scoped>
dialog {
  position: fixed;
  top: 0;
  left: 0;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgba(0, 0, 0, 0.5); /* Semi-transparent backdrop */
  border: none; /* Remove default border */
  z-index: 1000;
}

dialog::backdrop {
  background: rgba(0, 0, 0, 0.5); /* Ensure backdrop is semi-transparent */
}

form {
  background-color: #fff;
  padding: 2rem;
  border-radius: 10px;
  box-shadow: 0px 4px 20px rgba(0, 0, 0, 0.2); /* Soft shadow for depth */
  width: 90%;
  max-width: 500px;
  display: flex;
  flex-direction: column;
  gap: 1.5rem;
}

.title {
  display: flex;
  flex-flow: row;
  justify-content: space-between;
  align-items: center;

  button {
    color: black;

    &:hover {
      color: white;
    }
  }
}

h3 {
  font-size: 1.5rem;
  margin: 0;
  color: #333; /* Dark text color */
  text-align: center;
}

div {
  display: flex;
  flex-direction: column;
  gap: 0.5rem;
}

label {
  font-size: 1rem;
  color: #555;
}

input {
  padding: 0.8rem;
  border: 1px solid #ddd;
  border-radius: 5px;
  font-size: 1rem;
  outline: none;
  transition: border-color 0.3s ease;
}

input:focus {
  border-color: #007bff; /* Highlight on focus */
}

AppButton {
  align-self: center;
  padding: 0.8rem 1.5rem;
  font-size: 1rem;
  border-radius: 5px;
  background-color: #007bff;
  color: white;
  border: none;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

AppButton:hover {
  background-color: #0056b3; /* Darker blue on hover */
}

@media (max-width: 768px) {
  form {
    width: 100%;
    padding: 1.5rem;
  }

  input {
    font-size: 0.9rem;
  }

  AppButton {
    font-size: 0.9rem;
    padding: 0.7rem 1.2rem;
  }
}
</style>
