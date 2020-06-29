<template>
   <div class="fixedbottom section">
      <form @submit="onSubmit">
         <div class="field has-addons">
            <div class="control is-expanded">
               <input
                  class="input"
                  type="text"
                  v-model="title"
                  placeholder="What's on your mind?"
               />
            </div>
            <div class="control">
               <button type="submit" value="Submit" class="button is-primary" :class="{'is-loading': isLoading}">
                  <span class="icon">
                     <i class="fas fa-plus"></i>
                  </span>
                  <span>Add</span>
               </button>
            </div>
         </div>
      </form>
   </div>
</template>

<script>
import { mapActions, mapGetters } from "vuex";

export default {
   name: "AddTodo",
   data() {
      return {
         title: "",
      };
   },
   methods: {
      ...mapActions(["addTodo"]),
      onSubmit(e) {
         e.preventDefault();
         this.addTodo(this.title);
         this.title = ''
      },
   },
   computed: mapGetters(["isLoading"])
};
</script>

<style scoped>
.fixedbottom {
   position: fixed;
   bottom: 0;
   width: 100%;
   overflow: hidden;
   background: #fff;
   padding: 1em;
}
</style>
