<template>
  <div class="wrapper">
    <div class="squad">
      <h2>Working with GET request</h2>
      <div
        :class="{ active: isLoading }"
        class="squad__cards"
      >
        <template v-if="isLoading">
          <UiPreloader />
        </template>
        <template v-if="!isLoading">
          <user-card
            v-for="user in users"
            :key="user.id"
            class="squad__faces"
            :user="user"
          />
        </template>
      </div>
      <button class="btn">
        Show more
      </button>
    </div>
  </div>
</template>

<script>
import UserCard from '~/components/common/UserCard.vue'
import UiPreloader from '~/components/common/UiPreloader.vue'
export default {
  name: 'SquadSection',
  components: {
    UserCard,
    UiPreloader
  },
  data () {
    return {
      users: [],
      isLoading: false
    }
  },
  mounted () {
    this.getUsersData()
  },
  methods: {
    async getUsersData () {
      this.isLoading = true
      try {
        const response = await this.$axios.get('https://frontend-test-assignment-api.abz.agency/api/v1/users', {
          params: {
            count: 6
          }
        })
        this.users = response.data.users
      } catch (e) {
        // eslint-disable-next-line no-console
        console.log(e)
      } finally {
        this.isLoading = false
      }
    }
  }
}
</script>
