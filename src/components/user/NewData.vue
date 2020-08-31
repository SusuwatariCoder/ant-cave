<template>
    <div>
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
                <el-button @click="resetForm('ruleForm')">重置</el-button>
            </el-form-item>
                <el-button @click="ReadFrom3Box">浏览更多</el-button>
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
            alert('提交!');
            console.log("网站", this.ruleForm.webName)
            console.log("网址", this.ruleForm.webUrl)
            console.log("标签", this.ruleForm.webTag)
            let spaceName = this.ruleForm.webTag
            let DataKey = this.ruleForm.webName
            let DataValue = this.ruleForm.webUrl
            this.SaveTo3Box(spaceName, DataKey, DataValue)
          } else {
            console.log('提交出错！');
            return false;
          }
        });
      },
      resetForm(formName) {
        this.$refs[formName].resetFields();
      },
    async SaveTo3Box(spaceName, DataKey, DataValue){
        // For MetaMask the user must give permission for application.
        const accounts = await window.ethereum.enable();
        console.log('account: ' + accounts[0])
        // Open account 3Box. Will require user to sign via MetaMask.
        const box = await Box.openBox(accounts[0], window.ethereum);
        box.syncDone
        console.log('Opening Tag space: ' + spaceName)
        // Open app space - where the data will be stored (public space). Will require user to sign via MetaMask.
        const space = await box.openSpace(spaceName);
        // Wait for 3Box to sync.
        await space.syncDone;
        console.log('Opened');
        console.log('Saving...');
        // Save the data.
        await space.public.set(DataKey, DataValue);
        console.log('Saved')
    },

    async ReadFrom3Box(){
            //  2. 获得  信息 
            const spaceData = await Box.getSpace(this.address, '搜索引擎')
            console.log(spaceData)
            const box = await Box.openBox(this.address, window.ethereum)
            box.syncDone
            console.log(box)
    },
    }
  }
</script>
<style scoped>

</style>