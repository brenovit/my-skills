<template>
  <div class="about">
    <h1>Hello {{ their_name }}</h1>
    <h2>This is an about page</h2>
    <p>Lorem ipsum dolor sit amet, consectetur adipiscing elit. Nunc vel posuere quam. Proin sed dictum nulla, ut maximus est. Vivamus porttitor orci vel maximus commodo. In fringilla vestibulum justo. Nullam placerat neque sit amet metus pretium, nec maximus enim eleifend. Pellentesque tortor massa, pellentesque ut ullamcorper sed, tincidunt eu erat. Nulla facilisi. Fusce auctor ornare condimentum.</p>
  </div>
</template>
<script>
export default {
  name: "About",
  data() {
    return {
      their_name: this.$route.params.name
    };
  }
};
</script>