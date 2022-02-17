<template>
  <div class="previewer">
    <h2>Preview - Copy and paste this into Outlook:</h2>
    <div class="live-preview">
      <table class="email-template" style="margin: 0; padding: 0; font-family: 'Avenir W01', 'Helvetica Neue', Helvetica, Arial, 'Zawgyi-One', sans-serif;">
        <tr>
          <td>
            <table style="margin: 0; padding: 0; font-family: 'Avenir W01', 'Helvetica Neue', Helvetica, Arial, 'Zawgyi-One', sans-serif; line-height: 1.1"> <!-- Name and job title -->
              <tr>
                <td colspan="2" style="padding: 0;">{{ name_en }} {{ name_zh }}</td>
              </tr>
              <tr>
                <td style="padding: 0;">{{ title_en }}</td>
              </tr>
              <tr v-if="title_zh !== ''">
                <td style="padding: 0;">{{ title_zh }}</td>
              </tr>
            </table>
          </td>
        </tr>
        <tr>
          <td>
            <table style="margin: 0; padding: 0; font-family: 'Avenir W01', 'Helvetica Neue', Helvetica, Arial, 'Zawgyi-One', sans-serif;"> <!-- Staff accreditation -->
              <tr>
                <td style="padding-top: 5px; padding-bottom: 5px; padding-left: 0; padding-right: 0;">
                  <img style="display: inline-block; margin-right: 5px;" v-for="badge in badges" :key="badge.id" :title="badge.title" :src="getImgUrl(badge.id)" />
                </td>
              </tr>
            </table>
          </td>
        </tr>
        <tr>
          <td>
            <table style="margin: 0; padding: 0;"> <!-- DCB Branding -->
              <tr> <!-- Main logo -->
                <td style="border-top: 2px solid #7c484f; border-bottom: 2px solid #7c484f; padding-top: 10px; padding-bottom: 7px; padding-left: 0; padding-right: 0;">
                  <img src="../assets/dcb-branding/dcb-logo.png" title="Dulwich College Beijing" />
                </td>
              </tr>
              <tr>
                <td style="padding-top: 10px; padding-left: 0; padding-bottom: 0; padding-right: 0;">
                  <a style="display: inline-block; margin-right: 5px;" href="https://www.linkedin.com/school/dulwich-college-beijing/mycompany/">
                    <img width="25" height="25" src="../assets/socials/linkedin.png" alt="">
                  </a>
                  <a style="display: inline-block; margin-right: 5px;" href="https://www.facebook.com/dulwichbeijing">
                    <img width="25" height="25" src="../assets/socials/facebook.png" alt="">
                  </a>
                  <a style="display: inline-block; margin-right: 5px;" href="https://www.instagram.com/dulwichcollegebeijing/">
                    <img width="25" height="25" src="../assets/socials/instagram.png" alt="">
                  </a>
                  <a style="display: inline-block; margin-right: 5px;" href="https://www.youtube.com/channel/UCPAMYCaLqMLdKSTZWfmL-YQ">
                    <img width="25" height="25" src="../assets/socials/youtube.png" alt="">
                  </a>
                </td>
              </tr>
            </table>
          </td>
        </tr>
        <tr>
          <td>
            <table style="margin: 0; padding: 0;"> <!-- School accreditation -->
              <tr>
                <td style="padding: 0;">
                  <img src="../assets/accreditations/all-accreds.png" alt="">
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
                  <strong>T:</strong> (86 10) 6454 <span v-if="phone_extension">{{ phone_extension}}</span> <span v-else>9000</span> 
                  | <strong>WeChat:</strong> DulwichBeijing
                  <br>
                  89 Capital Airport Road Shunyi District Beijing 101300 PRC
                  <br>
                  北京德威英国国际学校 北京市顺义区首都机场路89号丽京花园7区 邮编：101300
                </td>
              </tr>
            </table>
          </td>
        </tr>
      </table>
    </div>
    <!-- <button>Copy to clipboard</button> -->
  </div>
</template>
<script>
export default {
  name: "Previewer",
  props: ['name_en', 'name_zh', 'title_en', 'title_zh', 'badges', 'phone_extension'],
  methods: {
    getImgUrl(badge_id) {
      return require('../assets/teacher-badges/' + badge_id + '.png')
    }
  }
}
</script>
<style>
  .previewer {
    line-height: 1;
    background: #fff;
    box-shadow: 0 0 8px rgba(0, 0, 0, 0.25);
    color: #3C3737;
    padding: 50px;
    margin-top: 20px;
  }

  .previewer button {
    background-color: #d30013;
    border-radius: 4px;
    border-style: none;
    color: #fff;
    display: inline;
    font-size: 16px;
    font-size: 1rem;
    line-height: 16px;
    margin: 20px 4px 0;
    min-width: 1px;
    padding: 11px 28px 12px;
  }

  .previewer button:hover {
    cursor: pointer;
    background: #9e1422
  }
</style>