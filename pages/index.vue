<template>
  <div class="py-4 max-w-6xl mx-auto">
    <LazyHydrate when-visible>
      <a-list :loading="loading" item-layout="horizontal" :data-source="data">
        <a-list-item slot="renderItem" slot-scope="item">
          <a slot="actions">Xem</a>
          <a-list-item-meta
            description="Ant Design, a design language for background applications, is refined by Ant UED Team"
          >
            <a slot="title" href="https://www.antdv.com/">{{
              item.name.last
            }}</a>
            <a-avatar slot="avatar" src="/ODTLcjxAfvqbxHnVXCYX.png" />
          </a-list-item-meta>
        </a-list-item>
      </a-list>
    </LazyHydrate>
  </div>
</template>
<script>
const fakeDataUrl =
  'https://randomuser.me/api/?results=55&inc=name,gender,email,nat&noinfo'
import LazyHydrate from 'vue-lazy-hydration'
export default {
  components: { LazyHydrate },
  async asyncData({ $axios }) {
    const data = await $axios.$get(fakeDataUrl)
    return {
      data: data.results,
      loading: false,
    }
  },
  data() {
    return {
      loading: true,
      loadingMore: false,
      showLoadingMore: true,
      data: [],
    }
  },
  methods: {
    onLoadMore() {},
  },
}
</script>
<style>
.py-4 {
  padding: 5rem 0;
}
.max-w-6xl {
  max-width: 990px;
}
.mx-auto {
  margin: 0 auto;
}
</style>
