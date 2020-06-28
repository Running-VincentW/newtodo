<template>
   <section class="section pt-0">
      <div class="container">
         <div class="todos">
            <div
               v-for="todo in allTodos"
               :key="todo.id"
               class="card todo has-text-white"
               @contextmenu="updateCompleted($event, todo)"
               :class="{ 'is-complete': todo.completed }"
            >
               <div class="card-content">
                  <div class="content">
                     <span
                        v-if="todo.id !== updateId"
                        @click="editTitle(todo)"
                        >{{ todo.title }}</span
                     >
                     <form v-else @submit.prevent="updateTodoTitle(todo)">
                        <input
                           type="text"
                           v-model="updateText"
                           placeholder="update"
                           ref="titleField"
                           class="input is-focused"
                        />
                        <input type="submit" value="Submit" hidden="true" />
                     </form>
                  </div>
                  <p class="buttons is-right">
                     <button @click="deleteTodo(todo.id)" class="button">
                        <span class="icon is-small">
                           <i class="fas fa-trash-alt"></i>
                        </span>
                     </button>
                     <button
                        @click="updateCompleted($event, todo)"
                        class="button"
                     >
                        <span class="icon is-small">
                           <i class="fas fa-check"></i>
                        </span>
                     </button>
                  </p>
               </div>
            </div>
         </div>
      </div>
   </section>
</template>

<script>
import { mapGetters, mapActions } from "vuex";

export default {
   name: "Todos",
   data() {
      return {
         updateId: -1,
         updateText: "",
      };
   },
   methods: {
      ...mapActions(["fetchTodos", "deleteTodo", "updateTodo"]),
      updateCompleted(e, todo) {
         e.preventDefault();
         const updTodo = {
            id: todo.id,
            title: todo.title,
            completed: !todo.completed,
         };
         this.updateTodo(updTodo);
      },
      updateTodoTitle(todo) {
         this.updateId = -1;
         const updTodo = {
            id: todo.id,
            title: this.updateText,
            completed: todo.completed,
         };
         this.updateTodo(updTodo);
      },
      editTitle(todo) {
         // console.log("updating id: " + todo.id);
         this.updateId = todo.id;
         this.updateText = todo.title;
         this.$nextTick(function() {
            this.$refs.titleField[0].focus();
         });
      },
   },
   computed: mapGetters(["allTodos"]),
   created() {
      this.fetchTodos();
   },
};
</script>

<style scoped>
.todos {
   display: grid;
   grid-template-columns: repeat(3, 1fr);
   grid-gap: 1rem;
}
.todo {
   border: 1px solid #ccc;
   background: #41b883;
   /* padding: 1rem; */
   border-radius: 5px;
   cursor: pointer;
}

.is-complete {
   background: #35495e;
   color: #fff;
}
@media (max-width: 500px) {
   .todos {
      grid-template-columns: 1fr;
   }
}
</style>
