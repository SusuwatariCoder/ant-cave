<template>
<div class="nav">
    <ul>
            <img src="../assets/faucet.gif" alt="#">
            <p class="yi">蚁穴</p>
        <li @click="login" class="login">
            <a class="el-icon-s-home" href="#">{{ loginText }}</a>
            </li>
        <li @click="create" class="Registration">
            <!-- 使用说明 https://element.eleme.cn/#/zh-CN/component/icon -->
            <a class="el-icon-edit" href="#">创建身份</a>
            </li>
        <li @click="create" class="Registration">
            <!-- 使用说明 https://element.eleme.cn/#/zh-CN/component/icon -->
            <a class="el-icon-edit" href="#">创建身份</a>
            </li>
        用户: {{ addressText }}

        网络: {{ network }}
    </ul>
     
</div>
</template>

<script>
import Box from '3box'
 
export default {
        data(){
            return{
                address: "未登录",
                addressText: "未登录",
                loginText: "钱包登录",
                network: "未连接",
            }
        },
        created: function(){
             this.connect()
             this.getNet() // 网络类型
        },
        methods:{
            async connect(){
                 // 1. 先连接钱包 获得地址
                let accounts = await window.ethereum.request({ method: 'eth_requestAccounts' })
                console.log("获得地址", accounts[0])
                this.address = accounts[0]
                this.addressText = this.address.substring(0, 6) + "..." + this.address.substring(this.address.length - 6)
                this.loginText = "已登录"
            },
            async login(){
                this.connect()
                //  2. 用户初次使用没有： proof_did ， 为地址创建Box身份， 获得proof_did
                this.box = await Box.openBox(this.address, window.ethereum)
                this.box.syncDone
                console.log(this.box)
                
            },
            async create(){
                // 1. 先连接钱包 获得地址
                this.connect()
                // 2. 用户初次使用没有： proof_did ， 为地址创建Box 身份， 获得proof_did
                this.box = await Box.openBox(this.address, window.ethereum)
                this.box.syncDone
                console.log(this.box)
            },
            getNet() {
             // 查询网络类型
            let net = window.ethereum.chainId
            console.log(net)
                        if(net == "0x1"){
                            this.network = "以太坊主网"
                        }else if(net == "0x2"){
                            this.network = "Expanse mainnet"
                        }else if(net == "0x3"){
                            this.network = "Ropsten 测试网"
                        }else if(net == "0x3"){
                            this.network = "Ropsten 测试网"
                        }else if(net == "0x4"){
                            this.network = "Rinkeby 测试网"
                        }else if(net == "0x5"){
                            this.network = "Goerli 测试网"
                        }else if(net == "0x2a"){
                            this.network = "Kovan 测试网"
                        }
            },
        }
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
        display: inline-block;
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
