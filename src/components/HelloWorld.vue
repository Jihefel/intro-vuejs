<template>
	<h1>Hello World</h1>
	<!-- <p>{{ user.name }} - {{ user.age }}</p> -->
	<!-- <slot name="name"></slot>
	<slot name="age"></slot> -->
	{{ country }}

	<select v-model="country" @change="handleUpdate">
		<option value="fr">France</option>
		<option value="us">USA</option>
	</select>
</template>

<script setup>
import { ref } from 'vue';

// defineProps({
// 	user: Object
// });

const emit = defineEmits(['updateCountry'])

const handleUpdate = (e) => {
	emit('updateCountry', e.target.value)
}

const country = ref('')
</script>