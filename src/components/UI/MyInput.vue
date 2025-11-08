<template lang="pug">
.form-field
	label.form-field__label(
		:for="id"
		:class="{ 'form-field__label_required': showError }"
	) {{ label }}

	input.form-field__input(
		v-if="type==='input'"
		:id="id"
		v-model="fieldValue"
		:class="inputClasses"
		:placeholder="placeholder"
	)
	textarea.form-field__input(
		v-else
		:id="id"
		v-model="fieldValue"
		:class="inputClasses"
		:placeholder="placeholder"
	)
	transition(name="showError" mode="out-in")
		.form-field__error(v-if="showError") {{ errorMessage }}
</template>

<script setup lang="ts">
import { computed } from 'vue'

interface Props {
	id: string
	type: string
	label: string
	modelValue: string
	placeholder?: string
	validationClass?: string
	errorMessage?: string
	showError?: boolean
}

interface Emits {
	(e: 'update:modelValue', value: string): void
}

const props = withDefaults(defineProps<Props>(), {
	id: '',
	type: 'input',
	label: '',
	modelValue: '',
	placeholder: '',
	validationClass: '',
	errorMessage: '',
	showError: false
});

const emit = defineEmits<Emits>();

const fieldValue = computed({
	get: () => props.modelValue,
	set: (value: string) => emit('update:modelValue', value)
});

const inputClasses = computed(() => {
	const classes = []
	if (props.validationClass) {
		classes.push(props.validationClass);
	}
	return classes;
})

</script>

<style lang="less" scoped>
@import "@/styles/mixins.less";

.form-field {
	&__label {
		display: block;
		margin-bottom: 0.5rem;
		font-weight: 500;
		color: var(--gray-700);

		&_required::after {
			content: ' *';
			color: var(--errors);
		}
	}

	&__input {
		width: calc(100% - 1.5rem);
		padding: 0.5rem 0.75rem;
		border: 1px solid var(--gray-300);
		border-radius: 0.375rem;
		font-size: 1rem;
		line-height: 1.5;
		transition: border-color 0.15s ease-in-out, box-shadow 0.15s ease-in-out;

		&:focus {
			outline: none;
			border-color: var(--blue-500);
			box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
		}

		&.is-invalid {
			border-color: var(--errors);

			&:focus {
				border-color: var(--errors);
				box-shadow: 0 0 0 3px rgba(239, 68, 68, 0.1);
			}
		}

		&.is-valid {
			border-color: var(--success);

			&:focus {
				border-color: var(--success);
				box-shadow: 0 0 0 3px rgba(16, 185, 129, 0.1);
			}
		}
	}

	&__error {
		color: var(--errors);
		font-size: 0.875rem;
		margin-top: 0.25rem;
	}
}

.showError {
	.animation-transition();
}

</style>
