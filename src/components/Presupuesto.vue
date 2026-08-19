<script>

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
        width: 100%;
        font-weight: bold;
        font-size: 2.2rem;
        padding: 1rem;
        margin-top: 2rem;
        border: none;
        border-radius: 1rem;
        color: $blanco;
        cursor: pointer;
        transition: color 5ms ease-in-out;

        &:hover {
            background-color: darken($azul, 5%);
        }
    }
}

.campo {
    @include m.grid(1,1,2);

    label {
        cursor: pointer;
        font-size: 2.5rem;
        font-weight: bold;
        margin-bottom: 1rem;
    }

    input {
        border: none;
        text-align: center;
        font-size: 2rem;
        border-radius: 1.2rem;
        background-color: $gris-claro;
        padding: 0.8rem;
        margin-bottom: 1rem;
    }
}
</style>