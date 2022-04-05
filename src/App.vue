<template>
  <main>
		<div class="container">
			<UserForm />
		</div>
	</main>
</template>

<script>
import UserForm from "./components/UserForm.vue"

export default {
  name: 'App',
  components: {
    UserForm
  }
}
</script>

<style lang="scss">
@import "./assets/ress.min.css";
@import "./assets/style.scss";
@import "./assets/form.scss";
</style>
