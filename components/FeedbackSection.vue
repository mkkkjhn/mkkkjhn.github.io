<template>
  <div class="wrapper">
    <div class="feedback">
      <h2>Working with POST request</h2>
      <form
        class="feedback__form"
      >
        <div
          class="feedback__wrap"
        >
          <div
            v-if="form.name"
            class="label"
          >
            Your name
          </div>
          <input
            v-model="form.name"
            type="text"
            class="input"
            placeholder="Your name"
            maxlength="60"
          >
          <span></span>
        </div>
        <div class="feedback__wrap">
          <div
            v-if="form.email"
            class="label"
          >
            Email
          </div>
          <input
            v-model="form.email"
            type="text"
            class="input"
            placeholder="Email"
          >
          <p></p>
        </div>
        <div class="feedback__wrap">
          <div
            v-if="form.phone"
            class="label"
          >
            Phone
          </div>
          <input
            v-model="form.phone"
            type="text"
            class="input"
            placeholder="Phone"
          >
          <p></p>
        </div>
        <div class="feedback__radio">
          <p>Select your position</p>
          <div class="feedback__inner">
            <input
              id="positionChoice1"
              v-model="form.position"
              class="radio"
              type="radio"
              name="position"
              value="frontend"
            >
            <label for="positionChoice1">
              Frontend developer
            </label>
          </div>
          <div class="feedback__inner">
            <input
              id="positionChoice2"
              v-model="form.position"
              class="radio"
              type="radio"
              name="position"
              value="frontend"
            >
            <label for="positionChoice2" >
              Backend developer
            </label>
          </div>
          <div class="feedback__inner">
            <input
              id="positionChoice3"
              v-model="form.position"
              class="radio"
              type="radio"
              name="position"
              value="2"
            >
            <label for="positionChoice3">
              Designer
            </label>
          </div>
          <div class="feedback__inner">
            <input
              id="positionChoice4"
              v-model="form.position"
              class="radio"
              type="radio"
              name="position"
              value="frontend"
            >
            <label for="positionChoice4">
              QA
            </label>
          </div>
        </div>
        <div class="feedback__upload">
          <input
            id="file"
            type="file"
            name="file"
            class="inputfile"
            @change="getAttachmentFile"
          >
          <label
            for="file"
            class="btn--upload"
          >
            Upload
          </label>
          <div>
            <p>
              {{ form.files[0] ? form.files[0] : 'Upload your photo' }}
            </p>
          </div>
        </div>
      </form>
      <button
        class="btn--submit"
        :class="{ active: isValidationPassed}"
      >
        Sing Up
      </button>
    </div>
  </div>
</template>

<script>

export default {
  name: 'FeedbackSection',
  data () {
    return {
      form: {
        name: '',
        email: '',
        phone: '',
        position: null,
        files: []
      },
      isValidationPassed: false,
      token: ''
    }
  },
  watch: {
    isUserRegistering () {
      if (this.name || this.email || this.phone) {
        this.getToken()
      }
    }
  },
  methods: {
    getAttachmentFile () {
      this.form.files.push(document.getElementById('file').files[0].name)
    },
    async getToken () {
      try {
        const response = await this.$axios.get('https://frontend-test-assignment-api.abz.agency/api/v1/token')
        this.token = response.data.token
      } catch (e) {
        // eslint-disable-next-line no-console
        console.log(e)
      }
    }
    // submitForm () {
    //   const formData = new FormData()
    //   formData.append('position_id', this.form.position)
    //   formData.append('name', this.form.name)
    //   formData.append('email', this.form.email)
    //   formData.append('phone', this.form.email)
    //   formData.append('photo', this.form.files[0])
    //   fetch('https://frontend-test-assignment-api.abz.agency/api/v1/users', { method: 'POST', body: formData, headers: { 'Token': this.token } })
    //
    // }
  }
}
</script>
