<template>
  <div class="contact-book">
    <div class="contact-list">
      <ContactList
        :contacts="contacts"
        :selectedContactId="selectedContact?.id"
        @select-contact="handleSelectContact"
      />
      <div class="action-buttons">
        <button class="btn btn-refresh" @click="refreshContacts">Làm mới</button>
        <button class="btn btn-add" @click="addContact">Thêm mới</button>
        <button class="btn btn-delete-all" @click="deleteAllContacts">Xóa tất cả</button>
      </div>
    </div>
    <div class="contact-details">
      <h3>Chi tiết Liên hệ</h3>
      <div v-if="selectedContact">
        <p><strong>Tên:</strong> {{ selectedContact.name }}</p>
        <p><strong>Email:</strong> {{ selectedContact.email }}</p>
        <p><strong>Số điện thoại:</strong> {{ selectedContact.phone }}</p>
        <p><strong>Địa chỉ:</strong> {{ selectedContact.address }}</p>
        <p><strong>Liên hệ yêu thích:</strong> {{ }}</p>
      </div>
      <div v-else>
        <p>Vui lòng chọn một liên hệ để xem chi tiết.</p>
      </div>
    </div>
  </div>
</template>

<script>
import ContactList from "@/components/ContactList.vue";

export default {
  components: { ContactList },
  data() {
    return {
      contacts: [
        {
          id: 1,
          name: "Nguyễn Viết Long",
          email: "dc23v7x214@dttx.edu.vn",
          phone: "0935323346",
          address: "Tp. Hồ Chí Minh",
        },
        {
          id: 2,
          name: "Anh Long",
          email: "anhlong@gmail.com",
          phone: "0987654321",
          address: "Tp. Quy Nhơn",
        },
        {
          id: 3,
          name: "Quang Dolla",
          email: "quangdola@gmail.com",
          phone: "0912345678",
          address: "Tp.HCM",
        },
      ],
      selectedContact: null,
    };
  },
  methods: {
    handleSelectContact(contact) {
      this.selectedContact = contact;
    },
    refreshContacts() {
      // Logic để làm mới danh bạ (có thể fetch lại từ API hoặc reset)
      console.log("Làm mới danh bạ");
    },
    addContact() {
      // Logic thêm một liên hệ mới
      const newContact = {
        id: this.contacts.length + 1,
        name: `Liên hệ mới ${this.contacts.length + 1}`,
        email: `new${this.contacts.length + 1}@gmail.com`,
        phone: `090000000${this.contacts.length + 1}`,
        address: "Địa chỉ mới",
      };
      this.contacts.push(newContact);
    },
    deleteAllContacts() {
      // Xóa toàn bộ danh bạ
      if (confirm("Bạn có chắc muốn xóa tất cả liên hệ?")) {
        this.contacts = [];
        this.selectedContact = null;
      }
    },
  },
};
</script>

<style scoped>
.contact-book {
  display: flex;
  gap: 20px;
}

.contact-list,
.contact-details {
  flex: 1;
  border: 1px solid #ccc;
  padding: 10px;
}

.action-buttons {
  margin-top: 20px;
  display: flex;
  gap: 10px;
  justify-content: space-between;
}

.btn {
  padding: 10px 15px;
  border: none;
  cursor: pointer;
  font-size: 14px;
}

.btn-refresh {
  background-color: #007bff;
  color: white;
}

.btn-add {
  background-color: #28a745;
  color: white;
}

.btn-delete-all {
  background-color: #dc3545;
  color: white;
}

.btn:hover {
  opacity: 0.9;
}
</style>
