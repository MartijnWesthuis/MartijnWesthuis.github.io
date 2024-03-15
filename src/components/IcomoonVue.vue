<template>
    <icomoon :iconSet="iconSet" v-bind="$props" />
  </template>
  
  <script>
    import { Icomoon, iconList } from "vue-icomoon";
    import iconSet from "../assets/selection.json";
  
    console.log(iconList(iconSet));

    export default {

      components: { Icomoon },
      setup() {
        return {
          iconSet,
        };
      },
    };
  </script>