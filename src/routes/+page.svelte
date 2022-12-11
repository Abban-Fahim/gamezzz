<script>
	import Icon from '@iconify/svelte/dist/OfflineIcon.svelte';
	import noAcc from '@iconify/icons-mdi/account-off-outline';
	import github from '@iconify/icons-mdi/github';
	import noAdds from '@iconify/icons-mdi/advertisements-off';
	import offline from '@iconify/icons-mdi/wifi-off';
	import Card from '../components/card.svelte';
	import { goto } from '$app/navigation';
</script>

<body>
	<h1>Gamezzz</h1>
	<div>
		<p>A simple app for playing your most loved games</p>
		<ul>
			<li><Icon inline icon={offline} /> Offline</li>
			<li><Icon inline icon={noAcc} /> Without accounts</li>
			<li><Icon inline icon={noAdds} /> Without ads</li>
			<!-- TODO add github link -->
			<li>
				<Icon inline icon={github} /> <a href="https://github.com/Abban-Fahim/">Open sourced</a> for
				your privacy :)
			</li>
		</ul>
	</div>
	<div>
		<Card
			title="Snek"
			action={() => {
				goto('/g/snake');
			}}
		/>
	</div>
</body>
