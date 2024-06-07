<template>
    <section class="title">
        <h1>{{ title }}</h1>
        <h3>{{ subtitle }}</h3>

        <div v-if="authors" class="authors">
            <span v-for="author, i in authors" :key="i">
                <a :href="author.homepage" target="_blank">{{ author.name }}</a>
                <span v-if="i < authors.length - 1">, </span>
            </span>
        </div>

        <div class="res_link">
            <a v-if="resources.pdf" class="button" :href="resources.pdf" target="_blank">
                <i class="iconfont icon-lm-pdf"></i>
                <span>Paper</span>
            </a>
            <a v-if="resources.arxiv" class="button" :href="resources.arxiv" target="_blank">
                <i class="iconfont icon-lm-Arxiv"></i>
                <span>arXiv</span>
            </a>

            <a v-if="resources.github" class="button" :href="resources.github" target="_blank">
                <i class="iconfont icon-lm-github"></i>
                <span>Code</span>
            </a>

            <a v-if="resources.huggingface" class="button" :href="resources.huggingface" target="_blank">
                <i class="iconfont icon-lm-huggingface"></i>
                <span>HuggingFace</span>
            </a>
        </div>

        <video v-lazy :src="mainVideo" muted loop controls></video>
    </section>
</template>

<script lang="ts" setup>
interface Props {
    title?: string,
    subtitle?: string,
    authors?: any[],
    resources?: any,
    mainVideo?: string,
}
const { props } = defineProps<{ props: Props }>()

const title = props.title
const subtitle = props.subtitle
const authors = props.authors
const resources = props.resources
const mainVideo = props.mainVideo && new URL(`../${props.mainVideo}`, import.meta.url).href
</script>

<style lang="scss" scoped>
.title {

    .authors {
        @apply text-center text-lg;
    }

    .res_link {
        @apply text-center mt-1;
    }

    video {
        max-width: 960px;
        @apply mt-4 block w-full;
    }
}

.button {
    @apply mr-3 mt-2;

    i {
        @apply mr-1;
    }
}
</style>
