<template>
  <div>
    <bounce-loader
      :loading="isLoadig"
      :color="'#68d391'"
      :size="100"
    ></bounce-loader>
    <px-assets-table v-if="!isLoadig" :assets="assets" />
  </div>
</template>

<script>
import api from "@/api"
import PxAssetsTable from "@/components/PxAssetsTable"

export default {
  name: "Home",

  components: {
    PxAssetsTable
  },

  data() {
    return {
      isLoadig: false,
      assets: []
    }
  },

  created() {
    this.isLoadig = true

    api
      .getAssets()
      .then(assets => (this.assets = assets))
      .finally(() => (this.isLoadig = false))
  }
}
</script>
