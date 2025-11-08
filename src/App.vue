<template lang="pug">
Header
Advantages
Services
Connection
Footer
</template>

<script setup>
import {defineAsyncComponent} from "vue";
import Header from "@/components/Header.vue";
import Advantages from "@/components/advantages/Advantages.vue";
const Services = defineAsyncComponent(() =>
	import("@/components/services/Services.vue")
);
const Connection = defineAsyncComponent(() =>
	import("@/components/connection/Connection.vue")
);
const Footer = defineAsyncComponent(() =>
	import("@/components/footer/Footer.vue")
);
</script>

<style scoped></style>
