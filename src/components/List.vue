<template>
    <div id="list">
        <ul>
          <li v-for="item in items" :class="{'finished':item.isFinished}"
              @mouseover='showDelete(item)' @mouseleave='hideDelete(item)'>
            <input :id="item.num" type="checkbox" v-model="item.isFinished">
            <label :for="item.num">{{ item.label }}</label>
            <transition name="fade">
                <span @click="removeItem(item.num)" v-show="item.delete" class="del">delete</span>
            </transition>
          </li>
        </ul>
        <p>{{finished}} / {{total}}</p>
    </div>
</template>

<script>
    export default {
        props: ['items'],
        methods: {
            showDelete (item) {
              item.delete = true;
            },
            hideDelete (item) {
              item.delete = false;
            },
            removeItem (num) {
              this.$emit("removeItem", num);
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

<style>
    .fade-enter-active, .fade-leave-active {
        transition: all .3s ease;
        opacity: 1;
    }
    .fade-enter, .fade-leave-active {
        opacity: 0;
    }

    ul {
      list-style-type: none;
      padding: 0;
      text-align: left;
    }

    li {
      /*display: inline-block;*/
      margin: 0 10px;
      padding: 5px;
      border-top: 1px #ccc solid;
    }
    li:first-child {
        border-top: 0;
    }
    .del {
        float: right;
    }
    .del::after {
        content: '';
        clear:both;
    }
</style>