<script lang="ts">
  // Importing altcha package will introduce a new element <altcha-widget>
  import 'altcha'

  interface Props {
    value?: string;
  }

  let { value = $bindable('') }: Props = $props();
</script>

<!-- Configure your `challengeurl` and remove the `test` attribute, see docs: https://altcha.org/docs/v2/widget-integration/ -->
<altcha-widget
  style="--altcha-max-width:100%"
  debug
  test
  onstatechange={(ev) => {
    const { payload, state } = ev.detail
    if (state === 'verified' && payload) {
      value = payload;
    } else {
      value = '';
    }
  }}
></altcha-widget>