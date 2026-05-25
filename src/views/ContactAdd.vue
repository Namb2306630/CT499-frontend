<template>
  <div class="page">
    <h4>Thêm mới liên hệ</h4>
    <ContactForm @submit:contact="addContact" :contact="{}" />
    <p>{{ message }}</p>
  </div>
</template>

<script>
import ContactForm from "@/components/ContactForm.vue";
import ContactService from "@/services/contact.service";

export default {
  components: {
    ContactForm,
  },
  data() {
    return {
      message: "",
    };
  },
  methods: {
    async addContact(data) {
      try {
        await ContactService.create(data);
        alert("Liên hệ được tạo thành công.");
        this.$router.push({ name: "contactbook" });
      } catch (err) {
        console.log(err);
      }
    },
  },
};
</script>
