<template>
  <b-navbar class="fixed-top" toggleable="md" type="dark" variant="info">

  <b-navbar-toggle target="nav_collapse"></b-navbar-toggle>

  <b-navbar-brand href="#">KanBan</b-navbar-brand>

  <b-collapse is-nav id="nav_collapse">
    <b-navbar-nav class="ml-auto">
    <add-kanban></add-kanban>
    </b-navbar-nav>
  </b-collapse>
</b-navbar>
</template>

<script>
import AddKanban from '@/components/AddKanban'
export default {
  components: {
    AddKanban
  }
}
</script>
