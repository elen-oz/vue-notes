<script setup>
import {ref} from "vue";

const isModalShown = ref(false);
const newNote = ref('')
const notes = ref([])

const addNote = () => {
  notes.value.push({
    text:newNote,
    date: new Date(),
  })
}
</script>

<template>
  <main>
    <div v-if="isModalShown" class="overlay">
      <div class="modal">
        <textarea v-model="newNote" name="note" id="note" cols="30" rows="10"></textarea>
        <button>Add Note</button>
        <button class="close"  @click="isModalShown=false">Close</button>
      </div>
    </div>

    <div class="container">
      <div class="header">
        <h1>Notes</h1>
        <button @click="isModalShown=true">+</button>
      </div>

      <div class="cards-container">
        <div class="card">
          <p class="main-text">Lorem ipsum dolor sit amet, consectetur adipisicing elit. Aspernatur dolor, est hic nisi placeat voluptatum.</p>
          <p class="date">10/09/2025</p>
        </div>
      </div>
    </div>
  </main>
</template>

<style scoped>
main{
  position: relative;
  width: 100vw;
  height: 100vh;
}
.container{
  max-width: 1000px;
  padding: 2rem;
  margin: 0 auto;
}
.header{
  display: flex;
  justify-content: space-between;
  align-items: center;
}

h1{
  font-size: 4.5rem;
  font-weight: bold;
  margin-bottom: 3rem;
}

.header button{
  border: none;
  padding: 1rem;
  width: 50px;
  height: 50px;
  cursor: pointer;
  background-color: cornflowerblue;
  border-radius: 100%;
  color: white;
  font-size: 1.2rem;
  font-weight: bold;
}

.card{
  width: 225px;
  height: 225px;
  background-color: bisque;
  padding: 2rem;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.date{
  font-size: small;
  font-style: italic;
}

.cards-container{
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
}

.overlay{
  position: absolute;
  width: 100vw;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: grid;
  place-items: center;
}

.modal{
  width: 400px;
  background-color: white;
  border-radius: 1rem;
  padding: 2rem;
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
.modal button{
  border: none;
  padding: 1rem;
  font-size: 1.2rem;
  width: 100%;
  background-color: coral;
  color: white;
  cursor: pointer;
  border-radius: 1rem;
}

.modal .close{
  background-color: blueviolet;

  //border-radius: 100%;
  //width: 2rem;
  //height: 2rem;
  //padding: 0.3rem;
}
</style>
