<template>
  <row>
    <div class="col-md-4">
      <ma-illist :datas="textdata"></ma-illist>
    </div>
    <div class="col-md-8">
      <va-direct-chat
        theme="primary"
        :talkList="talkList"
        :contacts="contacts"
        title="短信来往"
        :badgeCount="30"
        placeholder=""
      ></va-direct-chat>
    </div>
  </row>
</template>

<script>

  import VADirectChat from '../widgets/VADirectChat.vue'
  //用户列表
  import Maillist from '../maillist/Maillist.vue'
  export default {
      // name: 'sms-chat-record',
    data () {
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
        textdata: "短信来源"
      }
    },
    components: {
      'va-direct-chat': VADirectChat,
      'ma-illist': Maillist
    }
  }
</script>

<style>

</style>
