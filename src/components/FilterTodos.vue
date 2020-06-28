<template>
   <section class="section">
      <div class="container">
         <div class="columns is-mobile">
            <div class="column">
               <span class="incomplete-box"></span> = Incomplete
            </div>
            <div class="column">
               <span class="complete-box"></span> = Complete
            </div>
            <div class="column">
               <div class="select is-small">
                  <select @change="filterTodos($event)">
                     <option value="200">200</option>
                     <option value="100">100</option>
                     <option value="50">50</option>
                     <option value="20">20</option>
                     <option value="10">10</option>
                     <option value="5">5</option>
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
