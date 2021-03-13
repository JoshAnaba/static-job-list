<template>
    <div class='header'>
        <slot></slot>
    </div>
</template>

<script>
export default {
    name: 'Header'
}
</script>

<style scoped>

.header{
    width: 100%;
    height: 150px;
}

svg{
    width: 100%;
}


</style>