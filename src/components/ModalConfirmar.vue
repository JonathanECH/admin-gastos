<script setup>
import iconoCerrarModal from '../assets/img/cerrar.svg'

const emit = defineEmits(['cerrar-modal', 'confirmar']);

const props = defineProps({
    titulo: {
        type: String,
        required: true
    },
    detalles: {
        type: String,
        default: ''
    }
});
</script>

<template>
    <div class="modal" @click.self="emit('cerrar-modal')">
        <div class="contenedor">
            <div class="cerrar-modal">
                <img :src="iconoCerrarModal" alt="Icono cerrar modal" @click="emit('cerrar-modal')">
            </div>
            <div class="confirmar">
                <h2>{{ titulo }}</h2>
                <p v-if="detalles">{{ detalles }}</p>
                <div class="botones">
                    <button type="button" @click="emit('cerrar-modal')">No, Cancelar</button>
                    <button type="button" @click="emit('confirmar')" class="eliminar">Sí, Confirmar</button>
                </div>
            </div>
        </div>
    </div>
</template>

<style lang="scss" scoped>
@use 'sass:color';

.modal {
    position: fixed;
    z-index: 110;
    inset: 0;
    background-color: rgba($negro, 0.5);

    transition: opacity 300ms ease-in;

    .contenedor {
        width: 90%;
        max-width: 48rem;
        position: fixed;
        top: 50%;
        left: 50%;
        transform: translate(-50%, -50%);
        background-color: $blanco;
        border-radius: 1.6rem;
        padding: 4rem 3rem 3rem 3rem;
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.25);
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

    .confirmar {
        text-align: center;

        h2 {
            font-size: 2.4rem;
            font-weight: 700;
            color: $negro;
            margin: 0 auto 1rem auto;
        }

        p {
            font-size: 1.6rem;
            color: $gris-oscuro;
            margin: 0 auto 2.5rem auto;
            line-height: 1.5;
        }

        .botones {
            display: flex;
            gap: 1.5rem;

            button {
                width: 100%;
                padding: 1.2rem 1rem;
                border-radius: 1rem;
                border: none;
                font-size: 1.8rem;
                font-weight: 700;
                cursor: pointer;
                transition: background-color 300ms ease, transform 150ms ease;
                background-color: $gris;
                color: $blanco;

                &:hover {
                    background-color: color.scale($gris, $lightness: -15%);
                }

                &:active {
                    transform: scale(0.98);
                }

                &.eliminar {
                    background-color: $eliminar;
                    color: $blanco;

                    &:hover {
                        background-color: color.scale($eliminar, $lightness: -10%);
                    }
                }
            }
        }
    }
}
</style>