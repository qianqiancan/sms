<template>
  <div class="col-lg-12 col-sm-12 box ndy-table">
    <div class="row whit">
      <h4 class="text-center"><b>用户详情</b></h4>
    </div>
    <form action="">
      <table class="table table-bordered">
        <tbody>
          <tr>
            <td class="ndy-td col-ls-2 col-sm-2">所在单位</td>
            <td :contenteditable="msg" class="ndy-text-ta col-ls-10 col-sm-10" :class="{'bg-info': msg}">{{datas.edit ? datas.edit : ""}}</td>
          </tr>
          <tr>
            <td class="ndy-td col-ls-2 col-sm-2">用户名</td>
            <td :contenteditable="msg" class="ndy-text-ta col-ls-10 col-sm-10" :class="{'bg-info': msg}">{{datas.name ? datas.name : ""}}</td>
          </tr>
          <tr>
            <td class="ndy-td col-ls-2 col-sm-2">手机号</td>
            <td :contenteditable="msg" class="ndy-text-ta col-ls-10 col-sm-10" :class="{'bg-info': msg}">{{datas.iphone ? datas.iphone : ""}}</td>
          </tr>
        </tbody>
      </table>

      <row>
        <div class="col-ls-1 col-sm-1">
          <input type="button" value="保存" class="btn btn-success" @click="btn_edit(false)">
        </div>
        <div class="col-ls-1 col-sm-1">
          <input type="button" value="编辑" class="btn btn-primary" @click="btn_edit(true)">
        </div>
      </row>
    </form>
  </div>
</template>
<script>
  export default {
    name: 'Details',
    props:{
      datas: ""
    },
    data(){
      return {
        msg: false
      }
    },
    methods: {
      //编辑触发事件
      btn_edit(status){
        if(status){
          this.msg = status;
        }else{
          this.msg = status;
        }

      }
    }

  }
</script>
<style>
  .ndy-table{
    padding-bottom: 20px;
  }
  .ndy-td{
    text-align: justify;
  }
  .ndy-text-ta{
    max-width: 100%;
    word-wrap:break-word;
    word-break:break-all;
    white-space:pre-wrap;
  }
</style>
