<script setup lang="ts">
const { availableLocales, locale } = useI18n();

// 如果locale为undefined，将其默认为中文
if (!locale) {
  // 此处使用 zh 作为默认语言，你可以根据实际情况调整
  useI18n().locale = 'zh';
}

const localesLong: Record<string, string> = {
  zh: '中文', 
  en: 'English',
  es: 'Español',
  fr: 'Français',
  pt: 'Português',
  ru: 'Русский',
  uk: 'Українська',
};

const localeOptions = computed(() =>
  availableLocales.map(locale => ({
    label: localesLong[locale] ?? locale,
    value: locale,
  })),
);
</script>

<template>
  <c-select
    v-model:value="locale"
    :options="localeOptions"
    placeholder="Select a language"
    w-100px
  />
</template>
