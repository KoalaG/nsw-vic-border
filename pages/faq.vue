<template>
    <v-container>
        <v-expansion-panels>
            <v-expansion-panel v-for="(faq,i) in faqs" :key="i">
                <v-expansion-panel-header>{{ faq.title }}</v-expansion-panel-header>
                <v-expansion-panel-content>
                    <nuxt-content :document="faq" />
                </v-expansion-panel-content>
            </v-expansion-panel>
        </v-expansion-panels>
    </v-container>
</template>
<script>
export default {
    async asyncData ({ $content }) {
        const faqs = await $content('faq').fetch()
        return {
            faqs
        }
    }
}
</script>