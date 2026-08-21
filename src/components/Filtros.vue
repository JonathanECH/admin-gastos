<script setup>
import { ref } from 'vue';
defineEmits(['update:filtro']);
defineProps(['filtro']);

const menuAbierto = ref(false);
</script>

<template>
    <div class="filtros sombra contenedor">
        <form>
            <div class="campo">
                <label for="filtro">Filtrar Gastos:</label>
                <div class="select-personalizado">
                    <select name="filtro" id="filtro" :value="filtro" @click="menuAbierto = !menuAbierto"
                        @input="$emit('update:filtro', $event.target.value)">
                        <option value="" disabled>Usar Filtro </option>
                        <option value="sinFiltro">Sin filtro</option>
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
        </form>
    </div>
</template>

<style lang="scss" scoped>
.filtros {
    margin-top: 10rem;

    .campo {
        display: flex;
        gap: 2rem;
        align-items: center;

        label {
            font-size: 2.4rem;
            font-weight: 900;
            color: $gris-oscuro;
        }

        .select-personalizado {
            position: relative;
            overflow: hidden;
            border-radius: 1rem;
            background-color: $blanco;
            width: 100%;

            @include m.tablet {
                flex: 1;
            }

            select {
                width: 100%;
                appearance: none;
                -webkit-appearance: none;

                -moz-appearance: none;
                border: none;
                border-radius: 1rem;
                padding: 1rem;
                text-align: center;
                cursor: pointer;
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
    }
}
</style>