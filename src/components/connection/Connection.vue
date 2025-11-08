<template lang="pug">
section.connection(id="contact-block")
	.connection__container(v-once)
		.connection__header
			.connection__title Свяжитесь с нами
			.connection__desc Готовы начать проект? Напишите нам, и мы ответим в течении 24 часов
	ConnectionSendMessage

</template>

<script setup>
	import ConnectionSendMessage from "@/components/connection/ConnectionSendMessage.vue";
</script>

<style lang="less" scoped>
@import "@/styles/mixins.less";

.connection {
	padding: 5rem 0;
	background-color: var(--gray-50);

	&__header {
		.section-header();
	}

	&__title {
		.section-title();
	}

	&__description {
		.section-subtitle(42rem);
	}
}
</style>
