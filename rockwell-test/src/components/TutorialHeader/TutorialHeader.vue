<template>

    <cv-header aria-label="Carbon tutorial">

        <cv-skip-to-content href="#main-content">Skip to content</cv-skip-to-content>

        <cv-header-name to="/" prefix="Rockwell Automations"></cv-header-name>

        <cv-header-nav>
            <cv-header-menu-item to="/">RASIV Portal</cv-header-menu-item>
        </cv-header-nav>

    </cv-header>
</template>

<script>
export default {
    name: "TutorialHeader"
}
</script>

<style scoped>
.nav-headers {
    font-weight: bold;
}

</style>