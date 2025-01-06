<script setup lang="ts">
	import { AccordionHeader, AccordionTrigger } from 'radix-vue';
	import type { AccordionTriggerProps } from 'radix-vue';
	import { computed } from 'vue';
	import type { HTMLAttributes } from 'vue';
	import { cn } from '../Utils';

	const props = defineProps<AccordionTriggerProps & { class?: HTMLAttributes['class'] }>();

	const delegatedProps = computed(() => {
		const { class: _, ...delegated } = props;

		return delegated;
	});
</script>

<template>
	<AccordionHeader class="flex">
		<AccordionTrigger
			v-bind="delegatedProps"
			:class="
				cn(
					'flex flex-1 items-center justify-between py-4 font-medium transition-all hover:underline [&[data-state=open]>svg]:rotate-180',
					props.class,
				)
			"
		>
			<slot />
			<slot name="icon"> </slot>
		</AccordionTrigger>
	</AccordionHeader>
</template>
