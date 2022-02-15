<template>
  <form class="teacher-details">
    <h2>Your details</h2>
    <label class="text">
      Full name:
      <input type="text" name="name">
    </label>
    <label class="text">
      Job title:
      <input type="text" name="title">
    </label>
    <h2>Your certifications</h2>
    <div class="badges">
      <label class="checkbox">
        MIEE Expert
        <input type="checkbox" name="miee">
      </label>
      <label class="checkbox">
        Apple Distinguished Educator
        <input type="checkbox" name="apple">
      </label>
      <label class="checkbox">
        Seesaw Ambassador
        <input type="checkbox" name="seesaw">
      </label>
      <label class="checkbox">
        Kognity Leader
        <input type="checkbox" name="kognity">
      </label>
    </div>
  </form>
</template>

<script>
export default {
  name: "TeacherForm",
  data: function() {
    return {
      name: "",
      title: "",
      badges: []
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
    justify-content: space-between;
    margin-bottom: 10px;
  }

  [type="text"] {
    background: #F5F5F5;
    border-radius: 2px;
    border: 1px solid #E8E8E8;
    width: calc(100% - 120px);
  }
</style>