<template>
  <div class="space-y-10">
    <div class="space-y-2">
    <h2 class="text-2xl font-bold tracking-wider text-primary">
      {{
        $store.state.near.user ? $store.state.near.user.accountId : "My Profile"
      }}
    </h2>
    <p>
      {{
        $store.state.near.user ? $store.state.near.user.balance+' Ⓝ' : ""
      }}
    </p>
  </div>
<div class="w-full h-px bg-paragraph"/>
    <div class="space-y-5">
      <h2 class="text-xl font-bold tracking-wider text-primary">Create Item</h2>
      <CreateItem class="h-80" />
    </div>

    <div class="space-y-5">
      <h2 class="text-xl font-bold tracking-wider text-primary">My Album</h2>
      <AlbumList
        :list="$store.state.items.own"
        v-if="$store.state.items.own.length > 0"
      />
      <p v-else>You haven't created any album yet.</p>
    </div>
  </div>
</template>

<script>
export default {
  async beforeCreate() {
    await this.$store.dispatch("items/own");
  },
};
</script>

<style>
</style>