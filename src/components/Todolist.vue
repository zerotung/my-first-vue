<template>
  <div class="todolist">
    <h1 v-text='title'></h1>
    <ul>
      <li v-for="item in items" :class="{'finished':item.isFinished}"
          @mouseover='showDelete(item)' @mouseleave='hideDelete(item)'>
        <input :id="item.num" type="checkbox" v-model="item.isFinished">
        <label :for="item.num">{{ item.label }}</label>
        <span @click="removeItem(item.num)" v-show="item.delete" class="del">delete</span>
      </li>
    </ul>
    <p>{{finished}} / {{total}}</p>
    <input type="text" v-model="newItem" @keyup.enter='addItem' placeholder="Add a new todo">
    <button @click='addItem' >add</button>
  </div>

</template>

<script>
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
      newItem: '',
      itemIndex: 0
    }
  },
  methods: {
    addItem () {
      this.items.push({
        label: this.newItem,
        num: this.itemIndex++,
        isFinished: false,
        delete: false
      });
      this.newItem = '';
    },
    showDelete (item) {
      item.delete = true;
    },
    hideDelete (item) {
      item.delete = false;
    },
    removeItem (num) {
      this.items = this.items.filter(function(i) {
        return !(i.num == num);
      })
    }
  },
  computed: {
    total () {
      return this.items.length;
    },
    finished () {
      return this.items.filter(function(x) {
        return x.isFinished;
      }).length;
    }
  }

}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
  text-align: left;
}

li {
  /*display: inline-block;*/
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
