<template>
<div class="nav">
    <ul>
            <img src="../assets/faucet.gif" alt="#">
            <p class="yi">蚁穴</p>
        <li class="login">
            <a href="#">登录</a>
            </li>
        <li class="Registration">
            <a href="#">注册</a>
            </li>
    </ul>
</div>
</template>

<script>
    export default {

    }
</script>

<style scoped>
    .nav{
        color: white;
        text-decoration: none;
    }
    ul {
        list-style-type: none;
        height: 70px;
        margin: 0 auto;
        padding: 0;
        overflow: hidden;
        background-color:#4DD0E1;
    }

    img {
        display: block;
        float: left;
        border-radius: 50%;
        border: 1px solid #4DD0E1;
        /* padding:8px 30px 8px 200px; */
        margin: 3px 30px 3px 248px;
        width: 60px;
        
    }

    .yi{
        position: absolute;
        font-size: 50px;
        text-align: left;
        margin: 0px !important;
        padding: 2px 20px 2px 320px;

    }

    li{
        font-size: 25px;
        text-align: right;
    }
    li a{
        color: white;
        width: 60px;
        margin: 18px;
        text-decoration:none;

    }
    .login a{
        position: absolute;
        right: 300px;
    }
    .Registration a{
        position: absolute;
        right: 232px;
    }

    li a:hover {
        color:#EBEDEF;
    }
</style>
