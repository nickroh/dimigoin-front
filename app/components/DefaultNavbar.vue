<script>
import Brand from '@/assets/brand.svg?inline'

export default {
  name: 'DefaultNavbar',
  components: { Brand },

  methods: {
    async logout () {
      await this.$store.dispatch('account/logout')
      this.$router.push({ name: 'login' })
    }
  }
}
</script>

<template>
  <header>
    <dimi-navbar>
      <router-link
        slot="brand"
        :to="{ name: 'main' }"
        class="brand"
      >
        <brand style="height: 32px;" />
      </router-link>
      <span slot="end">
        {{ $store.state.account.informations.name }}
        <a
          class="icon-logout logout-btn"
          title="로그아웃"
          @click="logout"
        />
      </span>
    </dimi-navbar>
  </header>
</template>

<style lang="scss" scoped>
.brand {
  display: flex;
}

.logout-btn {
  cursor: pointer;
}
</style>
