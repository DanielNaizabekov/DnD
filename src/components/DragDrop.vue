<template>
  <div class="drag-drop-wrapper">
    <!-- ====first block==== -->
    <div class="first-block">
      <draggable
        v-model="list"
        class="list-wrapper"
        tag="ul"
        ghost-class="list-item-ghost"
        :disabled="isDisabled"
        @start="start"
        @end="end"
        @change="change"
      >
        <li
          class="list-item"
          v-for="item in list"
          :key="item.id"
        >
          {{ item.name }}
        </li>
      </draggable>

      <div class="checkbox-wrapper">
        <input @change="isDisabled = !isDisabled" id="checkbox" type="checkbox">
        <label class="checkbox-label" for="checkbox">Disable DnD</label>
      </div>
    </div>
    <!-- ====first block==== -->

    <div class="divider"></div>

    <!-- ====second block==== -->
    <div class="second-block">
      <draggable
        class="list-wrapper"
        :class="{empty: !list1.length}"
        tag="ul"
        ghost-class="list-item-ghost"
        :list="list1"
        :group="{name: 'second-block', pull: 'clone', put: false}"
      >
        <li
          class="list-item"
          v-for="item in list1"
          :key="item.id"
        >
          {{ item.name }}
        </li>
      </draggable>

      <draggable
        class="list-wrapper"
        :class="{empty: !list2.length}"
        tag="ul"
        ghost-class="list-item-ghost"
        :list="list2"
        :group="{name: 'second-block', pull: 'clone'}"
      >
        <li
          class="list-item"
          v-for="item in list2"
          :key="item.id"
        >
          {{ item.name }}
        </li>
      </draggable>

      <draggable
        class="list-wrapper"
        :class="{empty: !list3.length}"
        tag="ul"
        ghost-class="list-item-ghost"
        :list="list3"
        group="second-block"
      >
        <li
          class="list-item"
          v-for="item in list3"
          :key="item.id"
        >
          {{ item.name }}
        </li>
      </draggable>
    </div>
    <!-- ====second block==== -->

    <div class="divider"></div>

    <!-- ====thirth block==== -->
    <div class="thirth-block">
      <draggable
        class="list-wrapper"
        tag="ul"
        ghost-class="list-item-ghost"
        v-model="list4"
        handle=".handle"
      >
        <li
          class="list-item list-handle-item"
          v-for="item in list4"
          :key="item.id"
        >
          <img class="handle handle-img" src="https://img.icons8.com/material-two-tone/24/000000/menu.png"/>
          {{ item.name }}
        </li>
      </draggable>

      <draggable
        class="list-wrapper"
        v-model="list4"
        v-bind="dragOptions"
      >
        <li
          class="list-item list-handle-item"
          v-for="item in list4"
          :key="item.id"
        >
          <img class="handle handle-img" src="https://img.icons8.com/material-two-tone/24/000000/menu.png"/>
          {{ item.name }}
        </li>
      </draggable>
    </div>
    <!-- ====thirth block==== -->
  </div>
</template>

<script>
import draggable from "vuedraggable";

export default {
  components: { draggable },
  data() {
    return {
      isDisabled: false,
      list: [
        {name: 'Daniel', id: 45},
        {name: 'Mike', id: 41},
        {name: 'John', id: 21},
      ],
      list1: [
        {name: 'Katy', id: 15},
        {name: 'Sam', id: 22},
        {name: 'Doe', id: 40},
      ],
      list2: [
        {name: 'Samsung', id: 16},
        {name: 'Apple', id: 23},
        {name: 'Sony', id: 39},
      ],
      list3: [
        {name: 'Amazon', id: 17},
        {name: 'Uber', id: 24},
        {name: 'Facebook', id: 38},
      ],
      list4: [
        {name: 'Amazon', id: 17},
        {name: 'Uber', id: 24},
        {name: 'Facebook', id: 38},
      ],
    };
  },
  computed: {
    dragOptions() {
      return {
        animation: 200,
        ghostClass: "list-item-ghost",
        tag: 'ul',
        handle: '.handle',
      };
    },
  },
  methods: {
    start() {
      console.log('start');
    },
    end() {
      console.log('end');
    },
    change() {
      console.log('change');
    },
  },
}
</script>

<style scoped>
.divider {
  height: 1px;
  width: 100%;
  background: #000;
  margin: 15px 0 15px 0;
}
.empty {
  border: 1px dashed #000;
  min-height: 100px;
}

.list-wrapper {
  width: 200px;
}
.list-item {
  padding: 12px;
  border: 1px solid #ccc;
  background: #fff;
  margin-bottom: -1px;
  cursor: move;
  font-size: 14px;
}
.list-item-ghost {
  background: #e0e1f0;
}
.list-item:first-child {
  border-top-left-radius: 3px;
  border-top-right-radius: 3px;
}
.list-item:last-child {
  margin: 0;
  border-bottom-left-radius: 3px;
  border-bottom-right-radius: 3px;
}

.checkbox-wrapper {
  margin-top: 5px;
}
.checkbox-label {
  font-size: 13px;
}


.second-block,
.thirth-block {
  display: flex;
  align-items: flex-start;
}
.second-block .list-wrapper,
.thirth-block .list-wrapper {
  margin-right: 15px;
}

.list-handle-item {
  display: flex;
  align-items: center;
  cursor: default;
}
.handle-img {
  margin-right: 10px;
  cursor: move;
}
</style>