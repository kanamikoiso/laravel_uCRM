<script setup>
import { computed } from 'vue';
import { usePage } from '@inertiajs/inertia-vue3';

// `usePage` の結果を確認する
const page = usePage();

// `errors` プロパティの存在確認とデフォルト値設定
const errors = computed(() => page.props.value?.errors || {});

const hasErrors = computed(() => Object.keys(errors.value).length > 0);
</script>

<template>
    <div v-if="hasErrors">
        <div class="font-medium text-red-600">問題が発生しました。</div>

        <ul class="mt-3 list-disc list-inside text-sm text-red-600">
            <li v-for="(error, key) in errors" :key="key">{{ error }}</li>
        </ul>
    </div>
</template>