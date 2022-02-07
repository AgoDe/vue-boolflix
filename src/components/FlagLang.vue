<template>
    <div class="flag"
    :class="language">
        {{ language }}
    </div>
</template>

<script>
export default {
    props: {
        language: String,
    }
}

</script>

<style lang="scss" scoped>

 .flag {
    width: 37px;
    height: 25px;
    margin: 0 auto;
    // background: url('../assets/download.png') center center;
    background-size: cover;

 }
 .flag.en {
    background: url(../assets/united-kingdom-flag.png) center center no-repeat;
    background-size: contain;
    color: transparent;
 }
 .flag.it {
    background: url(../assets/italy-flag.png) center center no-repeat;
    background-size: contain;
    color: transparent;

 }
 .flag.fr {
    background: url(../assets/france-flag.png) center center no-repeat;
    background-size: contain;
    color: transparent;

 }
 .flag.es {
    background: url(../assets/spain-flag.png) center center no-repeat;
    background-size: contain;
    color: transparent;

 }
 .flag.ko {
    background: url(../assets/south-korea-flag.png) center center no-repeat;
    background-size: contain;
    color: transparent;

 }
 .flag.de {
    background: url(../assets/germany-flag.png) center center no-repeat;
    background-size: contain;
    color: transparent;

 }

</style>