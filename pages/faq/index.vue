<template>
    <v-container>
        <v-expansion-panels>
            <v-expansion-panel v-for="(faq,i) in faqs" :key="i">
                <v-expansion-panel-header>
                    <b>{{ faq.title }}</b>
                </v-expansion-panel-header>
                <v-expansion-panel-content>
                    <nuxt-content :document="faq" />
                    <nuxt-link :to="{ name: 'faq', params: { slug: faq.slug } }">Read More</nuxt-link>
                </v-expansion-panel-content>
            </v-expansion-panel>
        </v-expansion-panels>
    </v-container>
</template>
<script>
export default {
    data () {
        return {
            query: '',
            faqs: [],
        }
    },
    async asyncData ({ $content, route }) {
        const faqs = await $content('faq').fetch()
        return {
            faqs
        }
    }
}
</script>