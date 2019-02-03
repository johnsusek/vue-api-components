<template>
  <span>
    <slot :action="doAction" />
  </span>
</template>

<script>
import axios from 'axios';
import { getConfig } from '@/lib/config';

export default {
  props: ['name', 'url', 'data', 'params', 'method'],

  data() {
    return {
      response: null
    };
  },

  mounted() {
    // If the user hasn't put anything in the slot, just do the action
    // immediately
    if (!this.$slots.default && !this.$scopedSlots.default) {
      this.doAction();
    }
  },

  methods: {
    async doAction() {
      await this.$nextTick();

      let axiosConfig = getConfig(this.name);

      if (this.method) axiosConfig.method = this.method;
      if (this.params) axiosConfig.params = this.params;
      if (this.data) axiosConfig.data = this.data;
      if (this.url) axiosConfig.url = this.url;

      this.$emit('start');

      try {
        console.log(axiosConfig);
        let res = await axios.request(axiosConfig);
        // For successful calls, just return the data
        this.response = res.data;
        this.$emit('success', this.response);
      } catch (error) {
        console.log(error);
        // For errors, return the whole response object for handling
        this.response = error.response;
        this.$emit('error', this.response);
      } finally {
        this.$emit('end');
      }
    }
  }
};
</script>
