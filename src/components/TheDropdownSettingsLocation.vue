<template>
  <DropdownSettingsHeader 
    title="Choose your location" 
    @back="$emit('select-menu', 'main')" 
  />
  <section class="py-2">
    <div class="text-gray-500 text-xs p-3">Setting applies to this browser only</div>
    <ul>
      <DropdownSettingsListItem
        v-for="location, locationId in locations"
        :key="locationId"
        :label="location"
        :active="locationId === selectedLocationId"
        @click="selectedLocationId = locationId"
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
      selectedLocationId: 0,
      locations: ['Russia', 'Armenia', 'Ukraine', 'USA', 'France'],
    }
  },

}
</script>