<template>
  <div class="dashboard">
    <row>
      <section class="col-lg-12 connectedSortable ui-sortable">
        <ma-illist></ma-illist>
      </section>
    </row>
  </div>
</template>

<script>
import Maillist from '../maillist/Maillist.vue'

export default {
  name: 'dashboard',
  data () {
    return {

    }
  },
  methods: {

  },
  components: {
    'ma-illist': Maillist
  }
}

</script>
