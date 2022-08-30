<template>
  <form class="teacher-details">
    <h2>Your details</h2>
    <label class="text">
      Full name:
      <input type="text" name="name_en" v-model="staff_name_en">
    </label>
    <label class="text">
      姓名:
      <input type="text" name="name_zh" v-model="staff_name_zh">
    </label>
    <label class="text">
      Job title:
      <input type="text" name="title_en" v-model="staff_title_en">
    </label>
    <label class="text">
      职称:
      <input type="text" name="title_zh" v-model="staff_title_zh">
    </label>
    <label class="text">
      Phone extension / <br>
      电话分机:
      <input type="text" name="title_zh" v-model="staff_extension" placeholder="e.g. 9174">
    </label>
    <h2>Your certifications (optional - max. 3)</h2>
    <div class="badges">
      <label class="checkbox" v-for="badge in staff_badges" :key="badge.id">
        {{ badge.title }}
        <input type="checkbox" :name="badge.title" v-model="badge.selected">
      </label>
      <label>
        Something missing? <a href="mailto:jared.rigby@dulwich.org">Email Jared</a>
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
        { id: "apple", title: "Apple Distinguished Educator", selected: false },
        { id: "common", title: "Common Sense Educator", selected: false},
        // { id: "google1", title: "Google Certified Educator Level 1", selected: false},
        // { id: "google2", title: "Google Certified Educator Level 2", selected: false},
        { id: "iste", title: "ISTE Certified Educator", selected: false },
        { id: "kognity", title: "Kognity Lead Educator", selected: false },
        { id: "miee-2122", title: "MIEE 2021-2022", selected: false },
        { id: "esports", title: "Microsoft Esports Leader", selected: false },
        { id: "seesaw", title: "Seesaw Ambassador", selected: false }
      ]
    }
  },
  computed: {
    badge_counter: function() {
      let num_badges = this.staff_badges.filter(badge => badge.selected == true).length

      if (num_badges <= 3) {
        return num_badges;
      } else {
        return -1;
      }
    },
    selected_badges: function() {
      if (this.badge_counter !== -1) {
        return this.staff_badges.filter(badge => badge.selected == true);
      } else {
        return [];
      }
    }
  }
}
</script>

<style scoped>

  a {
    color: #D30013;
  }
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