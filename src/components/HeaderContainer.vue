<template>
    <header>

        <img src="../assets/booley-plus.png" alt="logo">

        <ul>
            <li @click="$emit('activeHome')"> 
                <i class="fas fa-home"></i>
                <p>home</p>
            </li>
            <li @click="$emit('activeSearch')">
                <i class="fas fa-search"></i> 
                <p>cerca</p>     
            </li>
            <li @click="$emit('activeFavorites')">
                <i class="fas fa-heart"></i>
                <p>la mia lista</p>           
            </li>
        </ul>
        
    </header>
</template>

<script>
export default {
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

        ul {
            list-style: none;
            display: flex;

            li {
                margin: 0 15px;
                cursor: pointer;
                font-weight: bold;
                color: #f9f9f9;
                text-decoration: none;
                padding-bottom: 4px;
                border-bottom: 3px solid transparent;

                position: relative;
                display: flex;
                align-items: center;

                &:hover p::before{
                    background-color: #f9f9f9;
                    transform: scaleX(1);
                    visibility: visible;
                    opacity: 1;
                }
                p {
                    text-transform: uppercase;
                    padding-left: 7px;

                    &::before {
                        background-color: rgba(249, 249, 249, 0.4);
                        border-radius: 0px 0px 4px 4px;
                        bottom: -6px;
                        height: 3px;
                        left: 0px;
                        opacity: 1;
                        position: absolute;
                        right: 0px;
                        transform-origin: left center;
                        transform: scaleX(0);
                        transition: all 250ms cubic-bezier(0.25, 0.46, 0.45, 0.94) 0s;
                        visibility: hidden;
                        width: auto;
                        content: '';
                    }
                }     
            }          
        }
        
    }
</style>