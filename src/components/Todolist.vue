<template>
  <div class="todolist">
    <h1 v-text='title'></h1>
    <list :items="this.items" @removeItem="removeItem"></list>
    <controller @addItem='addItem'></controller>
  </div>

</template>

<script>
import List from './List';
import Controller from './Controller';

export default {
  data () {
    return {
      title: 'Todo List',
      items: [
        // {
        //   label: this.newItem,
        //   num: this.itemIndex,
        //   isFinished: false,
        //   delete: false
        // }
      ],
      itemIndex: 0
    }
  },
  components: {
    controller: Controller,
    list: List
  },
  methods: {
    addItem (name) {
      this.items.push({
        label: name,
        num: this.itemIndex++,
        isFinished: false,
        delete: false
      });
      this.newItem = '';
    },
    removeItem (num) {
      this.items = this.items.filter(function(i) {
        return !(i.num == num);
      })
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

a {
  color: #42b983;
}
</style>
