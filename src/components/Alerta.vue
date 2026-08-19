<template lang="">
    <div class="alerta">
        <slot></slot>
    </div>
</template>

<style lang="scss" scoped>
    .alerta{
        padding: 1rem;
        font-weight: 900;
        font-size: 1.6rem;
        text-align: center;
        text-transform: uppercase;
        background-color: $blanco;
        border-left: 0.5rem solid #b91c1c;
        color: #b91c1c
    }
</style>