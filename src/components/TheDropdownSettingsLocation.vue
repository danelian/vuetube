<template>
  <DropdownSettingsHeader 
    title="Choose your location" 
    @back="$emit('close')" 
  />
  <section class="py-2">
    <div class="text-gray-500 text-xs p-3">Setting applies to this browser only</div>
    <ul class="max-h-96 overflow-auto">
      <DropdownSettingsListItem
        v-for="(locationName, locationId) in locations"
        :key="locationId"
        :label="locationName"
        :active="locationId === selectedOptions.location.id"
        @click="selectOption({ id: locationId, text: locationName })"
      />
    </ul>
  </section>
</template>


<script>
import dropdownSubmenu from '../mixins/dropdownSubmenu'

export default {
  mixins: [dropdownSubmenu],

  data() {
    return {
      optionName: 'location',
      locations: ['Russia', 'Armenia', 'Ukraine', 'USA', 'France', 'Germany', 'Italia'],
    }
  },
}
</script>