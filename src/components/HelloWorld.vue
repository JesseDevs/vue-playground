<script setup>
import { ref, computed, watch } from "vue";

const label = ref("name");
const name = ref("");
const output = ref("");

const message = computed(function () {
	if (name.value) {
		return `Hello world. My name is ${name.value}`;
	} else {
		return `Please enter your name`;
	}
});

function doSomething() {
	output.value = message;
}

watch(name, function (newName, oldName) {
	if (newName !== oldName) {
		output.value = '';
	}
});

const color = "#4fc08d";
</script>

<template>
  <form autocomplete="off" @submit.prevent="doSomething()">
		<h1>Hello World</h1>

		<div class="form-field">
			<label for="x">What is your {{ label }}?</label>
			<input autocomplete="off" id="x" type="text" v-model="name" />
		</div>

		<button type="submit">
			<span>Say Hello</span>
		</button>

		<output>
			{{ output }}
		</output>
	</form>
</template>

<style lang="scss">
#app {
	font-family: Avenir, Helvetica, Arial, sans-serif;
	text-align: center;
	color: #2c3e50;
	margin-top: 60px;
}

h1 {
	border-bottom: 1px solid black;
	margin: 0 auto;
	width: fit-content;
	font-size: 2rem;
}

output {
	margin-top: 40px;
	display: block;
}

div.form-field {
	display: flex;
	flex-direction: column;
	gap: 10px;
	margin-top: 20px;
	margin-bottom: 20px;
	justify-content: center;
	align-items: center;

	label {
		font-size: 1.1rem;
	}

	input {
		width: 60%;
		padding: 5px 10px;
		font-size: 1.1rem;
	}
}

a,
button {
	color: white;
}

button {
	background-color: v-bind(color);
	border: solid 2px;
	border-radius: 2em;
	font: inherit;
	font-weight: 700;
	letter-spacing: 0.4px;
	padding: 0.75em 2em;

	&:hover {
		background-color: white;
		color: v-bind(color);
	}
}
</style>
