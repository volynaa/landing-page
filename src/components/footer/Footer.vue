<template lang="pug">
footer.footer
	.footer__container
		.footer__content
			.footer__section
				h3.footer__title О компании
				p.footer__text Мы создаем инновационные цифровые решения для бизнеса любого масштаба.

			.footer__section
				h3.footer__title Услуги
				ul.footer__list
					li.footer__item
						a.footer__link(@click="scrollUp") Веб-разработка
					li.footer__item
						a.footer__link(@click="scrollUp") Мобильные приложения
					li.footer__item
						a.footer__link(@click="scrollUp") Дизайн
					li.footer__item
						a.footer__link(@click="scrollUp") Консалтинг

			.footer__section
				h3.footer__title Компания
				ul.footer__list
					li.footer__item
						a.footer__link(@click="scrollUp") О нас
					li.footer__item
						a.footer__link(@click="scrollUp") Блог
					li.footer__item
						a.footer__link(@click="scrollUp") Карьера
					li.footer__item
						a.footer__link(@click="scrollUp") Контакты

			.footer__section
				h3.footer__title Контакты
				span.footer__info 8 (880) 555 35 35
				span.footer__info info@company.com

		.footer__bottom
			p.footer__copyright &copy; {{ currentYear }} Ваша крутая Компания. Все права защищены.
</template>

<script setup>
	const currentYear = new Date().getFullYear();

	function scrollUp() {
		const element = document.getElementById('header-block');
		if (element) {
			element.scrollIntoView({
				behavior: 'smooth',
				block: 'start'
			});
		}
	}
</script>

<style lang="less">
@import '@/styles/mixins.less';

.footer {
	background-color: var(--gray-900);
	color: var(--gray-300);

	&__container {
		margin: 0 auto;
		padding: 0 1rem;
	}

	&__content {
		.section-items();
		padding: 3rem 0;

		@media (max-width: 768px) {
			grid-template-columns: 1fr;
		}
	}

	&__section {
		.flex-col();
	}

	&__title {
		color: var(--white);
		font-size: 1.125rem;
		font-weight: 600;
		margin-bottom: 1rem;
	}

	&__text {
		font-size: 0.875rem;
		line-height: 1.5;
	}

	&__list {
		list-style: none;
		padding: 0;
		margin: 0;
		display: flex;
		flex-direction: column;
		gap: 0.5rem;
	}

	&__item {
		margin: 0;
	}

	&__link {
		color: var(--gray-300);
		font-size: 0.875rem;
		text-decoration: none;
		transition: color 0.3s ease;
		cursor: pointer;

		&:hover {
			color: var(--white);
		}
	}

	&__bottom {
		border-top: 1px solid var(--gray-700);
		padding: 2rem 0;
		text-align: center;
	}

	&__copyright {
		font-size: 0.875rem;
		margin: 0;
	}

	&__info {
		font-size: 0.875rem;
		line-height: 1.5rem;
	}

}
</style>
