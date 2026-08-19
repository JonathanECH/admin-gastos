<script>
import App from '../App.vue';
</script>
<template>
    <form class="presupuesto">
        <div class="campo">
            <label for="nuevo-presupuesto">Define tu Presupuesto</label>
            <input type="number" min="0" id="nuevo-presupuesto" class="nuevo-presupuesto"
                placeholder="Añade tu presupuesto en $">
        </div>
        <input type="submit" value="Definir Presupuesto">
    </form>
</template>

<style lang="scss" scoped>
.presupuesto {
    width: 100%;

    input[type=submit] {
        background-color: $azul;
        padding: 1rem;
        border: none;
        border-radius: 1rem;
        color: $blanco;
        cursor: pointer;
        transition: color 5ms ease-in-out;

        &:hover {
            background-color: lighten($azul, 5%);
        }
    }
}
.campo {
    display: flex;
    flex-direction: column;

    label {
        cursor: pointer;
        margin-bottom: 1rem;
    }

    input {
        border: solid 0.1rem;
        border-radius: 1.2rem;
        padding: 0.8rem;
        margin-bottom: 1rem;
    }
}
</style>