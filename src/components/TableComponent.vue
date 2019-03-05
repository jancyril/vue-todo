<template>
  <table class="table table-striped table-bordered table-hover">
    <thead class="thead-dark">
      <th>Item</th>
      <th class="text-right">Actions</th>
    </thead>
    <tbody>
      <tr v-for="(item, index) in items" :key="index">
        <td>
          <span :class="{complete: item.done}">{{ item.text }}</span>
        </td>
        <td class="text-right">
          <a
            href="#"
            @click.prevent="markAsComplete(index)"
            class="text-success"
            v-show="!item.done"
          >Mark as Complete</a>
          <a
            href="#"
            @click.prevent="markAsIncomplete(index)"
            class="text-primary"
            v-show="item.done"
          >Mark as Incomplete</a>
          <a href="#" @click.prevent="deleteItem(index)" class="text-danger">Delete</a>
        </td>
      </tr>
    </tbody>
  </table>
</template>

<script>
export default {
  props: ["items"],

  data() {
    return {
      isComplete: false
    };
  },

  methods: {
    deleteItem(index) {
      this.items.splice(index, 1);
    },

    markAsComplete(index) {
      this.items[index].done = true;
    },

    markAsIncomplete(index) {
      this.items[index].done = false;
    }
  }
};
</script>
