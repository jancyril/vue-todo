<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1>Todo App</h1>
      </div>
      <div class="col-12">
        <TableComponent :items="items"></TableComponent>
      </div>
    </div>
    <FormComponent @itemSubmitted="save"></FormComponent>
  </div>
</template>

<style>
  .complete {
    text-decoration: line-through;
  }
</style>

<script>
import FormComponent from './components/FormComponent'
import TableComponent from './components/TableComponent'

export default {
  name: 'App',

  components: {
    FormComponent,
    TableComponent
  },

  data() {
    return {
      items: []
    };
  },

  methods: {
    save(contents) {

      let newItem = {
        text: contents,
        done: false
      };

      this.items.push(newItem);
    }
  }
};
</script>
