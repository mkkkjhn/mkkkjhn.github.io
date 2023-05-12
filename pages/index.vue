<template>
  <main>
    <header-section />
    <about-section />
    <squad-section />
    <feedback-section />
  </main>
</template>

<script>
import HeaderSection from '~/components/HeaderSection.vue'
import AboutSection from '~/components/AboutSection.vue'
import SquadSection from '~/components/SquadSection.vue'
import FeedbackSection from '~/components/FeedbackSection.vue'
export default {
  name: 'IndexPage',
  components: {
    HeaderSection,
    AboutSection,
    SquadSection,
    FeedbackSection
  }
}
</script>
