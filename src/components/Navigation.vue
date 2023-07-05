<template>
    <div class="menu">
        <div class="label">
            <h1 class="logo">DD Tracker</h1>
        </div>
        <div class="navigation">
            <ul class="items" v-for="item in menuItems" :key="item">
                <li class="id"><a href="#" class="links">{{ item }}</a></li>
            </ul>
        </div>
    </div>
    <hr class="navline" />
</template>

<script>
export default {
    data() {
        return {
            menuItems : ['Count', 'Raw', 'Yearly Count', 'Bulk Insert']
        }
    }

}
</script>

<style>
    .menu {
        background-color:aquamarine;
    }
    .label {
        display: inline-flex;
    }
    .logo {
        padding-left: 25px;
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        font-weight: lighter;
        font-size: 18px;
    }
    .navigation {
        display: inline-flex;
    }
    .links {
        text-decoration: none;
        color: black;
        font-family: 'Gill Sans', 'Gill Sans MT', Calibri, 'Trebuchet MS', sans-serif;
        font-size: 15px;
        transition: background-color 2s ease-out 100ms
    }
    .links:hover {
        background-color:aqua;
    }
    .items{
        list-style-type: none
    }
    .navline {
        margin: 0;
        height: 3.5px;
        background: grey;
        opacity: 0.5;
    }
</style>