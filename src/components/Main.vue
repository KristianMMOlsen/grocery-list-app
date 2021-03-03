<template>
  <!-- container which wraps around the whole application -->
  <div class="container mx-0 px-0">
    <!-- row for the title -->
    <div class="row mx-0">
      <div class="col-12">
        <h1>GROCERY LISTS</h1>
      </div>
    </div>
    <!-- row for the textfield for adding items -->
    <div class="row justify-content-center mx-0">
      <div class="col-7 col-md-10 col-lg-10 pr-0">
        <div class="form-group">
          <input
            v-model="newItem"
            type="text"
            class="form-control shadow"
            placeholder="Add new item to list"
          />
        </div>
      </div>
      <div class="col-5 col-md-2 col-lg-2 px-0">
        <!-- button that adds items to the list by using the addItem function -->
        <button v-on:click="addItem" class="btn btn-success">
          Add to list
        </button>
      </div>
    </div>
    <!-- row for the text area listing items -->
    <div class="row justify-content-center mt-3 mx-0">
      <div class="col-12 col-md-12 col-lg-12">
        <ul class="list-group overflow-auto shadow">
          <!-- v-for that loops through the items array, and lists them as an unordered list if there are items to list -->
          <li
            class="list-group-item"
            v-for="(item, index) in items"
            v-bind:key="index"
          >
            {{ item }}
            <!-- button that when clicked removes targeted items from the list by using the removeItem function -->
            <button
              v-on:click="removeItem(index)"
              type="button"
              class="btn btn-danger"
              id="removeItem"
            >
              <!-- the svg is the icon for the trashcan on the remove button -->
              <svg
                xmlns="http://www.w3.org/2000/svg"
                xmlns:xlink="http://www.w3.org/1999/xlink"
                aria-hidden="true"
                focusable="false"
                width="1em"
                height="1em"
                style="
                  -ms-transform: rotate(360deg);
                  -webkit-transform: rotate(360deg);
                  transform: rotate(360deg);
                "
                preserveAspectRatio="xMidYMid meet"
                viewBox="0 0 16 16"
              >
                <g fill="#000">
                  <path
                    d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6z"
                  />
                  <path
                    fill-rule="evenodd"
                    d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1zM4.118 4L4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118zM2.5 3V2h11v1h-11z"
                  />
                </g>
              </svg>
            </button>
          </li>
        </ul>
      </div>
    </div>
    <!-- row for the "show previous lists and save list" buttons -->
    <div class="row my-3 justify-content-center mx-0">
      <div class="col-6">
        <button type="button" class="btn btn-primary btnHeight">
          Show previous grocery lists
        </button>
      </div>
      <div class="col-6">
        <button type="button" class="btn btn-success btnHeight">
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

    //need to add a filter function to prevent adding empty items to the list
  },
};
</script>
<!-- css styling for this component only -->
<style scoped>
/* styling for the list, also breaks long words automatically
   to prevent them going outside it's div */
ul {
  width: 100%;
  height: 400px;
  list-style-type: none;
  padding: 0;
  word-wrap: break-word;
  float: left;
}
/* makes every other line in the list light grey background */
li:nth-child(even) {
  background: rgb(240, 236, 236);
}
/* styling for the button that removes items from the list */
#removeItem {
  float: right;
}
/* aligns the text on the list items to the left */
.list-group-item {
  text-align: left;
  font-size: 25px;
}
.btnHeight {
  height: 100%;
}
</style>