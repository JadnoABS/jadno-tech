

<template>
    <header>
        <div class="link" @click="openExternalLink('/Currículo Jadno Barbosa.pdf')">
            <font-awesome-icon :icon="['fas', 'file']"/>
            <span class="link-text">
                Currículo
                <font-awesome-icon :icon="['fas', 'arrow-up-right-from-square']" class="external" />
            </span>
        </div>
        <div class="link" @click="openExternalLink('https://www.github.com/JadnoABS')">
            <font-awesome-icon :icon="['fab', 'github']" />
            <span class="link-text">
                JadnoABS
                <font-awesome-icon :icon="['fas', 'arrow-up-right-from-square']" class="external" />
            </span>
        </div>
        <div class="link" @click="openExternalLink('https://www.linkedin.com/in/jadno-barbosa')">
            <font-awesome-icon :icon="['fab', 'linkedin']" />
            <span class="link-text">
                jadno-barbosa
                <font-awesome-icon :icon="['fas', 'arrow-up-right-from-square']" class="external" />
            </span>
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
        display: flex;
        flex-direction: column;
        align-items: center;
        gap: 5px;
    }

    .link-text {
        display: flex;
        align-items: center;
        gap: 5px;
    }

    header {
        flex-direction: row;
        align-items: flex-start;
        justify-content: space-evenly;
        gap: 1rem;
        width: 100%;
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