<template lang="pug">
.service-card
	header.service-card__header
		.service-card__icon-wrapper
			img.service-card__icon(:src="icon" :alt="`Иконка ${title}`")
		h3.service-card__title {{ title }}
		p.service-card__description {{ desc }}

	.service-card__content
		ul.service-card__possibilities
			li.service-card__possibilit(
				v-for="(item, index) in possibilities"
				:key="index"
			)
				span.service-card__possibilit-text {{ item }}
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
		},
		possibilities: {
			type: Array,
			required: true
		}
	})
</script>

<style lang="less" scoped>
@import "@/styles/mixins.less";

.service-card{
	.section-card();
	border: 1px solid var(--bg-gray-600);

	&__header {
		margin-bottom: 1rem;
	}

	&__icon-wrapper {
		.flex-center();
		width: 3rem;
		height: 3rem;
		border-radius: 20%;
		background-color: var(--primary-color);
	}

	&__icon {
		width: 1.5rem;
		height: 1.5rem;
	}

	&__title {
		font-size: 1.25rem;
		font-weight: 600;
		margin-bottom: 0.5rem;
	}

	&__description {
		color: var(--gray-600);
		font-size: 0.875rem;
		line-height: 1.5;
	}

	&__content {
		margin-top: 1rem;
	}

	&__possibilities {
		font-size: 0.875rem;
		padding-left: 1rem;

		li {
			color: var(--primary-color);
		}
	}

	&__possibilit-text {
		line-height: 2;
		color: var(--gray-900);
	}

}
</style>