<template>
    <header>

        <img src="../assets/boolflix-logo.png" alt="logo">

        <div class="search-box">
            <input
            type="text"
            placeholder="Search Movies"
            v-model="searchInput"
            >
        </div>

    </header>
</template>

<script>
export default {
    props: {

    },
    data() {
        return {
            searchInput: '',

        }
    }
    
}
</script>

<style lang="scss" scoped>

    header {
        height: 80px;
        padding: 0 10px;
        display: flex;
        align-items: center;
        justify-content: space-between;

        img {
            height: 60px;
        }
    }
</style>