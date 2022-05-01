<template>
  <modal
    :overlay="30"
    :is-open="isBannerOpen"
    position="bottom"
    @close="closeBanner"
  >
    <div class="p-6 md:px-24">
      <header class="flex flex-col items-center mb-4">
        <div class="transform -rotate-45 mb-4">
          <span class="material-icons text-6xl"> settings_input_svideo </span>
        </div>
        <h2 class="font-bold text-2xl">Disclaimer</h2>
      </header>
      <main class="font-light max-w-2xl text-center mb-8">
<p> This website has been designed only for the purposes of dissemination of basic information on _____; information which is otherwise available on the internet, various public platforms and social media. Careful attention has been given to ensure that the information provided herein is accurate and up-to-date. However, we are not responsible for any reliance that a reader places on such information and shall not be liable for any loss or damage caused due to any inaccuracy in or exclusion of any information, or its interpretation thereof. Reader is advised to confirm the veracity of the same from independent and expert sources.</p>

<p> This website is not an attempt to advertise or solicit clients, and does not seek to create or invite any lawyer-client relationship. The links provided on this website are to facilitate access to basic information on ____, and to share the various thought leadership initiatives undertaken by it. The content herein or on such links should not be construed as a legal reference or legal advice. Readers are advised not to act on any information contained herein or on the links and should refer to legal counsels and experts in their respective jurisdictions for further information and to determine its impact.</p>

<p> We advise against the use of the communication platform provided on this website for exchange of any confidential, business or politically sensitive information. User is requested to use his or her judgment and exchange of any such information shall be solely at the user’s risk.</p>

<p> We use cookies on this website to improve its usability. This helps us in providing a good user experience and to also help in improving our website. By continuing to use our website without changing your privacy settings, you agree to use our cookies.</p>
        <nuxt-link to="/policies/privacy">privacy policy</nuxt-link>.
      </main>
      <footer class="text-center">
      <span>
        <sk-button secondary @click="closeBanner">Accept</sk-button>
        </span>

        <span>
        <sk-button   to="https://github.com/stormkit-io/www-stormkit-io"
        >Decline</sk-button>
        </span>
      </footer>
    </div>
  </modal>
</template>
<script>
import Modal from '../atoms/Modal'
import SkButton from '../atoms/Button'

const LOCAL_STORAGE_KEY = 'gdpr-banner-is-closed'

export default {
  components: {
    Modal,
    SkButton,
  },
  data() {
    return {
      isBannerOpen: false,
    }
  },
  mounted() {
    if (localStorage.getItem(LOCAL_STORAGE_KEY) !== 'true') {
      setTimeout(() => (this.isBannerOpen = true), 1000)
    }
  },
  methods: {
    closeBanner() {
      this.isBannerOpen = false
      localStorage.setItem(LOCAL_STORAGE_KEY, 'true')
    },
  },
}
</script>
