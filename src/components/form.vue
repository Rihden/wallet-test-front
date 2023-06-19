<template>
  <!-- Hire Us -->
  <div class="max-w-[85rem] px-4 py-10 sm:px-6 lg:px-8 lg:py-14 mx-auto">
    <div class="max-w-xl mx-auto">
      <div class="text-center">
        <h1 class="text-3xl font-bold text-gray-800 sm:text-4xl dark:text-white">
          Generate business your card
        </h1>
        <p class="mt-1 text-gray-600 dark:text-gray-400">Add your business card info</p>
      </div>

      <div class="text-center mt-6">
        <p class="font-bold text-red-500 dark:text-red-300">
          {{ errorMessages[0] || '&nbsp;' }}
        </p>
      </div>

      <div class="mt-6">
        <!-- Form -->
        <form>
          <div class="grid gap-4 lg:gap-6">
            <!-- Grid -->
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 lg:gap-6">
              <div>
                <label
                  for="hs-firstname-hire-us-2"
                  class="block text-sm text-gray-700 font-medium dark:text-white"
                  >First Name</label
                >
                <input
                  type="text"
                  name="hs-firstname-hire-us-2"
                  id="hs-firstname-hire-us-2"
                  class="py-3 px-4 block w-full border-gray-200 border-solid border rounded-md text-sm focus:border-blue-500 focus:ring-blue-500 dark:bg-slate-900 dark:border-gray-700 dark:text-gray-400"
                  :class="{
                    'border-red-400': errors.firstName,
                    'border-2': errors.firstName
                  }"
                  v-model="userData.firstName"
                />
              </div>

              <div>
                <label
                  for="hs-lastname-hire-us-2"
                  class="block text-sm text-gray-700 font-medium dark:text-white"
                  >Last Name</label
                >
                <input
                  type="text"
                  name="hs-lastname-hire-us-2"
                  id="hs-lastname-hire-us-2"
                  class="py-3 px-4 block w-full border-gray-200 border border-solid rounded-md text-sm focus:border-blue-500 focus:ring-blue-500 dark:bg-slate-900 dark:border-gray-700 dark:text-gray-400"
                  :class="{
                    'border-red-400': errors.lastName,
                    'border-2': errors.lastName
                  }"
                  v-model="userData.lastName"
                />
              </div>
            </div>
            <!-- End Grid -->

            <div>
              <label
                for="hs-work-email-hire-us-2"
                class="block text-sm text-gray-700 font-medium dark:text-white"
                >Work Email</label
              >
              <input
                type="email"
                name="hs-work-email-hire-us-2"
                id="hs-work-email-hire-us-2"
                autocomplete="email"
                class="py-3 px-4 block w-full border-gray-200 border border-solid rounded-md text-sm focus:border-blue-500 focus:ring-blue-500 dark:bg-slate-900 dark:border-gray-700 dark:text-gray-400"
                v-model="userData.email"
                :class="{
                  'border-red-400': errors.email,
                  'border-2': errors.email
                }"
              />
            </div>

            <!-- Grid -->
            <div class="grid grid-cols-1 sm:grid-cols-2 gap-4 lg:gap-6">
              <div>
                <label
                  for="hs-company-hire-us-2"
                  class="block text-sm text-gray-700 font-medium dark:text-white"
                  >Company</label
                >
                <input
                  type="text"
                  name="hs-company-hire-us-2"
                  id="hs-company-hire-us-2"
                  class="py-3 px-4 block w-full border-gray-200 border border-solid rounded-md text-sm focus:border-blue-500 focus:ring-blue-500 dark:bg-slate-900 dark:border-gray-700 dark:text-gray-400"
                  v-model="userData.company"
                  :class="{
                    'border-red-400': errors.company,
                    'border-2': errors.company
                  }"
                />
              </div>

              <div>
                <label
                  for="hs-company-website-hire-us-2"
                  class="block text-sm text-gray-700 font-medium dark:text-white"
                  >Company Website</label
                >
                <input
                  type="text"
                  name="hs-company-website-hire-us-2"
                  id="hs-company-website-hire-us-2"
                  class="py-3 px-4 block w-full border-gray-200 border border-solid rounded-md text-sm focus:border-blue-500 focus:ring-blue-500 dark:bg-slate-900 dark:border-gray-700 dark:text-gray-400"
                  v-model="userData.companyWebsite"
                  :class="{
                    'border-red-400': errors.companyWebsite,
                    'border-2': errors.companyWebsite
                  }"
                  @input="hanleWebsitePrefix()"
                />
              </div>
            </div>
            <!-- End Grid -->

            <div>
              <label
                for="hs-work-email-hire-us-2"
                class="block text-sm text-gray-700 font-medium dark:text-white"
                >Phone Number</label
              >
              <input
                type="email"
                name="hs-work-email-hire-us-2"
                id="hs-work-email-hire-us-2"
                autocomplete="email"
                class="py-3 px-4 block w-full border-gray-200 border border-solid rounded-md text-sm focus:border-blue-500 focus:ring-blue-500 dark:bg-slate-900 dark:border-gray-700 dark:text-gray-400"
                v-model="userData.phone"
                :class="{
                  'border-red-400': errors.phone,
                  'border-2': errors.phone
                }"
              />
            </div>
          </div>
          <!-- End Grid -->

          <div class="mt-12 flex justify-center items-end gap-3">
            <button
              class="text-center bg-blue-600 hover:bg-blue-700 border border-transparent text-sm lg:text-base text-white font-medium rounded-md focus:outline-none focus:ring-2 focus:ring-blue-600 focus:ring-offset-2 focus:ring-offset-white transition py-3 px-4 dark:focus:ring-offset-gray-800"
              @click="handleQRCreattion($event)"
            >
              Generate QR
            </button>
            <button
              class="text-center bg-gray-400 hover:bg-gray-700 border border-transparent text-sm lg:text-base text-white font-medium rounded-md focus:outline-none focus:ring-2 focus:ring-gray-600 focus:ring-offset-2 focus:ring-offset-white transition py-3 px-4 dark:focus:ring-offset-gray-800"
              @click="handleVKCreattion($event)"
            >
              Generate Card
            </button>
          </div>

          <div class="mt-3 text-center">
            <p class="text-sm text-gray-500">
              Scan the QR code to add your business card to your wallet.
            </p>
          </div>
        </form>
        <!-- End Form -->
      </div>
    </div>

    <div
      class="hs-overlay w-full h-full fixed top-0 left-0 z-[60] overflow-x-hidden overflow-y-auto"
      style="background-color: #00000066"
      v-if="isShowingOverlay"
    >
      <div
        class="hs-overlay-open:mt-7 hs-overlay-open:duration-500 mt-0 ease-out transition-all sm:max-w-lg sm:w-full m-3 sm:mx-auto min-h-[calc(100%-3.5rem)] flex items-center"
        v-if="isShowingPDF"
      >
        <div
          class="flex flex-col bg-white border shadow-sm rounded-xl dark:bg-gray-800 dark:border-gray-700 dark:shadow-slate-700/[.7]"
        >
          <div class="flex justify-between items-center py-3 px-4 border-b dark:border-gray-700">
            <h3 class="font-bold text-gray-800 dark:text-white">Business card</h3>
            <button
              type="button"
              class="hs-dropdown-toggle inline-flex flex-shrink-0 justify-center items-center h-8 w-8 rounded-md text-gray-500 hover:text-gray-400 focus:outline-none focus:ring-2 focus:ring-gray-400 focus:ring-offset-2 focus:ring-offset-white transition-all text-sm dark:focus:ring-gray-700 dark:focus:ring-offset-gray-800"
              data-hs-overlay="#hs-vertically-centered-modal"
              @click="hidePDF()"
            >
              <span class="sr-only">Close</span>
              <svg
                class="w-3.5 h-3.5"
                width="8"
                height="8"
                viewBox="0 0 8 8"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M0.258206 1.00652C0.351976 0.912791 0.479126 0.860131 0.611706 0.860131C0.744296 0.860131 0.871447 0.912791 0.965207 1.00652L3.61171 3.65302L6.25822 1.00652C6.30432 0.958771 6.35952 0.920671 6.42052 0.894471C6.48152 0.868271 6.54712 0.854471 6.61352 0.853901C6.67992 0.853321 6.74572 0.865971 6.80722 0.891111C6.86862 0.916251 6.92442 0.953381 6.97142 1.00032C7.01832 1.04727 7.05552 1.1031 7.08062 1.16454C7.10572 1.22599 7.11842 1.29183 7.11782 1.35822C7.11722 1.42461 7.10342 1.49022 7.07722 1.55122C7.05102 1.61222 7.01292 1.6674 6.96522 1.71352L4.31871 4.36002L6.96522 7.00648C7.05632 7.10078 7.10672 7.22708 7.10552 7.35818C7.10442 7.48928 7.05182 7.61468 6.95912 7.70738C6.86642 7.80018 6.74102 7.85268 6.60992 7.85388C6.47882 7.85498 6.35252 7.80458 6.25822 7.71348L3.61171 5.06702L0.965207 7.71348C0.870907 7.80458 0.744606 7.85498 0.613506 7.85388C0.482406 7.85268 0.357007 7.80018 0.264297 7.70738C0.171597 7.61468 0.119017 7.48928 0.117877 7.35818C0.116737 7.22708 0.167126 7.10078 0.258206 7.00648L2.90471 4.36002L0.258206 1.71352C0.164476 1.61976 0.111816 1.4926 0.111816 1.36002C0.111816 1.22744 0.164476 1.10028 0.258206 1.00652Z"
                  fill="currentColor"
                />
              </svg>
            </button>
          </div>
          <div class="p-4 overflow-y-auto">
            <iframe ref="my_iframe" width="420px" height="640px" :src="pdfFile"></iframe>
          </div>
          <div
            class="flex justify-end items-center gap-x-2 py-3 px-4 border-t dark:border-gray-700"
          >
            <button
              type="button"
              class="hs-dropdown-toggle py-3 px-4 inline-flex justify-center items-center gap-2 rounded-md border font-medium bg-white text-gray-700 shadow-sm align-middle hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-white focus:ring-blue-600 transition-all text-sm dark:bg-slate-900 dark:hover:bg-slate-800 dark:border-gray-700 dark:text-gray-400 dark:hover:text-white dark:focus:ring-offset-gray-800"
              data-hs-overlay="#hs-vertically-centered-modal"
              @click="hidePDF()"
            >
              Close
            </button>
            <a
              class="py-3 px-4 inline-flex justify-center items-center gap-2 rounded-md border border-transparent font-semibold bg-blue-500 text-white hover:bg-blue-600 focus:outline-none focus:ring-2 focus:ring-blue-500 focus:ring-offset-2 transition-all text-sm dark:focus:ring-offset-gray-800"
              :href="`${pdfFile}`"
              download="business card.pdf"
              target="_blank"
            >
              Download
            </a>
          </div>
        </div>
      </div>
      <div
        class="hs-overlay-open:mt-7 hs-overlay-open:duration-500 mt-0 ease-out transition-all sm:max-w-lg sm:w-full m-3 sm:mx-auto min-h-[calc(100%-3.5rem)] flex items-center justify-center"
        v-if="isShowingQROptions"
      >
        <div
          class="flex flex-col bg-white border shadow-sm rounded-xl dark:bg-gray-800 dark:border-gray-700 dark:shadow-slate-700/[.7]"
        >
          <div class="flex justify-between items-center py-3 px-4 border-b dark:border-gray-700">
            <h3 class="font-bold text-gray-800 dark:text-white">Wallet pass</h3>
            <button
              type="button"
              class="hs-dropdown-toggle inline-flex flex-shrink-0 justify-center items-center h-8 w-8 rounded-md text-gray-500 hover:text-gray-400 focus:outline-none focus:ring-2 focus:ring-gray-400 focus:ring-offset-2 focus:ring-offset-white transition-all text-sm dark:focus:ring-gray-700 dark:focus:ring-offset-gray-800"
              data-hs-overlay="#hs-vertically-centered-modal"
              @click="hideQROptions()"
            >
              <span class="sr-only">Close</span>
              <svg
                class="w-3.5 h-3.5"
                width="8"
                height="8"
                viewBox="0 0 8 8"
                fill="none"
                xmlns="http://www.w3.org/2000/svg"
              >
                <path
                  d="M0.258206 1.00652C0.351976 0.912791 0.479126 0.860131 0.611706 0.860131C0.744296 0.860131 0.871447 0.912791 0.965207 1.00652L3.61171 3.65302L6.25822 1.00652C6.30432 0.958771 6.35952 0.920671 6.42052 0.894471C6.48152 0.868271 6.54712 0.854471 6.61352 0.853901C6.67992 0.853321 6.74572 0.865971 6.80722 0.891111C6.86862 0.916251 6.92442 0.953381 6.97142 1.00032C7.01832 1.04727 7.05552 1.1031 7.08062 1.16454C7.10572 1.22599 7.11842 1.29183 7.11782 1.35822C7.11722 1.42461 7.10342 1.49022 7.07722 1.55122C7.05102 1.61222 7.01292 1.6674 6.96522 1.71352L4.31871 4.36002L6.96522 7.00648C7.05632 7.10078 7.10672 7.22708 7.10552 7.35818C7.10442 7.48928 7.05182 7.61468 6.95912 7.70738C6.86642 7.80018 6.74102 7.85268 6.60992 7.85388C6.47882 7.85498 6.35252 7.80458 6.25822 7.71348L3.61171 5.06702L0.965207 7.71348C0.870907 7.80458 0.744606 7.85498 0.613506 7.85388C0.482406 7.85268 0.357007 7.80018 0.264297 7.70738C0.171597 7.61468 0.119017 7.48928 0.117877 7.35818C0.116737 7.22708 0.167126 7.10078 0.258206 7.00648L2.90471 4.36002L0.258206 1.71352C0.164476 1.61976 0.111816 1.4926 0.111816 1.36002C0.111816 1.22744 0.164476 1.10028 0.258206 1.00652Z"
                  fill="currentColor"
                />
              </svg>
            </button>
          </div>
          <div
            class="p-4 overflow-y-auto flex flex-col items-center justify-center text-center gap-4 md:flex-row"
          >
            <a :href="`${passUrl}`"><img style="max-width: 250px" src="/wallet-button.png" /></a>
            <p>or</p>
            <img :src="QRurl" alt="QR Code for wallet pass" style="max-width: 200px" />
          </div>
          <div
            class="flex justify-end items-center gap-x-2 py-3 px-4 border-t dark:border-gray-700"
          >
            <button
              type="button"
              class="hs-dropdown-toggle py-3 px-4 inline-flex justify-center items-center gap-2 rounded-md border font-medium bg-white text-gray-700 shadow-sm align-middle hover:bg-gray-50 focus:outline-none focus:ring-2 focus:ring-offset-2 focus:ring-offset-white focus:ring-blue-600 transition-all text-sm dark:bg-slate-900 dark:hover:bg-slate-800 dark:border-gray-700 dark:text-gray-400 dark:hover:text-white dark:focus:ring-offset-gray-800"
              data-hs-overlay="#hs-vertically-centered-modal"
              @click="hideQROptions()"
            >
              Close
            </button>
          </div>
        </div>
      </div>
      <div class="flex justify-center items-center h-full flex-col" v-if="isLoading">
        <span class="loader"></span>
        <p class="text-white">Generating Pdf...</p>
      </div>
    </div>
  </div>
  <!-- End Hire Us -->
