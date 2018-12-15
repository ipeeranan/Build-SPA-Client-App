<template>
    <div>
        <h1>Orders List</h1>
        <b-table striped hover 
        :items="order" 
        :fields="fields" 
        :per-page="pageSize" 
        :current-page="pageIndex"></b-table>
        <b-pagination size="md" :total-rows="order.length" v-model="pageIndex" :per-page="pageSize">
    </b-pagination>
    </div>
</template>
<script>
import axios from 'axios'
export default {
  name: 'orders',
  data(){
      return {
          message:'Project 2',
          order: [],
          pageSize: 10,
          pageIndex: 1,
          fields: [ 
              {key:'order_id',sortable : true},
              {key:'customer_id',sortable : true},
              {key:'employee_id', sortable : true,variant: 'danger'}
        ],
      }
  },
  mounted(){
      var instance = this
      axios
      .get('https://glacial-garden-24455.herokuapp.com/api/orders/')
      .then(function(response){
          console.log(response.data)
          instance.order = response.data.data
      })
  }
}
</script>
