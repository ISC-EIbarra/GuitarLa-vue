<!-- Lógica -->
<script setup>
import { ref, reactive, onMounted } from 'vue';
import { db } from './data/guitarras.js';
import Guitarra from './components/Guitarra.vue';
import Header from './components/Header.vue';
import Footer from './components/Footer.vue';

// const state = reactive({
//   guitarras: [],
// });

const guitarras = ref([]);
const carrito = ref([]);

onMounted(() => {
  guitarras.value = db;
});

const agregarCarrito = (guitarra) => {
  const existeCarrito = carrito.value.findIndex(
    (producto) => producto.id === guitarra.id
  );

  if (existeCarrito >= 0) {
    carrito.value[existeCarrito].cantidad++;
  } else {
    guitarra.cantidad = 1;
    carrito.value.push(guitarra);
  }
};
</script>

<!-- HTML -->
<template>
  <Header :carrito="carrito" />
  <main class="container-xl mt-5">
    <h2 class="text-center">Nuestra Colección</h2>

    <div class="row mt-5">
      <Guitarra
        v-for="guitarra in guitarras"
        :guitarra="guitarra"
        @agregar-carrito="agregarCarrito"
      />
      <!-- FIN GUITARRA -->
    </div>
  </main>

  <Footer />
</template>

<!-- CSS/SCSS -->
<style scoped></style>
, onMounted, onMounted
