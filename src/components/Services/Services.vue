<template lang="pug">
section.services
	.services__container
		.services__header
			h2.services__title Наши услуги
			p.services__subtitle Полный спектр услуг для развития вашего цифрого присутствия
		.services__images
			img.services__image(src="/image/services/services-hands.jpg")
			img.services__image(src="/image/services/services-home.jpg")
		.services__items
			ServicesCard(
				v-for="(item, index) in services"
				:key="index"
				:icon="item.icon"
				:title="item.title"
				:desc="item.desc"
				:possibilities="item.possibilities"
			)

</template>

<script setup>
	import ServicesCard from "@/components/Services/ServicesCard.vue";

	const services = [
		{
			icon: '/image/services/development.svg',
			title: 'Веб-разработка',
			desc: 'Создание современных веб-приложений с использованием новейших технологий',
			possibilities: ['Vue & TypeScript', 'Responsive дизайн', 'SEO оптимизация']
		},
		{
			icon: '/image/services/phone.svg',
			title: 'Мобильные приложения',
			desc: 'Разработка нативных и кроссплатформенных мобильных приложений',
			possibilities: ['iOS & Android', 'Интуитивный UX', 'Push-уведомления']
		},
		{
			icon: '/image/services/planet.svg',
			title: 'Цифровой маркетинг',
			desc: 'Комплексное продвижение вашего бизнеса в интернете',
			possibilities: ['SMM', 'Контекстная реклама', 'Email-маркетинг']
		},
		{
			icon: '/image/services/database.svg',
			title: 'Backend решения',
			desc: 'Разработка серверной части и интеграция с внешними сервисами',
			possibilities: ['API разработка', 'Базы данных', 'Cloud решения']
		}
	]
</script>

<style lang="less" scoped>
@import '@/styles/mixins.less';

.services {
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
		.section-subtitle();
	}

	&__images {
		display: grid;
		grid-template-columns: 1fr 1fr;
		gap: 2rem;
		margin-bottom: 4rem;
		max-width: 64rem;

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
		}
	}

	&__image {
		width: 100%;
		height: 300px;
		object-fit: cover;
	}

	&__items {
		.section-items();
	}
}
</style>