<template>
  <section>
    <div class="form-container">
      <h2>My Shopping List App</h2>
      <form @submit.prevent="addItem">
        <div>
          <label> Product Name</label>
          <br />
          <input v-model="state.input" type="text" />
        </div>

        <div>
          <button type="submit" class="submit">Add Item</button>
        </div>
      </form>
    </div>
    <div class="list-container">
      <ul v-for="(Item,index) in state.Items" :key="index">
        <li>
          {{Item}}
          <span style="float:right;padding-right:10px;">
            <button @click="removeItem(index)">X</button>
          </span>
        </li>
      </ul>
    </div>
  </section>
</template>
<script>
import { reactive } from "@vue/composition-api";
export default {
  setup() {
    const { state, addItem, removeItem } = ItemList();
    return { state, addItem, removeItem };
  }
};
function ItemList() {
  let state = reactive({
    input: "",
    Items: ["Grocery"]
  });
  let addItem = () => {
    state.Items.push(state.input);
    state.input = "";
  };
  let removeItem = i => {
    state.Items.splice(i, 1);
  };
  return { state, addItem, removeItem };
}
</script>

<style scoped>
input {
  width: 20%;
  height: 30px;
  border: 2px solid rgb(201, 138, 22);
}
.submit {
  margin: 10px;
  padding: 10px;
  border-radius: 0px;
  border: 0px;
  background: #2962ff;
  color: white;
}
ul li {
  list-style: none;
  border: 1px solid lightgrey;
  width: 20%;
  margin-top: 10px;
  background: coral;
  color: #fff;
}
</style>