<template>
  <row>
    <row>
      <div class='col-md-3'>
        <va-info-box
          bgColor='bg-aqua'
          bgIcon='ion ion-ios-gear-outline'
          text='Hello'
          number='8700'
        ></va-info-box>
      </div>
      <div class='col-md-3'>
        <va-info-box
          bgColor='bg-red'
          bgIcon='fa fa-google-plus'
          text='LIKES'
          number='232323'
          number-type='percentage'
        ></va-info-box>
      </div>
      <div class='col-md-3'>
        <va-info-box
          bgColor='bg-green'
          bgIcon='ion ion-ios-cart-outline'
          text='SALES'
          number='580'
        ></va-info-box>
      </div>
      <div class='col-md-3'>
        <va-info-box
          bgColor='bg-yellow'
          bgIcon='ion ion-ios-people-outline'
          text='new members'
          number='580'
          number-type='comma'
        ></va-info-box>
      </div>
    </row>
    <row>
      <div class="container-fluid">
        <section class="col-ls-4 col-sm-4 connectedSortable ui-sortable">
          <ed-tree></ed-tree>
        </section>
        <section class="col-ls-8 col-sm-8 connectedSortable ui-sortable">
          <va-direct-chat
            theme="primary"
            :talkList="talkList"
            :contacts="contacts"
            title="发送短信"
            :badgeCount="30"
            placeholder=""
          ></va-direct-chat>
        </section>
      </div>

    </row>
  </row>

</template>
<script>
import VAInfoBox from '../widgets/VAInfoBox'
//分组/单位
import Edtree from '../maillist/Edtree.vue'
//发送短信
import VADirectChat from '../widgets/VADirectChat.vue'

export default {
  components: {
    'va-info-box': VAInfoBox,
    'ed-tree': Edtree,
    'va-direct-chat': VADirectChat
  },
  data(){
    return {
      talkList: [
        {
          name: 'Alexander Pierce',
          date: new Date(),
          profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
          message: `Is this template really for free? That's unbelievable`,
          isMine: false
        },
        {
          name: 'Sarah Bullock',
          date: new Date(),
          profileImage: 'http://cfile9.uf.tistory.com/image/25270C4853F7057D09BFD3',
          message: `You better believe it!`,
          isMine: true
        }
      ],
    }
  }
}
</script>
<style lang="css">
</style>
