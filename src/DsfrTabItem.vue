<script lang="ts" setup>
const props = defineProps<{
  label: string
  tabId: string
  tabPanelId: string
  selected: boolean
}>()

const emit = defineEmits<{
  (e: 'click', tabId: string): void
  (e: 'next' | 'previous' | 'first' | 'last'): void
}>()

const keyToEventDict = {
  ArrowRight: 'next',
  ArrowLeft: 'previous',
  ArrowDown: 'next',
  ArrowUp: 'previous',
  Home: 'first',
  End: 'last'
} as const

const onKeyDown = (event: KeyboardEvent) => {
  if (event.key in keyToEventDict) {
    const eventToEmit = keyToEventDict[event.key as keyof typeof keyToEventDict]
    emit(eventToEmit)
  }
}
</script>

<template>
  <li role="presentation" :key="props.tabId">
    <button
      :id="props.tabId"
      class="fr-tabs__tab fr-icon-checkbox-line fr-tabs__tab--icon-left"
      :tabindex="props.selected ? 0 : -1"
      role="tab"
      type="button"
      :aria-selected="props.selected"
      :aria-controls="props.tabPanelId"
      @keydown="onKeyDown($event)"
      @click="emit('click', props.tabId)"
    >
      {{ props.label }}
    </button>
  </li>
</template>
