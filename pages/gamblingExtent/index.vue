<template>
  <div>
    <header class="blog header">
      <div class="foreground">
        <div class="page-bar wrapper">
          <a class="person-name" href="#">Extent of Gambling</a>
          <Navigation></Navigation>
        </div>
      </div>
    </header>

    <section class="body-container">
      <table>
        <tr>
          <th class="id">id</th>
          <th class="label">label</th>
          <th class="value">value</th>
        </tr>
        <gambling-extent v-for="gamblingExtent in gamblingExtents" :gamblingExtent="gamblingExtent"></gambling-extent>
      </table>
    </section>

  </div>
</template>

<script>
import {createClient} from '~/plugins/contentful.js'
import Navigation from '~/components/navigation.vue'
import GamblingExtent from '~/components/gambling-extent.vue'

const client = createClient()

export default {
  asyncData ({ env, params }) {
    return client.getEntries({
      'content_type': 'gamblingExtent',
      order: 'fields.id'
    }).then((entries) => {
      console.log(entries)

      return {
        gamblingExtents: entries.items
      }
    }).catch(console.error)
  },
  components: {
    GamblingExtent,
    Navigation
  }
}
</script>

<style>
  table {
    margin: auto;
  }

  th.id {
    width: 3rem;
  }

  th.label {
    width: 10rem;
  }

  th.value {
    width: 10rem;
  }
</style>
