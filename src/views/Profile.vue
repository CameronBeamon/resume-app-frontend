<script>
export default {
  data: function () {
    return {
      profile: {},
    };
  },
  created: function () {
    console.log("looks like it's working");
  },
  methods: {},
};
</script>

<template>
  <div class="profile">
    <h2>{{ "This is going to look great trust me" }}</h2>
    <p>{{ "Like I said, It'll look great" }}</p>
  </div>
</template>
