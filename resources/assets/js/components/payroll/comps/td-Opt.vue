<template>
  <div class="btn-group btn-group-sm">
    <!-- <button class="btn btn-default" title="Display row"
      :class="{ '-nested-comp-open-btn': isDisplayRowVisible }"
      @click="toggleNestedComp('DisplayRow')">
      <i class="fa fa-list-ul"></i>
    </button> -->
    <a :href="'/employee/'+ row.id ">
    <button class="btn btn-default" data-toggle="tooltip"  data-placement="top" title="Ver Empleado">
      <i class="fa fa-eye"></i>
    </button>
    </a>
  </div>
</template>
<script>

export default {
  props: ['row', 'nested'],
  mounted () {
    // console.log(jQuery(this.$el).find('button[title]').tooltip());
    // jQuery(this.$el).find('button[title]').tooltip();
  },
  computed: {
    isDisplayRowVisible () {
      if (this.nested.comp !== 'DisplayRow') return
      return this.nested.visible
    },
    isFriendsTableVisible () {
      if (this.nested.comp !== 'FriendsTable') return
      return this.nested.visible
    }
  },
  methods: {
    toggleNestedComp (comp) {
      const { nested } = this
      if (nested.comp === comp) return nested.$toggle()
      nested.$toggle(comp, true)
    }
  }
}
</script>
<style>
.-nested-comp-open-btn {
  color: #fff !important;
  background-color: #337ab7 !important;
}
</style>
