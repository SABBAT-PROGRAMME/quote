<template>
  <h1>Liste de citations !</h1>

  <div v-if="citation">
    <Quote
      :citation="citation[currentIndex].citation"
      :auteur="citation[currentIndex].auteur"
      :date="citation[currentIndex].date"
      :index="currentIndex"
    />
    <button type="button" class="next-button" @click="nextQuote">
      Citation Suivante
    </button>
  </div>
</template>

<script setup>
import { ref } from "vue";
import Quote from "./components/Quote.vue";

const url = "/quote.json";
const citation = ref(null);

const currentIndex = ref(0);

fetch(url)
  .then((response) => {
    if (!response.ok) {
      throw new Error("Erreur réseau lors du chargement du fichier JSON.");
    }
    return response.json();
  })
  .then((data) => {
    console.log("Données récupérées :", data);
    citation.value = data;
  })
  .catch((error) => {
    console.error("Erreur :", error.message);
  });

const nextQuote = () => {
  if (citation.value && currentIndex.value < citation.value.length - 1) {
    currentIndex.value = Math.floor(Math.random() * citation.value.length);
  } else {
    currentIndex.value = 0;
  }
};
</script>

<style>
h1 {
  text-align: center;
  font-family: Arial, sans-serif;
  color: #398712;
}

button {
  display: block;
  margin-left: auto;
}

.next-button:hover {
  background-color: #45a049;
}
</style>
