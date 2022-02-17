<template>
  <form class="teacher-details">
    <h2>Your details</h2>
    <label class="text">
      Full name (en):
      <input type="text" name="name_en" v-model="staff_name_en">
    </label>
    <label class="text">
      Full name (zh):
      <input type="text" name="name_zh" v-model="staff_name_zh">
    </label>
    <label class="text">
      Job title (en):
      <input type="text" name="title_en" v-model="staff_title_en">
    </label>
    <label class="text">
      Job title (zh):
      <input type="text" name="title_zh" v-model="staff_title_zh">
    </label>
    <label class="text">
      Phone extension:
      <input type="text" name="title_zh" v-model="staff_extension">
    </label>
    <h2>Your certifications</h2>
    <div class="badges">
      <label class="checkbox" v-for="badge in staff_badges" :key="badge.id">
        {{ badge.title }}
        <input type="checkbox" :name="badge.title" v-model="badge.selected">
      </label>
    </div>
  </form>
  <Previewer 
    :name_en="staff_name_en" 
    :name_zh="staff_name_zh" 
    :title_en="staff_title_en" 
    :title_zh="staff_title_zh" 
    :badges="selected_badges"
    :phone_extension="staff_extension"
  />
</template>

<script>
import Previewer from './Previewer.vue'

export default {
  name: "TeacherForm",
  components: {
    Previewer
  },
  data: function() {
    return {
      staff_name_en: "",
      staff_name_zh: "",
      staff_title_en: "",
      staff_title_zh: "",
      staff_extension: "",
      staff_badges: [
        // { id: "apple", title: "Apple Distinguished Educator", selected: false },
        // { id: "mie", title: "MS Innovative Educator", selected: false },
        { id: "miee21", title: "MIEE 2020-2021", selected: false },
        // { id: "miee22", title: "MIEE 2021-2022", selected: false },
        { id: "seesaw", title: "Seesaw Ambassador", selected: false },
        { id: "kognity", title: "Kognity Lead Educator", selected: false }
      ]
    }
  },
  computed: {
    selected_badges: function() {
      return this.staff_badges.filter(badge => badge.selected == true)
    }
  }
}
</script>

<style scoped>
  .teacher-details {
    background: #fff;
    box-shadow: 0 0 8px rgba(0, 0, 0, 0.25);
    color: #3C3737;
    border-bottom: 6px solid #D30013;
    padding: 50px;
  }

  label.text {
    display: flex;
    align-items: center;
    justify-content: space-between;
    margin-bottom: 10px;
  }

  [type="text"] {
    background: #F5F5F5;
    border-radius: 2px;
    border: 1px solid #E8E8E8;
    width: calc(100% - 150px);
    padding: 10px;
    font-family: "Avenir W01", "Helvetica Neue", Helvetica, Arial, "Zawgyi-One", sans-serif;
    font-size: 1rem;
  }

  .badges {
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
  }

  .badges label {
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: #F5F5F5;
    width: calc(50% - 7.5px);
    margin-bottom: 15px;
    padding: 15px;
    border-radius: 2px;
  }
</style>