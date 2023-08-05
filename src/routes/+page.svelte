<script>
	import { page } from '$app/stores'
	import iconPaths from '$lib/assets/icons'

	// import all icons from assets
	const icons = {}
	Object.entries(iconPaths).forEach(([name, path]) => {
		const id = name.toLowerCase().split(" ").join("-")
		icons[id] = {path, name}
	})

	$: hash = decodeURIComponent($page.url.hash.slice(1))

	$: tabIcon = icons[hash] || {}
</script>

<svelte:head>
	<link rel="icon" href={tabIcon.path} />
	<title>{tabIcon.name} | Tab Icons</title>
</svelte:head>

<img src={tabIcon.path} alt="Folder">
<p>{tabIcon.name} icon showing in tab.</p>
