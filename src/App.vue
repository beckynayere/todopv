<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <HelloWorld msg="Welcome to Your Vue.js App"/>
</template>

<script>
import addItemForm from "./addItemForm";
import listView from "./listView";

export default {
    components: {
        addItemForm,
        listView
    },

    data: function() {
        return {
            items: []
        };
    },
    methods: {
        getItems() {
            axios
                .get("api/items")
                .then(res => {
                    this.items = res.data;
                })
                .catch(error => {
                    console.log(error);
                });
        }
    },
    created() {
        this.getItems();
    }
};
</script>
</style>
