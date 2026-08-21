<script setup>
import { computed } from 'vue';
import CircleProgressImport from 'vue3-circle-progress';
import "vue3-circle-progress/dist/circle-progress.css";
import { formatearCantidad } from '../helpers';
const CircleProgress = CircleProgressImport.default;
const emit = defineEmits(['resetear-app'])
const props = defineProps({
    presupuesto: {
        type: Number,
        required: true
    },
    disponible: {
        type: Number,
        required: true
    },
    gastado: {
        type: Number,
        required: true
    }
})
const porcentaje = computed(() => {
    return parseInt(((props.presupuesto - props.disponible) * props.presupuesto) / 100)
})
</script>
<template>
    <div class="dos-columnas">
        <div class="contenedor-grafico">
            <p class="porcentaje" :style="{ color: porcentaje > 0 ? '#3b82f6' : '#64748b' }">{{ porcentaje }}%</p>
            <CircleProgress :percent="porcentaje" :size="250" :border-width="30" :border-bg-width="30"
                fill-color="#3b82f6" empty-color="#e1e1e1" />
        </div>

        <div class="contenedor-presupuesto">
            <p><span>Presupuesto:</span> {{ formatearCantidad(presupuesto) }}</p>
            <p><span>Disponible:</span> {{ formatearCantidad(disponible) }}</p>
            <p><span>Gastado:</span> {{ formatearCantidad(gastado) }}</p>
            <div class="reset-app">
                <button type="button" @click="emit('resetear-app')">Resetear App</button>
            </div>
        </div>
    </div>
</template>
<style lang="scss">
@use 'sass:color';

.dos-columnas {
    display: flex;
    flex-direction: column;
    align-items: center;
    gap: 2rem;

    @include m.tablet {
        display: flex;
        flex-direction: row;
        align-items: initial;
        gap: 2rem;
    }

    .contenedor-grafico {
        position: relative;

        .porcentaje {
            position: absolute;
            margin: auto;
            top: calc(50% - 1.5rem);
            right: 0;
            left: 0;
            text-align: center;
            z-index: 2;

            font-weight: 900;
            font-size: 3rem;
        }
    }

    .contenedor-presupuesto {
        text-align: center;

        @include m.tablet {
            display: flex;
            flex-direction: column;
            text-align: left;
            flex: 1;
        }

        p {
            font-size: 2.4rem;
            color: $gris-oscuro;
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
        font-size: 2.2rem;
        text-transform: uppercase;
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