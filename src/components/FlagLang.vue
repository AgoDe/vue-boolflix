<template>
    <div class="flag">
        <img :src="`/images/${showFlag.path}`" :alt="showFlag.state">
    </div>
</template>

<script>
export default {
    props: {
        language: String,

    },
    data() {
        return {
            flags: [
                {
                state: 'italy',
                abbr: 'it',
                path: 'italy-flag.png',
                },
                {
                state: 'france',
                abbr: 'fr',
                path: 'france-flag.png',
                },
                {
                state: 'germany',
                abbr: 'de',
                path: 'germany-flag.png',
                },
                {
                state: 'united-kingdom',
                abbr: 'en',
                path: 'united-kingdom-flag.png',
                },
                {
                state: 'south-korea',
                abbr: 'ko',
                path: 'south-korea-flag.png',
                },
                {
                state: 'spain',
                abbr: 'es',
                path: 'spain-flag.png',
                },
            ],

        }
    },
    computed: {
        showFlag: function() {
           const flag = this.flags.filter((element) => {
            return element.abbr === this.language
           });
            return flag[0]
        }
    }
    
}
</script>

<style lang="scss" scoped>

    img {
        height: 25px;
        width:  37px;
    }

</style>