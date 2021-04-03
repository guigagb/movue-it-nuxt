<template>
	<section class="flex flex-col flex-1 justify-center items-center py-6">
		<header class="w-full pb-6 border-b-2 border-background">
			<h2 class="text-xl text-blue font-semibold text-center">{{ `Win ${amount} xp` }}</h2>
		</header>
		<main class="flex flex-col flex-1 justify-center items-center mt-6">
			<img :src="`icons/${type}.svg`" :alt="type" :style="{minHeight: '70px'}" />
			<h1 class="font-semibold text-3xl text-title mt-4 mb-2">Work out</h1>
			<p class="text-center text-base leading-6">{{description}}</p>
		</main>
		<footer class="flex w-full gap-x-2">
			<button @click="resetChallenges" class="button failed">Failed</button>
			<button @click="challengeSucceeded" class="button succeeded">Completed</button>
		</footer>
	</section>
</template>

<script lang="ts">
import Vue from "vue";
import { mapState, mapMutations } from "vuex";

import { Mutations as CountdownMT } from "@/store/Countdown/types";
import { Challenge as ChallengeType, Mutations as ChallengesMT } from "@/store/Challenges/types";

export default Vue.extend<unknown, any, unknown, ChallengeType>({
	props: {
		type: { type: String, required: true },
		description: { type: String, required: true },
		amount: { type: Number, required: true },
	},
    computed:{
        ...mapState('Challenges',['level','xp','completedChallenges'])
    },
    methods: {
        ...mapMutations({
            resetTime: `Countdown/${CountdownMT.RESET_TIME}`,
            setIsActive: `Countdown/${CountdownMT.SET_IS_ACTIVE}`,
            setHasCompleted: 
        })
    }
});
</script>