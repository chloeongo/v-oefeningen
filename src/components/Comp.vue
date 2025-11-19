<script>
export default {
  mounted() {
    this.$refs.inpName.focus()
  },
}
</script>

<template>
  <h2>Form Component</h2>
  <p>
    When this component is added to the DOM tree, the mounted() function is called, and we put the
    cursor inside the input element.
  </p>
  <form @submit.prevent>
    <label>
      <p>
        Name: <br />
        <input type="text" ref="inpName" />
      </p>
    </label>
    <label>
      <p>
        Age: <br />
        <input type="number" />
      </p>
    </label>
    <button>Submit</button>
  </form>
  <p>(This form does not work, it is only here to show the mounted lifecycle hook.)</p>
</template>

<style></style>
