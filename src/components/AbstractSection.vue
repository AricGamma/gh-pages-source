<template>
    <section class="abstract">
        <div>
            <h3>Abstract</h3>
            <p>{{ props.content }}</p>
        </div>
    </section>
</template>

<script setup lang="ts">
interface Props {
    content?: string
}
const { props } = defineProps<{ props: Props }>()

</script>

<style lang="scss" scoped>
.abstract {
    div {
        max-width: 960px;
        @apply w-full mt-2;
    }

    li {
        @apply flex flex-row my-1;

        :first-child {
            @apply mr-2;
        }
    }
}
</style>