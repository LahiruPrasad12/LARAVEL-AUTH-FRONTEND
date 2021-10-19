<template>
  <div>
    Dashboard
  </div>
</template>

<script>
export default {
  // Mema middlware ek api use krnne email verify nati account ekk dashboad ekt yama valakvimatay
  // Meme frontend middleware ek venuvata apita backend middleware ekk unada use kala hakiya
  middleware: ['auth', 'verified'],
  mounted () {

  }
}
</script>
