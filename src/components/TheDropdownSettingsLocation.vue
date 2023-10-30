<template>
  <DropdownSettingsHeader 
    title="Choose your location" 
    @back="$emit('select-menu', 'main')" 
  />
  <section class="py-2">
    <div class="text-gray-500 text-xs p-3">Setting applies to this browser only</div>
    <ul class="max-h-96 overflow-auto">
      <DropdownSettingsListItem
        v-for="locationName, locationId in locations"
        :key="locationId"
        :label="locationName"
        :active="locationId === selectedOptions.locationId"
        @click="selectOption(locationId)"
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

  props: ['selectedOptions'],
  emits: ['select-menu', 'select-option'],

  data() {
    return {
      locations: ['Russia', 'Armenia', 'Ukraine', 'USA', 'France', 'Germany', 'Italia'],
    }
  },

  methods: {
    selectOption (locationId) {
      this.$emit('select-option', { name: 'locationId', value: locationId })
    }
  }
}
</script>