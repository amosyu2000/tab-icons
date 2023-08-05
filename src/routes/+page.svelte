<script>
	import { page } from '$app/stores'

	// import all icons from assets
	const icons = {}
	const iconModules = import.meta.glob('$lib/assets/icons/*.ico', { eager: true })
	for (const path in iconModules) {
		const name = path.substring(0, path.lastIndexOf(".")).split('/').pop()
		const id = name.toLowerCase().split(" ").join("-")
		icons[id] = {path, name}
	}

	$: hash = decodeURIComponent($page.url.hash.slice(1))

	$: tabIcon = icons[hash] || {}
</script>

<svelte:head>
	<link rel="icon" href={tabIcon.path} />
	<title>{tabIcon.name} | Tab Icons</title>
</svelte:head>

<img src={tabIcon.path} alt="Folder">
<p>{tabIcon.name} icon showing in tab.</p>
