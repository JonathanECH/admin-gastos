<script setup>
import imagen from '../assets/img/grafico.jpg'
const props = defineProps({
    presupuesto: {
        type: Number,
        required: true
    }
})
</script>
<template>
    <div class="grid">
        <div class="contenedor-grafico">
            <img :src="imagen" alt="">
        </div>

        <div class="contenedor-presupuesto">
            <p><span>Presupuesto:</span> ${{ presupuesto }}</p>
            <p><span>Disponible:</span> ${{ presupuesto }}</p>
            <p><span>Gastado:</span> ${{ presupuesto }}</p>
            <div class="reset-app">
                <button type="reset">Resetear App</button>
            </div>
        </div>
    </div>
</template>
<style lang="scss">
@use 'sass:color';

.grid {
    display: flex;
    flex-direction: column;
    gap: 2rem;

    @include m.tablet {
        @include m.grid(2, 1fr, 2rem);
    }

    .contenedor-presupuesto {
        @include m.tablet {
            display: flex;
            flex-direction: column;
        }

        p {
            font-size: 2rem;
            color: $gris;
            margin: 1.3rem 0;

            span {
                font-weight: 800;
                color: $azul
            }
        }
    }
}

.reset-app {
    margin-top: 2rem;

    @include m.tablet {
        margin-top: auto;
    }

    @include m.desktop {
        order: -1; // Mueve el botón al principio
        margin-bottom: 2rem;
        margin-top: 0;
    }

    button {
        font-weight: 800;
        font-size: 1.8rem;
        width: 100%;
        border: none;
        border-radius: 1rem;
        padding: 1rem;
        background-color: $fucsia;
        color: $blanco;
        cursor: pointer;
        transition: background 300ms ease;

        &:hover {
            background-color: color.scale($fucsia, $lightness: -10%);
        }
    }
}
</style>