<template>
  <div class="col-sm-6 ndy-tree">
    <div class="row whit">
      <h4 class="text-center"><b>单位及分组</b></h4>
    </div>
    <ul id="treeDemo" class="ztree" style="margin: 0 auto;"></ul>
  </div>
</template>
<style>
  @import "../assets/zTreeBootstrap/bootstrapStyle.css";
</style>
<script>
//  tree树状图
  import ztree from '../assets/zTreeBootstrap/jquery.ztree.core'
  import excheck from '../assets/zTreeBootstrap/jquery.ztree.excheck'
  import exedit from '../assets/zTreeBootstrap/jquery.ztree.exedit'
  export default {
    name: 'Edtree',
    data: function () {
      return {
        /**
         * 数据解析
         * @ type {[null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null,null]}
         * @ 父级id == 子级pId  则为同类别属性
         * @ name： 内容
         * @ open: true  默认打开  false  默认合并
         */
        zNodes:[
          {id:1, pId:0, name:"后台资源", open:true},
          {id:101, pId:1, name:"单位1", open:true},
              {id:201, pId:101, name:"单位"},
                  {id:2011, pId:201, name:"单位"},
                  {id:2012, pId:201, name:"单位"},
                  {id:2013, pId:201, name:"单位"},
                  {id:2014, pId:201, name:"单位"},
              {id:202, pId:101, name:"单位"},
                  {id:2021, pId:202, name:"单位"},
                  {id:2022, pId:202, name:"单位"},
                  {id:2023, pId:202, name:"单位"},
                  {id:2024, pId:202, name:"单位"},
              {id:203, pId:101, name:"单位"},
                  {id:2031, pId:203, name:"单位"},
                  {id:2032, pId:203, name:"单位"},
                  {id:2033, pId:203, name:"单位"},
                  {id:2034, pId:203, name:"单位"},
              {id:204, pId:101, name:"单位"},
                  {id:2041, pId:204, name:"单位"},
                  {id:2042, pId:204, name:"单位"},
                  {id:2043, pId:204, name:"单位"},
                  {id:2044, pId:204, name:"单位"},
          {id:102, pId:1, name:"单位2", open:false},
              {id:301, pId:102, name:"单位"},
              {id:302, pId:102, name:"单位"},
              {id:303, pId:102, name:"单位"},
              {id:304, pId:102, name:"单位"},
          {id:103, pId:1, name:"单位3", open:false},
              {id:401, pId:103, name:"单位"},
              {id:402, pId:103, name:"单位"},
              {id:403, pId:103, name:"单位"},
              {id:404, pId:103, name:"单位"},
          {id:104, pId:1, name:"单位4", open:false},
              {id:501, pId:104, name:"单位"},
              {id:502, pId:104, name:"单位"},
              {id:503, pId:104, name:"单位"},
              {id:504, pId:104, name:"单位"},
        ],
        /**
         * 创建实例
         */
        setting:{
          view: {
              addHoverDom: false,
              removeHoverDom: false,
              selectedMulti: false
          },
          check: {
            enable: true
          },
          data: {
            simpleData: {
              enable: true
            }
          },
          edit: {
            enable: true
          }
        }
      }
    },
    mounted: function () {
      var _this = this;
      /**
       * 调用实例
       */
      _this.init($("#treeDemo"), _this.setting, _this.zNodes);
    },
    methods: {
      /**
       * 封装实体
       * @param el
       * @param setting
       * @param znodes
       */
      init(el, setting, znodes){
        $.fn.zTree.init(el, setting, znodes);
      }
    }
  }
</script>
<style>
  .ndy-tree{
    width: 100%;
    min-height: 990px;
    background-color: #fff;
    border-radius: 5px;
  }

</style>
