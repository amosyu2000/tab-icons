<script>
	import { page } from '$app/stores'
	import icons from '$lib/assets/icons'

	$: hash = $page.url.hash.slice(1)

	$: tabIcon = icons[hash] || {}
</script>

<svelte:head>
	<link rel="icon" href={tabIcon.path} />
	<title>{tabIcon.name} | Tab Icons</title>
</svelte:head>

<img src={tabIcon.path} alt="Folder">
<p>{tabIcon.name} icon showing in tab.</p>
