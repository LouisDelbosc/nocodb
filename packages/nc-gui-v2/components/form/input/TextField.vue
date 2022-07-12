<script lang="ts" setup>
import { computed } from '#imports'

interface Props {
  modelValue: string
  id?: string
  label?: string
  type?: string
  placeholder?: string
  error?: string
}

interface Emits {
  (event: 'update:modelValue', value: string): void
}

const { modelValue, label, id = undefined, type = 'text', placeholder, error } = defineProps<Props>()

const emits = defineEmits<Emits>()

const model = computed({
  get: () => modelValue,
  set: (value) => {
    emits('update:modelValue', value)
  },
})
</script>

<template>
  <label :for="id">
    <span>{{ label }}</span>
    <input :id="id" v-model="model" :type="type" :placeholder="placeholder" />
  </label>
</template>
