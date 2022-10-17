<script setup>
import { defineProps } from "vue";

const { isWithColor } = defineProps(["isWithColor"]);

const copyUrl = async (url) => {
  await navigator.clipboard.writeText(url);
};
</script>

<template>
  <VCard class="mx-5 my-2 pa-5">
    <VRow>
      <VCol cols="4" sm="4" md="4" lg="2" v-for="n in 200" :key="n">
        <VHover v-slot="{ isHovering, props }">
          <VCard
            :elevation="isHovering ? 12 : 2"
            v-bind="props"
            @click="
              copyUrl(
                `https://picsum.photos/500/300?image=${n * 5 + 10}${
                  isWithColor ? '' : '&grayscale'
                }`
              )
            "
          >
            <VImg
              :src="`https://picsum.photos/500/300?image=${n * 5 + 10}${
                isWithColor ? '' : '&grayscale'
              }`"
              :lazy-src="`https://picsum.photos/10/6?image=${n * 5 + 10}${
                isWithColor ? '' : '&grayscale'
              }`"
              aspect="1"
              cover
            >
              <!-- Loading Animation -->
              <template v-slot:placeholder>
                <VRow class="fill-height ma-0" align="center" justify="center">
                  <VProgressCircular
                    indeterminate
                    color="grey-lighten-5"
                  ></VProgressCircular>
                </VRow>
              </template>
            </VImg>
          </VCard>
        </VHover>
      </VCol>
    </VRow>
  </VCard>
</template>
