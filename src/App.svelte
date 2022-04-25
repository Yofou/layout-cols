<script lang="ts">
  import Card from "./lib/card.svelte";
  import AnimateSharedLayout from "svelte-motion/src/components/AnimateSharedLayout/AnimateSharedLayout.svelte";

  let selected: number | undefined = undefined;
</script>

<AnimateSharedLayout>
    <main>
      <Card --color="red" bind:selected num={1}>Col - 1</Card>
      <Card --color="green" bind:selected num={2}>Col - 2</Card>
      <Card --color="blue" bind:selected num={3}>Col - 3</Card>
      <Card --color="purple" bind:selected num={4}>Col - 4</Card>
    </main>
</AnimateSharedLayout>

<style>
  main {
    width: 100%;
    min-height: 100vh;
    display: grid;
    grid-template-columns: repeat(4, 1fr);
  }
</style>
