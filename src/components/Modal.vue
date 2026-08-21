<script setup>
import { ref } from 'vue';
import Alerta from './Alerta.vue';
import iconoCerrarModal from '../assets/img/cerrar.svg'
const emit = defineEmits(['cerrar-modal', 'guardar-gasto', 'eliminar-gasto', 'update:nombre', 'update:cantidad', 'update:categoria']);
const props = defineProps({
    modal: {
        type: Object,
        required: true
    },
    nombre: {
        type: String,
        required: true
    },
    cantidad: {
        type: [String, Number],
        required: true
    },
    categoria: {
        type: String,
        required: true
    },
    disponible: {
        type: Number,
        required: true
    },
    id: {
        type: [String, null],
        required: true
    }
});
// Variables
const cantidadOld = props.cantidad;
const mensaje = ref('');
const menuAbierto = ref(false);

//Para agregar un gasto
const agregarGasto = () => {
    //Validar que no haya campos vacíos
    const { nombre, cantidad, categoria, disponible, id } = props;
    if ([nombre, cantidad, categoria].includes('')) {
        mensaje.value = 'Todos los campos son obligatorios';
        setTimeout(() => {
            mensaje.value = ''
        }, 3000)
        return;
    }

    //Validar que la cantidad sea un número positivo
    if (isNaN(cantidad) || cantidad <= 0) {
        mensaje.value = 'La cantidad debe ser un número positivo';
        setTimeout(() => {
            mensaje.value = ''
        }, 3000)
        return;
    }

    if (id) {
        if (cantidad > cantidadOld + disponible) {
            mensaje.value = 'Estás excediendo el presupuesto';
            setTimeout(() => {
                mensaje.value = ''
            }, 3000)
            return;
        }
    } else {
        //Validar que no se exceda del presupuesto
        if (cantidad > disponible) {
            mensaje.value = 'Estás excediendo el presupuesto';
            setTimeout(() => {
                mensaje.value = ''
            }, 3000)
            return;
        }
    }
    emit('guardar-gasto');
    emit('cerrar-modal');
}
</script>

<template>
    <div class="modal" :class="{ animar: modal.animar }" @click.self="emit('cerrar-modal')">
        <div class="contenedor">
            <div class="cerrar-modal">
                <img :src="iconoCerrarModal" alt="Icono cerrar modal" @click="emit('cerrar-modal')">
            </div>
            <form class="formulario" @submit.prevent="agregarGasto">
                <legend>{{ id ? 'Guardar Cambios' : 'Añadir Gasto' }}</legend>
                <Alerta v-if="mensaje" class="alerta">{{ mensaje }}</Alerta>
                <!--?Alerta-->
                <div class="campo">
                    <label for="nombre">Nombre de Gasto:</label>
                    <input type="text" id="nombre" placeholder="Añade el Nombre del Gasto" :value="nombre"
                        @input="emit('update:nombre', $event.target.value)">
                </div>

                <div class="campo">
                    <label for="cantidad">Cantidad:</label>
                    <input type="number" id="cantidad" placeholder="Añade la Cantidad, ej: 300" :value="cantidad"
                        @input="emit('update:cantidad', +$event.target.value)">
                </div>

                <div class="campo">
                    <label for="categoria">Categoria:</label>
                    <div class="select-personalizado">
                        <select name="categoria" id="categoria" :value="categoria" @click="menuAbierto = !menuAbierto"
                            @input="emit('update:categoria', $event.target.value)">
                            <option value="" disabled>-- Seleccionar --</option>
                            <option value="ahorro">Ahorro</option>
                            <option value="comida">Comida</option>
                            <option value="casa">Casa</option>
                            <option value="gastos">Gastos</option>
                            <option value="ocio">Ocio</option>
                            <option value="salud">Salud</option>
                            <option value="suscripciones">Suscripciones</option>
                        </select>
                        <font-awesome-icon icon="fa-solid fa-angle-down" :class="{ rotar: menuAbierto }" />
                    </div>
                </div>
                <div v-if="id" class="botones">
                    <button type="button" @click="emit('eliminar-gasto')" class="eliminar">Eliminar</button>
                    <input type="submit" value="Guardar"></input>
                </div>
                <input v-else type="submit" value="Añadir Gasto">
            </form>
        </div>
    </div>
</template>

<style lang="scss" scoped>
@use 'sass:color';

.modal {
    position: fixed;
    z-index: 100;
    inset: 0;
    background-color: rgba($negro, 0.5);
    opacity: 0;
    transition: opacity 300ms ease-in;

    &.animar {
        opacity: 1;
    }

    .contenedor {
        @include m.contenedor;
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        background-color: $blanco;
        border-radius: 1rem;
        padding: 5rem;
    }

    .cerrar-modal {
        position: absolute;
        top: 1.8rem;
        right: 1.8rem;
        background-color: $negro;
        border-radius: 50%;
        width: 3.2rem;
        height: 3.2rem;
        display: flex;
        justify-content: center;
        align-items: center;
        cursor: pointer;
        transition: all 300ms ease;
        box-shadow: 0 2px 6px rgba(0, 0, 0, 0.15);

        &:hover {
            background-color: $eliminar;
            transform: scale(1.1) rotate(90deg);
        }

        img {
            width: 1.6rem;
            height: 1.6rem;
            cursor: pointer;
        }
    }

    .formulario {
        legend {
            font-size: 3rem;
            font-weight: 700;
            color: $negro;
            margin: 0 auto 3rem auto;
        }

        .alerta {
            margin-bottom: 1rem;
        }

        .campo {
            display: grid;
            gap: 2rem;
            margin-bottom: 2rem;
        }

        label {
            font-size: 2.4rem;
            color: $negro;
        }

        input,
        button,
        select {
            width: 100%;
            padding: 1rem;
            border-radius: 1rem;
            border: 1px solid $gris;
            font-size: 2.2rem;
        }

        .select-personalizado {
            position: relative;
            overflow: hidden;

            select {
                cursor: pointer;
                appearance: none;
                -webkit-appearance: none;
                -moz-appearance: none;
            }

            .fa-angle-down {
                pointer-events: none;
                position: absolute;
                right: 2rem;
                top: 50%;
                transform: translateY(-50%);
                transition: transform .3s ease;

                &.rotar {
                    transform: translateY(-50%) rotate(-180deg);
                }
            }
        }

        .botones {
            display: flex;
            gap: 2rem;

            .eliminar {
                background-color: $eliminar;
                color: $blanco;
                font-weight: 700;
                cursor: pointer;
                transition: background-color 300ms ease;

                &:hover {
                    background-color: color.scale($eliminar, $lightness: -10%);
                }
            }
        }

        input[type="submit"],
        button[type="submit"],
        button {
            border: none;
            background-color: $azul;
            color: $blanco;
            font-weight: 700;
            cursor: pointer;
            transition: background-color 300ms ease;

            &:hover {
                background-color: color.scale($azul, $lightness: -10%);
            }
        }
    }
}
</style>