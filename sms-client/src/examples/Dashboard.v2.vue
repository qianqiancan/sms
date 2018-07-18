<template>
  <div class="dashboard">

    <row>
      <section class="col-lg-4 connectedSortable ui-sortable">
        <ed-tree></ed-tree>
      </section>
      <div class="col-lg-8">
        <row>
          <section class="col-lg-12 connectedSortable ui-sortable">
            <de-tails :datas="getContent"></de-tails>
          </section>
        </row>
        <row>
            <ma-illist @edit-obj="receiveObj" :datas="textdata"></ma-illist>
        </row>
      </div>
    </row>
  </div>
</template>

<script>
  //分组/单位
  import Edtree from '../maillist/Edtree.vue'
  //用户列表
  import Maillist from '../maillist/Maillist.vue'
  //用户详情
  import Details from '../maillist/details.vue'
  export default {
    name: 'dashboard',
    data () {
      return {
          textdata: "编辑",
          getContent: {
            edit: "单位名称",
            name: "用户名",
            iphone: "手机号"
          }
      }
    },
    methods: {
      receiveObj(obj){
        this.getContent = obj;
        console.log('我是父组件obj==>', this._getContent);
      }
    },
    components: {
      'de-tails': Details,
      'ed-tree': Edtree,
      'ma-illist': Maillist
    }
  }

</script>
