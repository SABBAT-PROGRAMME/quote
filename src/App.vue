<!-- tamplate -->
<template>
  <h1>Liste de citations !</h1>

  <p>Voici la citation du jour</p>
  {{ citation }}
</template>

<!-- script -->
<script setup>
import { ref } from "vue";

let url = "../public/quote.json";

let citation = ref("");
let data = ref("");

// fecth

fetch(url)
  .then((response) => {
    if (response.ok) {
      return response.json();
    }
    throw new Error("Network response was not ok.");
  })
  .then((data) => {
    citation.value = data;
  })
  .catch((error) => {
    console.log(error);
  });
</script>

<!-- style -->
<style></style>
