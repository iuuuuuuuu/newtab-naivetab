<script setup lang="ts">
import { URL_DAYJS_FORMAT } from '@/logic/const'
import { localConfig } from '@/logic/store'
import BaseComponentSetting from '@/newtab/components/form/BaseComponentSetting.vue'
import Tips from '@/newtab/components/form/Tips.vue'
</script>

<template>
  <BaseComponentSetting cname="clockDigital">
    <template #header>
      <NFormItem :label="$t('common.format')">
        <NInput v-model:value="localConfig.clockDigital.format" />
        <Tips
          link
          :content="URL_DAYJS_FORMAT"
        />
      </NFormItem>
      <NFormItem :label="$t('clock.apMark')">
        <NSwitch v-model:value="localConfig.clockDigital.unitEnabled" />
        <NSlider
          v-if="localConfig.clockDigital.unitEnabled"
          v-model:value="localConfig.clockDigital.unit.fontSize"
          class="setting__item-element"
          :step="1"
          :min="5"
          :max="200"
          :tooltip="false"
        />
        <NInputNumber
          v-if="localConfig.clockDigital.unitEnabled"
          v-model:value="localConfig.clockDigital.unit.fontSize"
          class="setting__item-element setting__input-number"
          :min="5"
          :step="1"
        />
      </NFormItem>
    </template>
  </BaseComponentSetting>
</template>
