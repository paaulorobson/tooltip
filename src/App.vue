<template>
  <div>
    <ul>
      <li v-for="item in items" :key="item.id">
        <span>
            {{ item.name.length > 5 ? item.name.slice(0, 5) : item.name }}
        </span>

        <span
          v-if="item.name.length > 5"
          :title="item.name"
          :mouseenter="activeTooltip = item.id"
          :mouseleave="activeTooltip = null"
        >
          ...
        </span>
        <div v-if="activeTooltip === item.id" class="tooltip">{{ item.name }}</div>
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  data() {
    return {
      items: [
        { id: 1, name: 'INSS', description: 'Description 1' },
        { id: 2, name: 'FGTS', description: 'Description 2' },
        { id: 3, name: 'SIMPLES', description: 'Description 3' },
        { id: 4, name: 'CONFINS', description: 'Description 4' }
      ],
      activeTooltip: null
    }
  }
}
</script>

<style>
.tooltip {
  position: absolute;
  background-color: #333;
  color: #fff;
  padding: 5px;
  border-radius: 3px;
  z-index: 9999;
}
</style>
