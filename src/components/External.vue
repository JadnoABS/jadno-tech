

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
header {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    height: 100%;
}

.link {
    font-size: x-large;
    margin: 0.5em 0;
    padding: 0.5em;
    cursor: pointer;
    text-align: center;
    word-wrap: break-word;
}

.link:hover {
    color: #570000;
}

.external {
    font-size: x-small;
}

@media (max-width: 1125px) {
    .link {
        font-size: large;
        margin: 0.4em 0;
        padding: 0.4em;
    }
}

@media (max-width: 714px) {
    .link {
        font-size: medium;
        margin: 0.3em 0;
        padding: 0.3em;
    }
}
</style>