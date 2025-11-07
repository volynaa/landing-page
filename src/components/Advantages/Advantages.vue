<template lang="pug">
section.advantages
	.advantages__container
		.advantages__header
			h2.advantages__title Наши преимущества
			p.advantages__subtitle Мы предоставляем комплексные решения, которые помогут вашему бизнесу достичь новых высот
		.advantages__items
			AdvantagesCard(
				v-for="(item, index) in advantages"
				:key="index"
				:icon="item.icon"
				:title="item.title"
				:desc="item.desc"
			)

</template>

<script setup>

import AdvantagesCard from "@/components/Advantages/AdvantagesCard.vue";

const advantages = [
	{
		icon: '/image/advantages/lightning.svg',
		title: 'Быстро',
		desc: 'Оперативная разработка и внедрение решений для вашего бизнеса'
	},
	{
		icon: '/image/advantages/security.svg',
		title: 'Надежно',
		desc: 'Высокие стандарты безопасности и качества кода'
	},
	{
		icon: '/image/advantages/stonks.svg',
		title: 'Эффективно',
		desc: 'Увеличиваем конверсию и рост вашего бизнеса'
	},
	{
		icon: '/image/advantages/support.svg',
		title: 'Поддержка',
		desc: 'Круглосуточная техническая поддержка и консультации'
	}
]
</script>

<style lang="less" scoped>
@import "@/styles/mixins.less";

.advantages {
	padding: 5rem 0;
	background: var(--white);

	&__container {
		margin: 0 auto;
		padding: 0 1rem;
	}

	&__header {
		text-align: center;
		margin-bottom: 4rem;
	}

	&__title {
		font-size: 2.25rem;
		font-weight: 700;
		line-height: 1.2;
		margin-bottom: 1rem;
		color: var(--gray-900);
	}

	&__subtitle {
		font-size: 1rem;
		line-height: 1.6;
		color: var(--gray-600);
		max-width: 32rem;
		margin: 0 auto;
	}

	&__items {
		display: grid;
		grid-template-columns: repeat(4, 1fr);
		gap: 2rem;

		@media (max-width: 768px) {
			grid-template-columns: repeat(2, 1fr);
		}

		@media (max-width: 640px) {
			grid-template-columns: 1fr;
		}
	}
}
</style>