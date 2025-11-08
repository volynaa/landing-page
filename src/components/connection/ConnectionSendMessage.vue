<template lang="pug">
.services-send-message
	.services-send-message__header
		h3.services-send-message__title Отправить сообщение
		p.services-send-message__description Заполните форму ниже, и мы свяжемся с вами в ближайшее время
	.services-send-message__content
		transition(name="success" mode="out-in")
			.alert.alert_success(v-if="submitted")
				| Спасибо за обращение! Мы свяжемся с вами в ближайшее время.

		form.form(@submit.prevent="handleSubmit")
			MyInput(
				id="name"
				label="Имя"
				v-model="form.name"
				:validation-class="validation('name')"
				placeholder="Ваше имя"
				:error-message="fieldErrors.name"
				:show-error="v$.form.name.$error && v$.form.name.$dirty"
			)

			MyInput(
				id="email"
				label="Email"
				v-model="form.email"
				:validation-class="validation('email')"
				placeholder="your@mail.ru"
				:error-message="fieldErrors.email"
				:show-error="v$.form.email.$error && v$.form.email.$dirty"
			)

			MyInput(
				id="message"
				type="textarea"
				label="Сообщение"
				v-model="form.message"
				:validation-class="validation('message')"
				placeholder="Расскажите о вашем проекте..."
				:error-message="fieldErrors.message"
				:show-error="v$.form.message.$error && v$.form.message.$dirty"
			)

			button.button.button_send(type="submit") Отправить сообщение

</template>

<script setup lang="ts">
import {computed, ref} from "vue";
import {email, helpers, maxLength, minLength, required} from "@vuelidate/validators";
import useVuelidate from "@vuelidate/core";
import MyInput from "@/components/UI/MyInput.vue";

interface FormData {
	name: string,
	email: string,
	message: string,
}

const form = ref<FormData>({
	name: '',
	email: '',
	message: ''
})

const submitted = ref<boolean>(false);

const fieldErrors = computed<FormData>(() => ({
	name: v$.value.form.name.$errors[0]?.$message || '',
	email: v$.value.form.email.$errors[0]?.$message || '',
	message: v$.value.form.message.$errors[0]?.$message || ''
}))

const rules = computed(() => ({
	form: {
		name: {
			required: helpers.withMessage('Имя обязательно для заполнения', required),
			minLength: helpers.withMessage('Имя должно содержать минимум 2 символа', minLength(2)),
			maxLength: helpers.withMessage('Имя не должно превышать 50 символов', maxLength(50)),
			validChars: helpers.withMessage(
				'Имя может содержать только буквы, пробелы и дефисы',
				(value: string) => !value || /^[a-zA-Zа-яА-ЯёЁ\s\-]+$/.test(value)
			)
		},
		email: {
			required: helpers.withMessage('Email обязателен для заполнения', required),
			email: helpers.withMessage('Введите корректный email адрес', email)
		},
		message: {
			required: helpers.withMessage('Сообщение обязательно для заполнения', required),
			minLength: helpers.withMessage('Сообщение должно содержать минимум 10 символов', minLength(10)),
			maxLength: helpers.withMessage('Сообщение не должно превышать 1000 символов', maxLength(1000))
		}
	}
}))

const v$ = useVuelidate(rules, { form });

function validation(type: keyof FormData | null): string {
	try {
		if (type) {
			if (v$.value.form[type].$dirty) {
				if (v$.value.form[type].$invalid) {
					return 'is-invalid'
				} else if (!v$.value.form[type].$invalid) {
					return 'is-valid'
				} else {
					return ''
				}
			} else {
				return ''
			}
		} else {
			return v$.value.form.$invalid ? 'form-invalid' : 'form-valid'
		}
	} catch {
		return ''
	}
}

function clearForm(): void {
	form.value.name = '';
	form.value.email = '';
	form.value.message = '';
	v$.value.$reset();
}
async function handleSubmit (): Promise<void> {
	const isFormCorrect = await v$.value.$validate()

	if (!isFormCorrect) {
		v$.value.form.$touch()
		return
	}

	submitted.value = true;

	setTimeout(() => {
		submitted.value = false;
	}, 3000);

	clearForm();
}
</script>

<style lang="less" scoped>
@import "@/styles/mixins.less";

.services-send-message {
	width: 70vw;
	margin: 0 auto;
	background: var(--white);
	border-radius: 0.5rem;
	box-shadow: 0 1px 3px 0 rgba(0, 0, 0, 0.1), 0 1px 2px 0 rgba(0, 0, 0, 0.06);
	overflow: hidden;

	@media (max-width: 768px) {
		width: auto;
		margin: 0 1rem;
	}

	&__header {
		padding: 1.5rem 1.5rem 0;
	}

	&__title {
		font-size: 1.5rem;
		font-weight: 600;
		color: #111827;
		margin-bottom: 0.5rem;
	}

	&__description {
		color: var(--gray-600);
		margin-bottom: 1rem;
	}

	&__content {
		padding: 1.5rem;
	}
}

.form {
	width: 100%;
	.flex-col();
	gap: 1rem;
}

.alert {
	padding: 1rem;
	border-radius: 0.375rem;
	margin-bottom: 1rem;

	&_success {
		background-color: car(--emerald-100);
		color: car(--emerald-800);
	}
}

.button {
	display: inline-flex;
	align-items: center;
	justify-content: center;
	padding: 0.5rem 1rem;
	font-size: 1rem;
	font-weight: 500;
	border: none;
	border-radius: 0.375rem;
	cursor: pointer;
	transition: all 0.15s ease-in-out;
	text-decoration: none;

	&_send {
		background-color: var(--primary-color);
		color: white;
		width: 100%;
		height: 2.5rem;

		&:hover {
			background-color: var(--blue-700);
		}

		&:focus {
			outline: none;
			box-shadow: 0 0 0 3px rgba(37, 99, 235, 0.1);
		}
	}
}

.success {
	.animation-transition();
}
</style>
