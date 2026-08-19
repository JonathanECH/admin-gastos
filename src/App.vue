<script setup>
import { ref } from 'vue';
import Presupuesto from './components/Presupuesto.vue';
import ControlPresupuesto from './components/ControlPresupuesto.vue';
import iconoNuevoGasto from './assets/img/nuevo-gasto.svg'
const presupuesto = ref(0);
const disponible = ref(0);
const definirPresupuesto = cantidad => {
  presupuesto.value = cantidad
  disponible.value = cantidad
}
</script>

<template>
  <div>
    <header>
      <h1>Planificador De Gastos</h1>
      <div class="contenedor-header contenedor sombra">
        <Presupuesto v-if="presupuesto === 0" @definir-presupuesto="definirPresupuesto" />
        <ControlPresupuesto v-else :presupuesto="presupuesto" :disponible="disponible" />
      </div>
    </header>
    <main v-if="presupuesto > 0">

      <div class="gasto-nuevo">
        <img :src="iconoNuevoGasto" alt="Icono nuevo gasto">
      </div>
    </main>
  </div>
</template>

<style lang="scss">
html {
  font-size: 62.5%;
  box-sizing: border-box;
}

*,
*::before,
*::after {
  box-sizing: inherit;
}

body {
  font-size: 1.6rem;
  font-family: 'Lato', sans-serif;
  background-color: $gris-claro;
}

h1 {
  font-size: 4rem;
}

h2 {
  font-size: 3rem;
}

header {
  background-color: $azul;

  h1 {
    padding: 3rem 0;
    margin: 0;
    color: $blanco;
    text-align: center;
  }
}

.contenedor {
  @include m.contenedor;
}

.contenedor-header {
  margin-top: -5rem;
  transform: translateY(5rem);
  padding: 5rem;
}

.sombra {
  box-shadow: 0px 10px 15px -3px rgba(0, 0, 0, 0.1);
  background-color: $blanco;
  border-radius: 1.2rem;
  padding: 5rem;
}

.gasto-nuevo {
  position: fixed;
  right: 2.5rem;
  bottom: 2.5rem;

  @include m.tablet {
    right: 5rem;
    bottom: 5rem;
  }

  img {
    width: 5rem;

    &:hover {
      cursor: pointer;
    }
  }
}
</style>