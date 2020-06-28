<template>
   <div class="fixedbottom section">
      <form @submit="onSubmit">
         <div class="field has-addons">
            <p class="control is-expanded">
               <input
                  class="input is-fullwidth"
                  type="text"
                  v-model="title"
                  placeholder="What's on your mind?"
               />
            </p>
            <p class="control">
               <input type="submit" value="Submit" class="button is-info" />
            </p>
         </div>
      </form>
   </div>
</template>

<script>
import { mapActions } from "vuex";

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
      },
   },
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
