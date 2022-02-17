<template>
  <div class="builder">
    <h1>DCB Email Signature Builder</h1>
    <p>Complete the fields with your personal information to generate your new email signature. Your new signature can be copied and pasted into Outlook.</p>
    <p><a href="https://support.microsoft.com/en-gb/office/change-an-email-signature-86597769-e4df-4320-b219-39d6e1a9e87b">Click here to learn how to change your signature.</a></p>
    <TeacherForm/>
  </div>
</template>

<script>
import TeacherForm from './TeacherForm.vue'

export default {
  name: 'SignatureBuilder',
  components: {
    TeacherForm
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
  .builder {
    font-family: "Avenir W01", "Helvetica Neue", Helvetica, Arial, "Zawgyi-One", sans-serif;
    font-size: 1rem;
    line-height: 1.6;
    margin: 0 auto;
    padding: 50px;
    max-width: 850px;
  }

  a {
    color: #D30013;
  }

  a:hover {
    color: #9e1422
  }
</style>
