<template>
	<div
		class="flex justify-between items-center pb-5 border-b-2 border-gray-line mt-8 lg:mt-12 font-medium"
	>
		<p class="text-lg">Completed Challenges</p>
		<p class="text-2xl">{{ completedChallenges }}</p>
	</div>
</template>

<script lang="ts">
import Vue from "vue";
import { mapState } from "vuex";

export default Vue.extend({
	computed: {
		...mapState("Challenges", ["completedChallenges"]),
	},
});
</script>

