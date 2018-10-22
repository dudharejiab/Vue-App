<template>
    <div class="about">
        <h1>Hi {{ name }}! <p> This is About Page </p></h1>
        <p>Lorem  Ipsum dolor sit amet.</p>
    </div>
</template>

<script>
export default {
    name: "Skills",
  data() {
    return {
      name: this.$route.params.name
    }
  }
  
  
}
</script>
