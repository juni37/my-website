<script lang="ts">
  export let title = 'Paul Kim';
  export let description = "Hi! I'm Yujun (Paul) Kim, and I build and make cool stuffs";
  export let image = 'https://paulkim.me/card.png';
</script>

<svelte:head>
	<title>{title}</title>
  <meta name="description" content={description}/>
    
  <meta name="twitter:card" content="summary_large_image" />
  <meta name="twitter:site" content="paulkim.me" />
  <meta name="twitter:title" content={title} />
  <meta name="twitter:description" content={description} />
  <meta name="twitter:image" content={image} />

  <meta property="og:title" content={title} />
  <meta property="og:description" content={description} />
  <meta property="og:image" content={image} />

  <link rel="icon" href="https://paulkim.me/favicon.ico" type="image/x-icon"/>
</svelte:head>