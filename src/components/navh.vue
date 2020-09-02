<template>
<div class="nav">
    <ul>    
            <img src="../assets/faucet.gif" alt="#">
            <a v-show="protocol" href="https://ant-cave.vercel.app/"> (由于安全协议，请点击跳转线上版本) </a>
            <p class="yi">蚁穴</p>
           
        <li @click="login" class="login">
            <a v-if="logined==false" class="el-icon-s-home" href="#">{{ loginText }}</a>
            <a v-else class="el-icon-s-home" href="#">{{ addressText }} </a>

            </li>
        <li @click="create" class="Registration">
            <!-- 使用说明 https://element.eleme.cn/#/zh-CN/component/icon -->
            <a v-if="logined==false" class="el-icon-edit" href="#"> 创建身份 </a>
            <a v-else class="el-icon-edit" href="#">网络: {{ network }}</a>
            </li>
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
                logined: false,
                protocol: true,
            }
        },
        created: function(){
             this.connect()
             if(window.location.protocol == "http:"){
                 this.protocol = true
             }else{
                 this.protocol = false
             }
        },
        methods:{
            async connect(){
                 // 1. 先连接钱包 获得地址
                let accounts = await window.ethereum.request({ method: 'eth_requestAccounts' })
                console.log("获得地址", accounts[0])
                this.address = accounts[0]
                this.addressText = this.address.substring(0, 4) + "..." + this.address.substring(this.address.length - 6)
                this.loginText = "已登录"
                this.getNet() // 网络类型
                this.logined = true
                this.sendDataToParent()
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
            sendDataToParent(){
                //$emit（even,value）even 是一个函数，value 是传给父组件的值
                this.$emit('userAddress', this.address)
            }

 
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
        font-size: 20px;
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
        width: 150px;
        margin: 0px;
        padding: 10px 0px 10px 0px;

        right: 450px;
    }
    .Registration a{
        position: absolute;
        margin:0px;
        width: 200px;
        padding: 10px 0px 10px 0px;
        right: 250px;
    }

    li a:hover {
        color:#EBEDEF;
    }
</style>
