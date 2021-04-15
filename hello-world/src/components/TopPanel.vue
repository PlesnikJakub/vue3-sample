<template>
  <div>
    <div>
        <IncrementOptionAPI />
    </div>
    <div>
        <IncrementCompositionAPI />
    </div>
  </div>
</template>

<script>
import IncrementOptionAPI from './IncrementOptionAPI';
import IncrementCompositionAPI from './IncrementCompositionAPI';
export default {
  name: "TopPanel",
  components: {
    IncrementOptionAPI,
    IncrementCompositionAPI
  },
}
</script>
