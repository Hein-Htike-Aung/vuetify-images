<script setup>
import { defineEmits } from "vue";

const emits = defineEmits(["selectOption"]);

const selectOption = (isColor) => {
  emits("selectOption", isColor);
};
</script>

<template>
  <VNavigationDrawer expand-on-hover rail>
    <VList>
      <VListItem
        prepend-avatar="https://randomuser.me/api/portraits/women/85.jpg"
        title="Kazuha"
        subtitle="kazuha@gmailcom"
      ></VListItem>
    </VList>

    <VDivider></VDivider>

    <VList density="compact" nav>
      <VListItem
        @click="selectOption(true)"
        prepend-icon="mdi-image"
        title="Color Gallery"
        value="color"
      />
      <VListItem
        @click="selectOption(false)"
        prepend-icon="mdi-dialpad"
        title="Grayspace Gallery"
        value="color"
      />
    </VList>
  </VNavigationDrawer>
</template>
