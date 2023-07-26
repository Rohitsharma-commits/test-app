<template>
  <div>
    <div v-html="formTemplate" ref="formContainer"></div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      formTemplate: `
        <form>
          <label for="name">Name:</label>
          <input type="text" id="name" required>
          <br>
          <label for="email">Email:</label>
          <input type="email" id="email" required>
          <br>
          <label for="message">Message:</label>
          <textarea id="message" required></textarea>
          <br>
          <!-- Manually bind the click event to the button -->
          <button type="button" @click="handleSubmit">Submit</button>
        </form>
      `,
    };
  },
  methods: {
    handleSubmit() {
      const name = document.getElementById('name').value;
      const email = document.getElementById('email').value;
      const message = document.getElementById('message').value;

      console.log({ name, email, message });
    },
  },
  mounted() {
    const button = this.$refs.formContainer.querySelector('button');
    button.addEventListener('click', this.handleSubmit);
  },
};
</script>