<template>
  <!-- container which wraps around the whole application -->
  <div class="container">
    <!-- row for the title -->
    <div class="row">
      <div class="col-12">
        <h1>GROCERY LISTS</h1>
      </div>
    </div>
    <!-- row for the textfield for adding items -->
    <div class="row justify-content-center">
      <div class="col-6 pr-0">
        <div class="form-floating">
          <input
            v-model="newItem"
            type="text"
            class="form-control shadow"
            placeholder="Add new item to list"
          />
        </div>
      </div>
      <div class="col-4 px-0">
        <!-- button that adds items to the list by using the addItem function -->
        <button v-on:click="addItem" class="btn btn-success">
          Add to list
        </button>
      </div>
    </div>
    <!-- row for the text area listing items -->
    <div class="row justify-content-center mt-3">
      <div class="col-10">
        <ul class="list-group overflow-auto shadow text-left">
          <!-- v-for that loops through the items array, and lists them as an unordered list if there are items to list -->
          <li
            class="list-group-item"
            v-for="(item, index) in items"
            v-bind:key="index"
          >
            {{ item }}
            <!-- button that when clicked removes targeted items from the list by using the removeItem function -->
            <span
              v-on:click="removeItem(index)"
              type="button"
              id="removeItem"
              class="text-center"
              >X</span
            >
          </li>
        </ul>
      </div>
    </div>
    <!-- row for the "show previous lists and save list" buttons -->
    <div class="row mt-3 justify-content-center">
      <div class="col-5">
        <button type="button" class="btn btn-primary">
          Show previous grocery lists
        </button>
      </div>
      <div class="col-5">
        <button type="button" class="btn btn-success">
          save current grocery list
        </button>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "Main",
  data: () => {
    return {
      //newItem is the same as what's written in the text field
      newItem: "",
      //the array for all the items added to the list
      items: [],
    };
  },
  methods: {
    // function that adds item from the textfield and places it in the list area by the use of push
    addItem() {
      if (this.newItem !== "");
      this.items.push(this.newItem);

      this.newItem = "";
    },
    //function that removes selected item from the list by using splice with index as identifier
    removeItem: function (index) {
      this.items.splice(index, 1);
    },
  },
};
</script>
<!-- css styling for this component only -->
<style scoped>
.container {
  margin: 0;
  padding: 0;
}
/* styling for the list, also breaks long words automatically
    to prevent them going outside it's div */
ul {
  width: 100%;
  height: 461px;
  list-style-type: none;
  padding: 0;
  word-wrap: break-word;
}
/* makes every other line in the list light grey background */
li:nth-child(even) {
  background: rgb(240, 236, 236);
}
/* styling for the button that removes items from the list */
#removeItem {
  background-color: red;
  width: 21px;
  height: 21px;
  border-radius: 50%;
  color: white;
  float: right;
}
</style>