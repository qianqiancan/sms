<template>
  <div class="col-sm-12">
    <h2 class="text-info">当前分组下的用户<code class="h6 text-danger">*默认显示第一个单位下的用户</code></h2>
    <table class="table table-hover table-striped" style="border: 1px solid #ddd;border-right: 1px solid #ddd; margin-top: 20px;">
      <thead>
      <tr class="whit text-white">
        <th><input type="checkbox" v-on:click="checkBox()">&nbsp;全选</th>
        <th class="text-center">序号</th>
        <th class="text-center">角色名称</th>
        <th class="text-center">手机号</th>
        <th class="text-right">Action</th>
        <th class="text-right">Remove</th>
      </tr>
      </thead>
      <tbody class="font-w">
      <tr v-for="(val,index) in users">
        <td><input type="checkbox" :checked="val.Check" v-model="val.Check"></td>
        <td class="text-center">{{index+1}}</td>
        <td class="text-center">{{val.name}}</td>
        <td class="text-center">{{val.iphone}}</td>
        <td class="text-right"><a href="javascript:;" class="btn btn-success" @click="btn_edit(index)">{{datas}}</a></td>
        <td class="text-right"><a href="javascript:;" class="btn btn-danger" @click="userIndex = index" data-toggle="modal" data-target="#del">删除</a></td>
      </tr>
      <tr>
        <td colspan="7" class="text-right">
          <button class="btn btn-success text-right">添加</button>
          <button type="button" class="btn btn-danger" style="outline: none; border: none;" @click="userIndex = -1"  data-toggle="modal" data-target="#del">删除全部</button>
        </td>
      </tr>
      </tbody>
    </table>
    <div class="row paging clearfix" >
      <div class="clearfix">
        <p class="text-success" style="margin-left: 15px">共<code>1</code>页</p>
        <p class="text-success" style="margin-left: 10px;"><code>10</code>条</p>
      </div>
      <div>
        <div class="container-fluid">
          <ul class="pagination" id="pagination">
            <li><a href="javascript:;">&laquo;</a></li>
            <li class="active pag_li"><a href="#">1</a></li>
            <li class="pag_li"><a href="javascript:;">2</a></li>
            <li class="pag_li"><a href="javascript:;">3</a></li>
            <li class="pag_li"><a href="javascript:;">4</a></li>
            <li class="pag_li"><a href="javascript:;">5</a></li>
            <li><a href="javascript:;">&raquo;</a></li>
          </ul>
        </div>
      </div>
    </div>

    <!--模态框-->
    <div class="modal" id="del">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <button type="button" class="close" data-dismiss="modal">
              &times;
            </button>
            <h4 class="modal-title">
              <b class="text-danger">小心操作，后果自负！</b>
            </h4>
          </div>
          <div class="modal-body">
            <div v-show="userIndex != -1">
              <p>
                <label class="col-sm-2">序号:</label>
                <code>{{users[userIndex] ? userIndex + 1 : ""}}</code>
              </p>
              <p>
                <label class="col-sm-2">角 色:</label>
                <code>{{users[userIndex] ? users[userIndex].name : ""}}</code>
              </p>
              <p>
                <label class="col-sm-2">手机号:</label>
                <code>{{users[userIndex] ? users[userIndex].iphone : ""}}</code>
              </p>
            </div>
            <div v-show="userIndex == -1">
              <p class="text-danger">有必要做的这么绝吗？ 全删了啊！！</p>
            </div>
            <div class="text-center">
              <button type="button" class="btn btn-success" data-dismiss="modal">取消</button>
              <button type="button" class="btn btn-danger" @click="deleteUser()" data-dismiss="modal">确认删除</button>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>


  export default {
    name: 'list',
    props:{
      datas: ""
    },
    data () {
      return {
        /**
         * 将数据返回  数据格式
         */
        users: [
          {edit:"单位111111111",name:"名字111111111",iphone:"13888888888",Check:false},
          {edit:"单位222222222",name:"名字222222222",iphone:"138834645688",Check:false},
          {edit:"单位333333333",name:"名字33333333",iphone:"138823678888",Check:false},
          {edit:"单位444444444",name:"名字44444444",iphone:"1380008888",Check:false},
          {edit:"单位555555555",name:"名字5555555555",iphone:"1382344645888",Check:false},
          {edit:"单位666666666",name:"名字6666666666",iphone:"13889789888",Check:false},
          {edit:"单位777777777",name:"名字777777777",iphone:"3453458888",Check:false},
          {edit:"单位888888888",name:"名字8888888",iphone:"585687568888",Check:false},
          {edit:"单位999999999",name:"名字9999999",iphone:"345345234888",Check:false},
          {edit:"单位100000000",name:"名字10000000",iphone:"546456888",Check:false}
        ],
        chck:false,
        userIndex: -1
      }
    },
    mounted: function () {
      $(function () {
        $("#plaim").on("click","strong",function () {
          $(this).addClass("init").siblings("strong").removeClass("init");
        })
        $("#pagination").on("click",".pag_li",function () {
          $(this).addClass("active").siblings(".pag_li").removeClass("active");
        })
      })
    },
    methods:{
      //全选
      checkBox(){
        var _this = this;
        this.chck = !this.chck;
        this.users.forEach(function (v) {
          if(_this.chck == true){
            v.Check = true
          }else{
            v.Check = false
          }
        })
      },
      //删除、全部删除
      deleteUser(){
        if(this.userIndex == -1){
          this.users = {};
        }else{
          this.users.splice(this.userIndex,1);
        }
      },
      //编辑
      btn_edit(index){
        var _this = this;
        this.$emit('edit-obj',_this.users[index]);
      }

    }
  }




</script>

<style>
  .whit {
    background-color: #2d3f53;
    color: #fff;
  }
  .paging{
    height: 50px;
  }
  .paging > div:nth-of-type(1){
    float: left;
  }
  .paging > div:nth-of-type(2){
    float: right;
  }
  .paging > div:nth-of-type(1) > p{
    float: left;
  }
  .paging > div:nth-of-type(2) span{
    margin-top: 2px;
  }
  .paging > div:nth-of-type(2) span:nth-of-type(1){
    float: left;
    margin-right: 5px;

  }
  .paging > div:nth-of-type(2) span:nth-of-type(2){
    float: right;
    margin-left: 5px;
    margin-right: 15px;
  }
  .paging > div:nth-of-type(2) strong.init{
    box-shadow: 2px 2px 5px rgba(0,0,0,0.5);
    margin-top: -5px;
    transition: all .2s;
    background: #5cb85c;
    border: none;
  }

</style>
