<template lang="pug">
section.header
	.header__content
		.text__content
			h1.header__title Создаем цифровые решения для вашего бизнеса
			p.header__desc Мы помогаем компаниям расти и развиваться с помощью современных техологий и инновационных подходов
		.header__buttons
			button.header__btn.header__btn--action(@click="scrollToContact")
				span Начать работу
				img(src="/image/arrow-right.svg")
			button.header__btn.header__btn--info
				span Узнать больше
	.header-gradient

</template>

<script setup>
	function scrollToContact(){
		const targetElement = document.getElementById('contact-block');
		if (targetElement) {
			targetElement.scrollIntoView({
				behavior: 'smooth',
				block: 'start'
			});
		}
	}
</script>

<style lang="less" scoped>
@import '@/styles/mixins.less';

.button__base() {
	.flex-center();
	gap: 0.5rem;
	height: 2.5rem;
	padding: 0 1.5rem;
	border: none;
	border-radius: 0.375rem;
	transition: all 0.2s ease-in-out;
	cursor: pointer;
	font-size: 1rem;
	line-height: 2rem;
}

.header {
	position: relative;
	background: linear-gradient(135deg, var(--primary-color), var(--violet-600));
	color: var(--white);
	overflow: hidden;

	&__content {
		padding: 6rem 1rem;

		@media (min-width: 768px) {
			padding: 8rem 1rem;
		}

		.text__content {
			text-align: center;
		}
	}


	&__title {
		font-size: 2.25rem;
		font-weight: 700;
		line-height: 1.2;
		margin-bottom: 1.5rem;

		@media (min-width: 768px) {
			font-size: 3rem;
		}
	}

	&__desc {
		font-size: 1.125rem;
		line-height: 1.6;
		color: var(--blue-100);
		margin-bottom: 2rem;

		@media (min-width: 768px) {
			font-size: 1.25rem;
		}
	}

	&__buttons {
		.flex-col();
		gap: 1rem;

		@media (min-width: 640px) {
			flex-direction: row;
			justify-content: center;
		}

	}

	&__btn {
		.button__base();
		text-align: center;

		&--action {
			background: var(--white);
			color: var(--primary-color);

			&:hover {
				background: var(--blue-50);
				box-shadow: 0 4px 12px rgba(0, 0, 0, 0.15);
			}
		}

		&--info {
			background: transparent;
			color: var(--white);
			border: 1px solid var(--white);

			&:hover {
				background: rgba(255, 255, 255, 0.1);
				box-shadow: 0 4px 12px rgba(255, 255, 255, 0.1);
			}
		}

	}

	&-gradient {
		position: absolute;
		bottom: 0;
		left: 0;
		right: 0;
		height: 4rem;
		background: linear-gradient(to top, var(--white), transparent);
	}
}

</style>
