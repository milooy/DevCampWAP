<template lang="html">
  <section>
    <ul v-if="passedData">
      <transition-group name="list" tag="div">
        <li v-for="(todoItem, index) in passedData" :key="todoItem" class="shadow">
          <i class="checkBtn fa fa-check" aria-hidden="true"></i>
          {{ todoItem }}
          <span class="removeBtn" type="button" @click="removeTodo(todoItem, index)">
            <i class="fa fa-trash-o" aria-hidden="true"></i>
          </span>
        </li>
      </transition-group>
    </ul>
  </section>
</template>

<script>
export default {
  props: ['passedData'],
  methods: {
    removeTodo(todoItem, index) {
      this.$emit('removeTodo', todoItem, index);
    }
  }
}
</script>

<style lang="css">
ul {
  list-style-type: none;
  padding-left: 0px;
  text-align: left;
  margin: 1.5rem 0;
}
li {
  display: flex;
  min-height: 50px;
  height: 50px;
  line-height: 50px;
  margin: 0.5rem 0;
  padding: 0 0.9rem;
  background: white;
}
.checkBtn {
  line-height: 45px;
  color: #62acde;
  margin-right: 5px;
}
.removeBtn {
  margin-left: auto;
  color: #de4343;
}

/* transition effect */
.list-item {
  display: inline-block;
  margin-right: 10px;
}
.list-enter-active, .list-leave-active {
  transition: all 1s;
}
.list-enter, .list-leave-to /* .list-leave-active for <2.1.8 */ {
  opacity: 0;
  transform: translateY(30px);
}
</style>
