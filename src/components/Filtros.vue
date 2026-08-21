<script setup>
defineEmits(['update:filtro']);
defineProps(['filtro']);
</script>

<template>
    <div class="filtros sombra contenedor">
        <form>
            <div class="campo">
                <label for="filtro">Elige la categoria:</label>
                <select name="filtro" id="filtro" :value="filtro"
                @input="$emit('update:filtro', $event.target.value)">
                    <option value="" disabled>-- Usar Filtro --</option>
                    <option value="sinFiltro">Sin filtro</option>
                    <option value="ahorro">Ahorro</option>
                    <option value="comida">Comida</option>
                    <option value="casa">Casa</option>
                    <option value="gastos">Gastos</option>
                    <option value="ocio">Ocio</option>
                    <option value="salud">Salud</option>
                    <option value="suscripciones">Suscripciones</option>
                </select>
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

        select {
            flex: 1;
            border: none;
            border-radius: 1rem;
            padding: 1rem;
            text-align: center;
            cursor: pointer;
        }
    }
}
</style>