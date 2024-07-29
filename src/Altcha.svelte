<script lang="ts">
  // Importing altcha package will introduce a new element <altcha-widget>
  import 'altcha'

  export let value: string = ''
</script>

<!-- Configure your `challengeurl` and remove the `test` attribute, see docs: https://altcha.org/docs/website-integration/#using-altcha-widget -->
<altcha-widget
  style="--altcha-max-width:100%"
  debug
  test
  on:statechange={(ev) => {
    const { payload, state } = ev.detail
    if (state === 'verified' && payload) {
      value = payload;
    } else {
      value = '';
    }
  }}
></altcha-widget>