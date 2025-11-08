<template lang="pug">
.advantages-card
	.advantages-card__icon-wrapper
		img.advantages-card__icon(:src="icon" :alt="`Иконка ${title}`")
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

.advantages-card {
	.section-card();
	text-align: center;

	&__icon-wrapper {
		.flex-center();
		width: 4rem;
		height: 4rem;
		border-radius: 50%;
		background-color: var(--blue-100);
		margin: 0 auto;
	}

	&__icon {
		width: 2rem;
		height: 2rem;
	}
}
</style>
