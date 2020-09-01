<template>
    <div class="cov">
        <el-form :model="ruleForm" status-icon ref="ruleForm" label-width="100px" >
            <el-form-item label="网站名称" prop="name">
                <el-input v-model="ruleForm.webName" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="网站地址" prop="url">
                <el-input v-model="ruleForm.webUrl" autocomplete="off"></el-input>
            </el-form-item>
            <el-form-item label="网站标签" prop="tag">
                <el-input v-model="ruleForm.webTag"></el-input>
            </el-form-item>
            <el-form-item>
                <el-button type="primary" @click="submitForm('ruleForm')">提交</el-button>
                <el-button @click="resetForm()">重置</el-button>
            </el-form-item>
                <!-- <el-button @click="SaveTag3Box('漫画')">test</el-button> -->
                
        </el-form>
    </div>
</template>
<script>
import Box from '3box';
 export default {
    data() {
      return {
        ruleForm: {
          webName: '',
          webUrl: '',
          webTag: ''
        }
      };
    },
    props: ['address'],
    methods: {
      submitForm(formName) {
        this.$refs[formName].validate((valid) => {
          if (valid) {
            console.log("网站", this.ruleForm.webName)
            console.log("网址", this.ruleForm.webUrl)
            console.log("标签", this.ruleForm.webTag)
            let spaceName = this.ruleForm.webTag
            let DataKey = this.ruleForm.webName
            let DataValue = this.ruleForm.webUrl
            this.SaveTo3Box(spaceName, DataKey, DataValue)
            alert('写入比较慢，请等待提交!');
          } else {
            console.log('提交出错！');
            return false;
          }
        });
      },
      resetForm() {
        console.log("重置")
        this.ruleForm.webName = ""
        this.ruleForm.webUrl = ""
        this.ruleForm.webTag = ""
      },
    async SaveTo3Box(spaceName, DataKey, DataValue){

        this.SaveTag3Box(spaceName)
        // For MetaMask the user must give permission for application.
        let publicAddress = "0x7F9d6ba73aD4c7B239c771C9EAcC5F4E4f13baCE"
        // const accounts = await window.ethereum.enable();
        console.log('account: ' + publicAddress)
        // Open account 3Box. Will require user to sign via MetaMask.
        const box = await Box.openBox(publicAddress, window.ethereum);
        box.syncDone
        console.log('Opening space: ' + spaceName)
        // Open app space - where the data will be stored (public space). Will require user to sign via MetaMask.
        const space = await box.openSpace(spaceName);
        // Wait for 3Box to sync.
        await space.syncDone;
        console.log('Opened');
        console.log('Saving...');
        // Save the data.
        await space.public.set(DataKey, DataValue);
        console.log('Saved')
        console.log('space', space);
        this.ReadFrom3Box(spaceName);
        console.log("提交成功！")
        alert("提交成功！")
       
    },
    async SaveTag3Box(newTage) {
         
        let publicAddress = "0x7F9d6ba73aD4c7B239c771C9EAcC5F4E4f13baCE"
        const box = await Box.openBox(publicAddress, window.ethereum);
        const space = await box.openSpace("tags");
        console.log("newTage", newTage)
        console.log("Tag space", space)
        await space.syncDone;
        console.log('Opened Tag');
        console.log('Saving Tag...');
        // Save the data.
        await space.public.set(newTage, "0");  // 0 级标签
        console.log('Saved')
    },
    async ReadFrom3Box(tag){
            //  2. 获得  信息 
            const spaceData = await Box.getSpace(this.address, tag)
            console.log(spaceData)
            const box = await Box.openBox(this.address, window.ethereum)
            box.syncDone
            console.log(box)
    },
    }
  }
</script>
<style scoped>
.cov{
      margin: 0px auto;
      background: #eee;
      z-index: 1000;
      text-align: center;
    }
    /*设置弹窗内容*/
    .cov .con {
        background-color: #eee(250, 188, 199, 0.76);
        border-radius: 5px;
        padding: 1.5rem;
        position: relative;
    }
    .bott
    {
      margin: 0px auto;
    }
    .el-form-item {
        margin-bottom: 22px;
        margin-left: 0px;
        text-align: left;
    }
    .el-form-item__label{
      text-align: left;
    }
</style>