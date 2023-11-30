<script setup>
import { reactive, ref, onMounted } from 'vue'
import { db } from './data/guitarras'
import Guitarra from './components/Guitarra.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

const guitarras = ref([]) // State de las guitarras
const carrito = ref([]) // State carrito de compras

onMounted(() => {
    guitarras.value = db;
})

const agregarCarrito = (guitarra) => {
    guitarra.cantidad = 1;
    carrito.value.push(guitarra) // Push añade un elemento a un arreglo al final - Modifica el arreglo original ☢️
}
</script>
    
<template>
    <Header />
    <main class="container-xl mt-5">
        <h2 class="text-center">Nuestra Colección</h2>

        <div class="row mt-5">
            <Guitarra v-for="guitarra in guitarras" :guitarra="guitarra" @agregar-carrito="agregarCarrito" />
        </div>
    </main>
    <Footer />
</template>
