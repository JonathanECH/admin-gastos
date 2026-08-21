<script setup>
import { formatearCantidad, formatearFecha } from '../helpers';
import IconoAhorro from '../assets/img/icono_ahorro.svg'
import IconoCasa from '../assets/img/icono_casa.svg'
import IconoComida from '../assets/img/icono_comida.svg'
import IconoGastos from '../assets/img/icono_gastos.svg'
import IconoOcio from '../assets/img/icono_ocio.svg'
import IconoSalud from '../assets/img/icono_salud.svg'
import IconoSuscripciones from '../assets/img/icono_suscripciones.svg'
const diccionarioIconos = {
    ahorro: IconoAhorro,
    comida: IconoComida,
    casa: IconoCasa,
    gastos: IconoGastos,
    ocio: IconoOcio,
    salud: IconoSalud,
    suscripciones: IconoSuscripciones
}

const props = defineProps({
    gasto: {
        type: Object,
        required: true
    }
})

defineEmits(['seleccionar-gasto'])
</script>

<template>

    <div class="gastos-realizados sombra">
        <div class="gasto">
            <img :src="diccionarioIconos[gasto.categoria]" alt="Incono de gasto" class="icono">
            <div class="detalles">
                <p class="categoria">{{ gasto.categoria }}</p>
                <p class="nombre" @click="$emit('seleccionar-gasto', gasto.id)">{{ gasto.nombre }}</p>
                <p class="fecha">Fecha: <span>{{ formatearFecha(gasto.fecha) }}</span></p>
            </div>
        </div>
        <p class="cantidad">{{ formatearCantidad(gasto.cantidad) }}</p>
    </div>

</template>

<style lang="scss" scoped>
.gastos-realizados {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: $blanco;
    padding: 2rem;
    border-radius: 1.2rem;
    margin-bottom: 2rem;

    .gasto {
        display: flex;

        .icono {
            width: 5rem;
        }

        p {
            margin-bottom: 1rem;
        }
    }

    .cantidad {
        font-size: 2.4rem;
        font-weight: 900;
        color: $negro;
    }
}

.detalles {
    display: flex;
    flex-direction: column;
    margin: 0 0 0 2rem;

    .categoria {
        font-weight: 900;
        font-size: 1.8rem;
        color: $gris;
        text-transform: uppercase;
    }

    .nombre {
        font-weight: 900;
        font-size: 2.4rem;
        color: $gris-oscuro;
        margin-bottom: 0.5rem;
        cursor: pointer;
        transition: color 300ms ease;

        &:hover {
            color: $azul;
        }
    }

    .fecha {
        font-size: 1.9rem;
        color: $gris-oscuro;
        font-weight: 900;

        span {
            font-weight: 400;
            color: $gris;
            text-transform: capitalize;
        }
    }

    p {
        margin: 0;
    }
}
</style>