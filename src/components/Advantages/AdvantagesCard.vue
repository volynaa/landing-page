<template lang="pug">
.advantages-card
	.advantages-card__icon
		img(:src="icon" :alt="`Иконка ${title}`")
	h3.advantages-card__title {{ title }}
	p.advantages-card__desc {{ desc }}

</template>

<script setup>
	defineProps({
		icon: {
			type: String,
			required: true
		},
		title: {
			type: String,
			required: true
		},
		desc: {
			type: String,
			required: true
		}
	})
</script>

<style lang="less" scoped>
@import "@/styles/mixins.less";

.advantages{
	&-card {
		text-align: center;
		padding: 1.5rem;
		border-radius: 0.5rem;
		transition: box-shadow 0.2s ease-in-out;

		&:hover {
			box-shadow: 0 10px 25px rgba(0, 0, 0, 0.1);
		}
	}
}
</style>