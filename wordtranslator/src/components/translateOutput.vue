<template>


<textarea class="col-lg-6 col-lg-4 form-control " readonly style=" position: absolute; left:50%; transform: translate(-50%,-50%);">{{translatedText}}</textarea>


</template>

<script>
    export default {
        name: "translateOutput",
        props:['translatedText']

    }
</script>

<style scoped>

</style>
