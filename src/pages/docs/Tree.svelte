
<slot node={node}></slot>

{#if children}
<CollapsibleSection headerText={node.title} path="undefined">
<ul>
    {#each children as childNode}
    <li>
      <svelte:self let:node={childNodeInner} bind:node={childNode}>
          <slot node={childNodeInner}></slot>
      </svelte:self>
    </li>
    {/each}
</ul>
</CollapsibleSection>
{/if}

<style>
  ul {
    --indent: 10px;
    padding: 0 0 0 var(--indent);
    margin: 0 0 0 var(--indent);
    list-style: none;
    border-left: 1px solid #eee;
  }
  li {
    padding: 0;
  }
</style>

<script>
  import CollapsibleSection from './CollapsibleSection.svelte';
  export let node;
  let children = node.children;
</script>
