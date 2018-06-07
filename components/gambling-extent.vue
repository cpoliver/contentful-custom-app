<template>
  <tr>
    <td>{{ gamblingExtent.fields.id }}</td>
    <td>{{ gamblingExtent.fields.label }}</td>
    <td>{{ gamblingExtent.fields.value }}</td>
  </tr>
</template>

<script>
export default {
  props: ['gamblingExtent']
}
</script>

<style>

</style>
