<template>
  <div class="preview_wrapper">
    <h2>Preview</h2>
    <button @click="toggleDarkMode">Dark Mode</button>
    <div class="previewer" :class="{ dark: darkMode }">
      <div class="live-preview">
        <table class="email-template" width="600" style="width: 600px; margin: 0; padding: 0; font-family: 'Avenir W01', 'Helvetica Neue', Helvetica, Arial, 'Zawgyi-One', sans-serif;">
          <tr>
            <td>
              <table style="margin: 0; padding: 0; font-family: 'Avenir W01', 'Helvetica Neue', Helvetica, Arial, 'Zawgyi-One', sans-serif; line-height: 1.1"> <!-- Name and job title -->
                <tr>
                  <td colspan="2" style="padding: 0; padding-bottom: 6px;">
                    <strong>{{ name_en }} {{ name_zh }}</strong>
                  </td>
                </tr>
                <tr>
                  <td style="padding: 0;">{{ title_en }} {{ title_zh }}</td>
                </tr>
              </table>
            </td>
          </tr>
          <tr v-if="badges.length > 0">
            <td>
              <table style="margin: 0; padding: 0; font-family: 'Avenir W01', 'Helvetica Neue', Helvetica, Arial, 'Zawgyi-One', sans-serif;"> <!-- Staff accreditation -->
                <tr>
                  <td style="padding-top: 5px; padding-bottom: 5px; padding-left: 0; padding-right: 7px;" v-for="badge in badges" :key="badge.id">
                    <img style="display: block;" :title="badge.title" :src="getImgUrl(badge.id)" />
                  </td>
                </tr>
              </table>
            </td>
          </tr>
          <tr>
            <td>
              <table style="margin: 0; padding: 0;"> <!-- DCB Branding -->
                <tr> <!-- Main logo -->
                  <td colspan="2" style="border-top: 1px solid #7c484f; padding-top: 10px; padding-bottom: 0; padding-left: 0; padding-right: 0;">
                    <img src="../assets/dcb-branding/dcb-logo-v4.png" title="Dulwich College Beijing" />
                  </td>
                </tr>
                <tr>
                  <td style="padding-top: 0; padding-left: 0; padding-right: 0;">
                    <img src="../assets/dcb-branding/live-worldwise.png" title="Live Worldwise" />
                  </td>
                  <td>
                    <table width="330" style="margin: 0; padding: 0;">
                      <tr>
                        <td style="border-bottom: 1px solid #7c484f; padding: 0;"></td>
                      </tr>
                    </table>
                  </td>
                </tr>
              </table>
            </td>
          </tr>
          <tr>
            <td>
              <table style="margin: 0; padding: 0;"> <!-- School contact details -->
                <tr>
                  <td style="font-size: 12px; font-family: 'Avenir W01', 'Helvetica Neue', Helvetica, Arial, 'Zawgyi-One', sans-serif; padding: 0; line-height: 1.2;">
                    <strong>beijing.dulwich.org</strong> | 
                    <strong>T:</strong> +8610 6454 <span v-if="phone_extension">{{ phone_extension}}</span> <span v-else>9000</span> 
                    | <strong>WeChat:</strong> DulwichBeijing
                    <br>
                    89 Capital Airport Road Shunyi District Beijing 101300 PRC
                    <br>
                    北京德威英国国际学校 北京市顺义区首都机场路89号丽京花园7区 邮编：101300
                    <br>
                  </td>
                  <td>
                    <table style="margin: 0; padding: 0">
                      <tr>
                        <td style="padding-top: 0px; padding-left: 25px; padding-bottom: 0; padding-right: 0;">
                          <a href="https://www.linkedin.com/school/dulwich-college-beijing/mycompany/">
                            <img width="24" height="32" src="../assets/socials/linkedin.png" alt="">
                          </a>
                        </td>
                        <td style="padding-top: 0px; padding-left: 7px; padding-bottom: 0; padding-right: 0;">
                          <a href="https://www.facebook.com/dulwichbeijing">
                            <img width="24" height="32" src="../assets/socials/facebook.png" alt="">
                          </a>
                        </td>
                        <td style="padding-top: 0px; padding-left: 7px; padding-bottom: 0; padding-right: 0;">
                          <a href="https://www.instagram.com/dulwichcollegebeijing/">
                            <img width="24" height="32" src="../assets/socials/instagram.png" alt="">
                          </a>
                        </td>
                        <td style="padding-top: 0px; padding-left: 7px; padding-bottom: 0; padding-right: 0;">
                          <a href="https://www.youtube.com/channel/UCPAMYCaLqMLdKSTZWfmL-YQ">
                            <img width="32" height="32" src="../assets/socials/youtube.png" alt="">
                          </a>
                        </td>
                      </tr>
                    </table>
                  </td>
                </tr>
              </table>
            </td>
          </tr>
          <tr>
            <td>
              <table style="margin: 0; padding: 0;"> <!-- School accreditation -->
                <tr>
                  <td style="padding: 0; padding-bottom: 5px;">
                    <img src="../assets/accreditations/all-accreds.png" alt="">
                  </td>
                </tr>
                <tr>
                  <td style="font-size: 12px; font-family: 'Avenir W01', 'Helvetica Neue', Helvetica, Arial, 'Zawgyi-One', sans-serif; padding: 0; line-height: 1.2; margin: 0;">
                    <small>
                      <em>
                        This email and any files transmitted with it are confidential and intended solely for the recipients to whom they are addressed. It is forbidden to share any part of this message with any third party without the sender's consent.<br>
                        If you received this message by mistake, please notify the sender immediately and delete this email from your system. If you are not the named addressee, you should not disseminate, distribute or copy this email. 
                      </em>
                    </small>
                  </td>
                </tr>
              </table>
            </td>
          </tr>
        </table>
      </div>
      <!-- <button>Copy to clipboard</button> -->
    </div>
  </div>
</template>
<script>
export default {
  name: "Previewer",
  props: ['name_en', 'name_zh', 'title_en', 'title_zh', 'badges', 'phone_extension'],
  data() {
    return {
      darkMode: false
    }
  },
  methods: {
    getImgUrl(badge_id) {
      return require('../assets/teacher-badges/' + badge_id + '.png')
    },
    toggleDarkMode() {
      this.darkMode = !this.darkMode;
    }
  }
}
</script>
<style>

  .preview_wrapper {
    position: relative;
    margin-top: 50px;
  }

  .preview_wrapper button {
    position: absolute;
    top: 0px;
    right: 0;
    font-size: 80%;
    background-color: #d30013;
    border-radius: 4px;
    border-style: none;
    color: #fff;
    display: inline;
    font-size: 16px;
    font-size: 1rem;
    line-height: 16px;
    margin: 0;
    min-width: 1px;
    padding: 8px 24px 9px;
  }

  .preview_wrapper button:hover {
    cursor: pointer;
    background: #9e1422
  }

  .previewer {
    position: relative;
    line-height: 1;
    background: #fff;
    box-shadow: 0 0 8px rgba(0, 0, 0, 0.25);
    color: #3C3737;
    padding: 50px;
    margin-top: 20px;
  }

  .previewer.dark {
    background: #262626;
    color: #fff;
  }

  
</style>