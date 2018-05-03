<template>
    <div class="img_container">
        <Office></Office>
    </div>
</template>
<script>
    import Office from "./Office.vue"
    export default {
        name: 'OfficeMap',
        components: {
            Office: Office
        }
    }
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    .img_container {
        height: 100vh;
        background-image: url("../assets/layout.svg");
        background-size: auto 100vh;
        background-repeat: no-repeat;
        background-position: center;
        text-align: center;
    }
</style>
