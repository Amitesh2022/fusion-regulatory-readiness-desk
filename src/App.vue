<script setup lang="ts">
import { onMounted } from 'vue'
import { storeToRefs } from 'pinia'
import { RouterLink, RouterView } from 'vue-router'
import { useDeliveryStore } from './store'
const store = useDeliveryStore()
const { approvedShare, offers, urgent } = storeToRefs(store)
onMounted(store.load)
</script>

<template><div class="shell"><aside><div class="brand">FusionReadyEU<span>REGULATORY READINESS</span></div><nav><RouterLink to="/">Readiness plans</RouterLink><RouterLink to="/insights">Regulatory guidance</RouterLink></nav><div class="health"><i /> Java fusion regulation service connected</div></aside><main><header><div><span class="eyebrow">Build a diverse workforce for Europe’s fusion ecosystem</span><h1>Fusion Regulatory Readiness Desk</h1></div><button @click="store.addOffer">Add readiness plan</button></header><section class="summary"><article><small>Plans ready</small><strong>{{ approvedShare }}%</strong><div class="bar"><span :style="{ width: `${approvedShare}%` }" /></div></article><article><small>Plans tracked</small><strong>{{ offers.length }}</strong><p>Shared workforce view</p></article><article><small>High-priority blockers</small><strong>{{ urgent }}</strong><p>Needs attention</p></article></section><RouterView /></main></div></template>
