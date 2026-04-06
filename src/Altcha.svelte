<script lang="ts">
  // Importing altcha package will introduce a new element <altcha-widget>
  import 'altcha'
  import type {} from 'altcha/types/svelte';

  interface Props {
    value?: string;
  }

  let { value = $bindable('') }: Props = $props();
</script>

<!-- Configure your `challenge` and remove the `test` attribute, see docs: https://altcha.org/docs/v2/widget-integration/ -->
<altcha-widget
  style="--altcha-max-width:100%"
  configuration={JSON.stringify({
    debug: true,
    test: true,
  })}
  onstatechange={(ev) => {
    const { payload, state } = ev.detail
    if (state === 'verified' && payload) {
      value = payload;
    } else {
      value = '';
    }
  }}
></altcha-widget>