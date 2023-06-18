<template>
    <cv-accordion>
        <cv-accordion-item v-for="res in resources" :key="res.id">
            <template #title>{{ res.name }}</template>
            <template #content> 
                <resource-content :documentId="res.id" :documentSummary="res.summary" :documentLink="res.link"></resource-content>
            </template>
        </cv-accordion-item>
    </cv-accordion>
</template>

<script>
import ResourceContent from './ResourceContent.vue'

export default {
    name: "ListResources",
    props: ['resources'],
    components: {
        ResourceContent
    }
}
</script>

<style scoped>
div {
  margin: 2rem auto;
  max-width: 40rem;
}
</style>