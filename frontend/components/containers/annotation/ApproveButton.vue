<template>
  <v-tooltip bottom>
    <template v-slot:activator="{ on }">
      <v-btn
        v-on="on"
        @click="approveDocument"
        :disabled="disabled"
        class="text-capitalize ps-1 pe-1"
        min-width="36"
        outlined
      >
        <span v-if="approved">Approved</span>
        <span v-else>Approve</span>
      </v-btn>
    </template>
    <span v-if="approved">Checked</span>
    <span v-else>Not checked</span>
  </v-tooltip>
</template>

<script>
import { mapActions } from 'vuex'

export default {
  props: {
    approved: {
      type: Boolean,
      default: false,
      required: true
    },
    disabled: {
      type: Boolean,
      default: false
    }
  },

  methods: {
    ...mapActions('documents', ['approve']),
    approveDocument() {
      this.approve({
        projectId: this.$route.params.id
      })
    }
  }
}
</script>
