<template>
   <section class="section">
      <div class="container">
         <div class="notification is-info" v-show="notice">
         <button class="delete" @click="notice=false"></button>
         This is just a vue.js + vuex frontend demo. The data you entered will not persist as this is connected to a <a href="https://jsonplaceholder.typicode.com/" target="_blank">mock backend</a>.
         </div>
         <h1 class="is-size-1 has-text-weight-medium">Todos</h1>
         <div class="columns is-mobile">
            <div class="column">
               <span class="incomplete-box"></span> Incomplete<br>
               <span class="complete-box"></span> Complete
            </div>
            <div class="column has-text-right">
               <div class="select is-small">
                  <select @change="filterTodos($event)">
                     <option value="0">-</option>
                     <option value="5">5</option>
                     <option value="10">10</option>
                     <option value="20">20</option>
                     <option value="50">50</option>
                     <option value="100">100</option>
                  </select>
               </div>
            </div>
         </div>
      </div>
   </section>
</template>

<script>
import { mapActions } from "vuex";
export default {
   name: "FilterTodos",
   methods: {
      ...mapActions(["filterTodos"]),
   },
   data(){
      return {
         notice: true
      }
   }
};
</script>

<style scoped>
.legend {
   display: flex;
   justify-content: space-around;
   margin-bottom: 1rem;
}
.complete-box {
   display: inline-block;
   width: 10px;
   height: 10px;
   background: #35495e;
}
.incomplete-box {
   display: inline-block;
   width: 10px;
   height: 10px;
   background: #41b883;
}
</style>
