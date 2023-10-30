<template>
  <DropdownSettingsHeader 
    title="Choose your language" 
    @back="$emit('select-menu', 'main')" 
  />
  <section class="py-2">
    <div class="text-gray-500 text-xs p-3">Setting applies to this browser only</div>
    <ul class="max-h-96 overflow-auto">
      <DropdownSettingsListItem
        v-for="language, languageId in languages"
        :key="languageId"
        :label="language"
        :active="languageId === selectedLanguageId"
        @click="selectedLanguageId = languageId"
      />
    </ul>
  </section>
</template>


<script>
import DropdownSettingsHeader from './DropdownSettingsHeader.vue'
import DropdownSettingsListItem from './DropdownSettingsListItem.vue';

export default {
  components: {
    DropdownSettingsHeader,
    DropdownSettingsListItem,
  },

  emits: ['select-menu'],

  data() {
    return {
      selectedLanguageId: 0,
      languages: ['English', 'Russian', 'Armenian'],
    }
  },

}
</script>