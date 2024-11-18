<template>
  <div>
    <h3>Danh bạ</h3>
    <ul>
      <li
        v-for="contact in contacts"
        :key="contact.id"
        @click="selectContact(contact)"
        :class="{ selected: selectedContactId === contact.id }"
      >
        {{ contact.name }}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  props: {
    contacts: Array,
    selectedContactId: Number, // Nhận ID liên hệ được chọn từ parent
  },
  methods: {
    selectContact(contact) {
      this.$emit("select-contact", contact); // Gửi liên hệ được chọn lên parent
    },
  },
};
</script>

<style scoped>
.selected {
  background-color: #007bff;
  color: white;
}
</style>
