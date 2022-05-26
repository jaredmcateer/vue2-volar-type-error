<script lang="ts">
import { defineComponent, PropType } from "@vue/composition-api";

export default defineComponent({

  props: {
    features: { type: Object as PropType<Record<string, string | boolean>>, required: true }
  },
  data() {
    return {
      feature: 'foo',
    };
  },
  methods: {
    isBoolean(feature: any): feature is boolean {
      return typeof feature === 'boolean';
    }
  }
});
</script>

<template>
  <div>
    <div>
      <!-- IDE Error -->
      <div>
        <h2>Error in ide</h2>
        <label>Checkbox <input
            type="checkbox"
            :checked="features[feature]"
          />
        </label>
        <br>
        <img src="../assets/ide-error.png" />
        <hr>
        <!-- IDE Error-->
        <h3>Also has error even with type checking</h3>
        <input
          type="checkbox"
          v-if="typeof features[feature] === 'boolean'"
          :checked="features[feature]"
        />

        <h3>Also has error checking type predicates</h3>
        <input
          type="checkbox"
          v-if="isBoolean(features[feature])"
          :checked="features[feature]"
        />
      </div>
      <div>
        <h2>Runtime error (uncomment code to see)</h2>
        <!-- Runtime Error-->
        <!--
        <input
          type="checkbox"
          :checked="(features[feature] as boolean)"
        />
        -->

        <br>
        <img src="../assets/error.png" />

        <h2>Works if you check property directly</h2>
        <input
          type="checkbox"
          v-if="typeof features.foo === 'boolean'"
          :checked="features.foo"
        />
      </div>
    </div>
  </div>
</template>

<style>
a {
  color: #42b983;
}

label {
  margin: 0 0.5em;
  font-weight: bold;
}

code {
  background-color: #eee;
  padding: 2px 4px;
  border-radius: 4px;
  color: #304455;
}
</style>
