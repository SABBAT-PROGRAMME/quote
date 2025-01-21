<template>
  <div class="quote-container" prevent-default>
    <article>
      <header class="quote-author">
        <span class="author-text">Auteur :</span> {{ auteur }}
      </header>
      <body>
        <p class="quote-text">{{ citation }}</p>
      </body>
      <footer class="quote-date">
        <i>Date : {{ date }}</i>
      </footer>
    </article>
  </div>
</template>

<script setup>
// Définition des props avec `defineProps`
const props = defineProps({
  citation: String,
  auteur: String,
  date: String,
  index: Number,
});
</script>

<style>
.quote-container {
  background-color: #f9f9f9;
  border: 1px solid #ddd;
  padding: 1rem;
  border-radius: 5px;
  max-width: 400px;
  margin: 1rem auto;
  text-align: center;
  box-shadow: 0 2px 5px rgba(0, 0, 0, 0.1);
}

.quote-text {
  font-size: 1.2rem;
  font-weight: bold;
  margin-bottom: 0.5rem;
}

.quote-author {
  font-size: 1rem;
  color: #eb5a3c;
}

.author-text {
  color: white;
}

.quote-date {
  font-size: 0.9rem;
  color: #888;
  margin-top: 0.5rem;
}
</style>
