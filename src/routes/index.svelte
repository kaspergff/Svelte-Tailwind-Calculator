<script>
	import Button from '../components/Button.svelte';
	import { answer, sum } from '../stores';

	let dark = false
</script>

<div class:dark>
	<div class="dark:bg-gray-700 bg-gray-200 w-screen h-screen flex justify-center items-center">
		<div
			class="bg-white dark:bg-gray-800 rounded-2xl shadow-xl border-4 border-gray-100 grid grid-cols-4 grid-rows-6 gap-3 grid-flow-row w-72 p-4"
		>
			<div
				class="row-span-full col-span-4 rounded-2xl shadow-xl border-4 border-gray-100 flex flex-col place-items-end break-all content-around pr-3 pl-3"
			>
				<p class="text-base font-semibold dark:text-white">{$sum}</p>
				<p class="text-lg font-semibold dark:text-white">{$answer}</p>
			</div>
			<Button _class="btn-light-control dark:btn-dark-control" sign="AC" />
			<Button _class="btn-light-control dark:btn-dark-control" sign="/" type="operator" />
			<Button _class="btn-light-control dark:btn-dark-control" sign="x" type="operator" />
			<Button _class="btn-light-control dark:btn-dark-control" sign="DEL" />
			<Button _class="btn-light-number dark:btn-dark-number" sign="7" type="number" />
			<Button _class="btn-light-number dark:btn-dark-number" sign="8" type="number" />
			<Button _class="btn-light-number dark:btn-dark-number" sign="9" type="number" />
			<Button _class="btn-light-control dark:btn-dark-control" sign="-" type="operator" />
			<Button _class="btn-light-number dark:btn-dark-number" sign="4" type="number" />
			<Button _class="btn-light-number dark:btn-dark-number" sign="5" type="number" />
			<Button _class="btn-light-number dark:btn-dark-number" sign="6" type="number" />
			<Button _class="btn-light-control dark:btn-dark-control" sign="+" type="operator" />
			<Button _class="btn-light-number dark:btn-dark-number" sign="1" type="number" />
			<Button _class="btn-light-number dark:btn-dark-number" sign="2" type="number" />
			<Button _class="btn-light-number dark:btn-dark-number" sign="3" type="number" />
			<Button _class="row-span-2 btn-light-control-jumbo dark:btn-dark-control-jumbo" sign="=" />
			<!-- <Button _class="btn-light-number dark:btn-dark-number" sign="DM" /> -->
			<button class="btn-light-control dark:btn-dark-control"
				type="button"
				on:click|preventDefault={() => {
					dark = !dark;
				}}>{dark ? 'dark' : 'light'}</button
			>
			<Button _class="btn-light-number dark:btn-dark-number" sign="0" type="number" />
			<Button _class="btn-light-number dark:btn-dark-number" sign="," />
		</div>
	</div>
</div>