</template>
<script>
import axios from 'axios'
import Vue3Toasity from 'vue3-toastify'
export default {
  data() {
    return {
      qrData: '',
      pdfFile: '',
      userData: {
        firstName: '',
        lastName: '',
        email: '',
        company: '',
        companyWebsite: '',
        phone: ''
      },
      errors: {
        firstName: false,
        lastName: false,
        phone: false,
        company: false,
        companyWebsite: false,
        email: false
      },
      errorMessages: [],
      formError: false,
      isShowingOverlay: false,
      isLoading: false,
      isShowingPDF: false,
      passUrl: ''
    }
  },
  methods: {
    handleQRCreattion: async function (e) {
      e.preventDefault()
      this.validateFields()
      try {
        if (!this.formError) {
          this.isLoading = true
          this.isShowingOverlay = true
          const result = await axios.post(
            'https://wallet-test-pc3j.onrender.com/users/QRpass',
            this.userData
          )
          this.isLoading = false
          this.passUrl = result.data.passUrl
          this.QRurl = `https://api.qrserver.com/v1/create-qr-code/?size=900x900&data=https://wallet-test-pc3j.onrender.com/url/${result.data.QRUrl}`
          this.showQROptions()
        }
      } catch (error) {
        this.isLoading = false
        this.isShowingOverlay = false

        console.log(error)
      }
    },
    handleVKCreattion: async function (e) {
      e.preventDefault()
      this.validateFields()
      try {
        if (!this.formError) {
          this.isLoading = true
          this.isShowingOverlay = true
          const result = await axios.post(
            'https://wallet-test-pc3j.onrender.com/users',
            this.userData
          )
          this.isLoading = false
          this.isShowingPDF = true
          this.pdfFile = result.data

          console.log(result)
        }
      } catch (error) {
        this.isLoading = false
        console.log(error)
      }
    },
    hidePDF: function () {
      this.isShowingOverlay = false
      this.isShowingPDF = false
    },
    showQROptions: function () {
      this.isShowingOverlay = true
      this.isShowingQROptions = true
    },
    hideQROptions: function () {
      this.isShowingOverlay = false
      this.isShowingQROptions = false
    },
    validateFields: function () {
      const alphabetic = /^[A-Za-z\s]*$/
      const alphanumeric = /^[\w\-\s]+$/
      const numeric = /^\+?[0-9\s]*$/
      const emailRegex = /^[\w-\.]+@([\w-]+\.)+[\w-]{2,4}$/g
      this.formError = false
      for (const [key, value] of Object.entries(this.errors)) {
        this.errors[key] = false
      }
      this.errorMessages = new Array()

      if (this.userData.firstName === '') {
        this.formError = true
        this.errors.firstName = true
        this.errorMessages.push('First Name is required.')
      } else if (!alphabetic.test(this.userData.firstName)) {
        this.formError = true
        this.errors.firstName = true
        this.errorMessages.push('First Name may only contain alphabetic characters.')
      }

      if (this.userData.lastName === '') {
        this.formError = true
        this.errors.lastName = true
        this.errorMessages.push('Last Name is required.')
      } else if (!alphabetic.test(this.userData.lastName)) {
        this.formError = true
        this.errors.lastName = true
        this.errorMessages.push('Last Name may only contain alphabetic characters.')
      }

      if (this.userData.email === '') {
        this.formError = true
        this.errors.email = true
        this.errorMessages.push('Email is required.')
      } else if (!emailRegex.test(this.userData.email)) {
        this.formError = true
        this.errors.email = true
        this.errorMessages.push('Please enter a valid email.')
      }

      if (this.userData.company === '') {
        this.formError = true
        this.errors.company = true
        this.errorMessages.push('Company is required.')
      } else if (!alphanumeric.test(this.userData.company)) {
        this.formError = true
        this.errors.company = true
        this.errorMessages.push('Company may only contain alphanumeric characters.')
      }
      if (this.userData.companyWebsite === '') {
        this.errorMessages.push('Company website is required.')
        this.formError = true
        this.errors.companyWebsite = true
      }
      if (this.userData.phone === '') {
        this.formError = true
        this.errors.phone = true
        this.errorMessages.push('Phone number is required.')
      } else if (!numeric.test(this.userData.phone)) {
        this.formError = true
        this.errors.phone = true
        this.errorMessages.push('Please enter a valid phone number.')
      }
    }
  }
}
</script>
<style scoped>
.loader {
  width: 48px;
  height: 48px;
  border-radius: 50%;
  position: relative;
  animation: rotate 1s linear infinite;
}
.loader::before,
.loader::after {
  content: '';
  box-sizing: border-box;
  position: absolute;
  inset: 0px;
  border-radius: 50%;
  border: 5px solid #fff;
  animation: prixClipFix 2s linear infinite;
}
.loader::after {
  border-color: #48a5f1;
  animation: prixClipFix 2s linear infinite, rotate 0.5s linear infinite reverse;
  inset: 6px;
}

@keyframes rotate {
  0% {
    transform: rotate(0deg);
  }
  100% {
    transform: rotate(360deg);
  }
}

@keyframes prixClipFix {
  0% {
    clip-path: polygon(50% 50%, 0 0, 0 0, 0 0, 0 0, 0 0);
  }
  25% {
    clip-path: polygon(50% 50%, 0 0, 100% 0, 100% 0, 100% 0, 100% 0);
  }
  50% {
    clip-path: polygon(50% 50%, 0 0, 100% 0, 100% 100%, 100% 100%, 100% 100%);
  }
  75% {
    clip-path: polygon(50% 50%, 0 0, 100% 0, 100% 100%, 0 100%, 0 100%);
  }
  100% {
    clip-path: polygon(50% 50%, 0 0, 100% 0, 100% 100%, 0 100%, 0 0);
  }
}
</style>
