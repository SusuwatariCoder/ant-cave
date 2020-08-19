<template>
<div class="table">
    <table>
        <tr class="head">
            <td>时间</td>
            <td>ID</td>
            <td>网址</td>
            <td>时间</td>
        </tr>
        <tr class="odd">
            <td id="time">
                2016-05-02
            </td>
            <td>王小虎</td>
            <td>上海市普陀区金沙江路 1518 弄</td>
            <td>访问</td>
        </tr>
        <tr class="even">
            <td>2</td>
            <td>teemo</td>
            <td>320</td>
            <td>76</td>
        </tr>
        <tr class="odd">
            <td>3</td>
            <td>annie</td>
            <td>380</td>
            <td>38</td>
        </tr>
        <tr class="even">
            <td>4</td>
            <td>deadbrother</td>
            <td>400</td>
            <td>90</td>
        </tr>
                <div >
        <img src="../assets/one.gif" alt="#">
    </div>
    </table>

</div>

</template>

<script>
    export default {


    }
</script>

<style scoped>
    table {
        border-collapse: collapse;
        height: 100px;
        width: 100%;
        border: 250px solid #ffffff;
        border-top: 3px solid rgb(16, 217, 243);
        border-bottom: 0px;
        margin: 0 auto;
        padding: 0px 0px 0px 0px;

    }
    
    tr.odd {
        background-color: #f8f8f8;
    }
    
    tr.head {
        border-bottom-width: 2px;
    }
    
    tr {
        border-bottom-style: solid;
        border: 20px;
        border-bottom-color: lightgray;
        height: 80px;
    }
    
    td {
        width: 25%;
        text-align: center;
    }

     img {
        display: block;
        position: absolute;
        z-index: 1;
        float: right;
        border-radius: 25px;
        /* padding:8px 30px 8px 200px; */
        top:700px;
        padding: 0px 0px 0px 950px;
        width: 200px;
        height: 150px;
        
    }
</style>
