<template>
  <div class="card">
    <div class="card__avatar">
      <img
        v-if="user.photo"
        class="card__img"
        :src="user.photo"
        alt="avatar"
      >
    </div>
    <p class="card__name">
      {{ user.name }}
    </p>
    <div class="card__about">
      <p class="card__position">
        {{ user.position }}
      </p>
      <div class="card__email tooltip-handler">
        {{ user.email }}
        <div class="tooltip">
          {{ user.email }}
        </div>
      </div>
      <p class="card__phone">
        {{ user.phone }}
      </p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'UserCard',
  props: {
    user: {
      type: Object,
      required: true
    }
  }
}
</script>
