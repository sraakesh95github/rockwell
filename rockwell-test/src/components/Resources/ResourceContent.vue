<template>
    <div>
        <p> <span class="key">Document ID: </span><span class="value">{{ documentId }}</span></p>

        <p> <span class="key">Document Summary: </span><span class="value">{{ documentSummary }}</span></p>

        <p class="key">Document Link: </p> <a href="documentLink">{{ documentLink }}</a>
    </div>
</template>

<script>
export default {
    props: {
        documentId: String,
        documentSummary: String,
        documentLink: String
    }
}
</script>

<style scoped>

div {
    margin: 0;
}

.key {
    font-weight: bold;
    font-size: 12 px;
}

.value {
    font-size: 10 px;
}
</style>