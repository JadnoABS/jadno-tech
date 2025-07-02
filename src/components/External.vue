

<template>
    <header>
        <div class="link" @click="openExternalLink('/Currículo Jadno Barbosa.pdf')">
            <font-awesome-icon :icon="['fas', 'file']"/>
            Currículo
            <font-awesome-icon :icon="['fas', 'arrow-up-right-from-square']" class="external" />
        </div>
        <div class="link" @click="openExternalLink('https://www.github.com/JadnoABS')">
            <font-awesome-icon :icon="['fab', 'github']" />
            JadnoABS
            <font-awesome-icon :icon="['fas', 'arrow-up-right-from-square']" class="external" />
        </div>
        <div class="link" @click="openExternalLink('https://www.linkedin.com/in/jadno-barbosa')">
            <font-awesome-icon :icon="['fab', 'linkedin']" />
            jadno-barbosa
            <font-awesome-icon :icon="['fas', 'arrow-up-right-from-square']" class="external" />
        </div>
    </header>
</template>

<script lang="ts">
export default {
    name: "External",
    methods: {
        openExternalLink(url: string) {
            window.open(url, "_blank");
        }
    }
}
</script>

<style scoped>
.link {
    font-size: x-large;
    margin: 0.5em 0;
    padding: 0.5em;
}

.link:hover {
    color: #570000;
}

.external {
    font-size: x-small;
}
</style>