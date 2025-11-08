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
	import AdvantagesCard from "@/components/advantages/AdvantagesCard.vue";

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
	.section();

	&__container {
		.container();
	}

	&__header {
		.section-header();
	}

	&__title {
		.section-title();
	}

	&__subtitle {
		.section-subtitle(32rem);
	}

	&__items {
		.section-items();
	}
}
</style>
