<template>
    <v-container>
        {{ faq.title }}
        <nuxt-content :document="faq" />
    </v-container>
</template>
<script>
export default {
    async asyncData ({ $content, route }) {
        const faq = await $content('faq', route.params.slug).fetch()
        return {
            faq
        }
    }
}
</script>