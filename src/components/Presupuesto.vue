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
@use 'sass:color';
.presupuesto {
    width: 100%;

    input[type=submit] {
        background-color: $azul;
        width: 100%;
        font-weight: 900;
        font-size: 2.2rem;
        padding: 1rem;
        border: none;
        border-radius: 1rem;
        color: $blanco;
        cursor: pointer;
        transition: background 300ms ease;

        &:hover {
            background-color: color.scale($azul, $lightness: -10%);
        }
    }
}

.campo {
    @include m.grid(1,1,2);

    label {
        cursor: pointer;
        font-size: 2rem;
        font-weight: bold;
        text-align: center;
        color: $azul;
        margin-bottom: 2rem;
    }

    input {
        border: none;
        text-align: center;
        font-size: 2rem;
        border-radius: 1.2rem;
        background-color: $gris-claro;
        padding: 0.8rem;
        margin-bottom: 2rem;
    }
}
</style>