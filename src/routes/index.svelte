<script>
	import Display from '../components/Display.svelte';
	import Button from '../components/Button.svelte';
	import { answer, sum } from '../stores';
	import { evaluate } from 'mathjs';

	let ans = evaluate($sum.replace('x', '*'));
	if (ans) {
		answer.set(ans);
		sum.set('');
	}
</script>

<div class="bg-gray-200 w-screen h-screen flex justify-center items-center">
	<div
		class="bg-gray-100 bg-white rounded-2xl shadow-xl border-4 border-gray-100 grid grid-cols-4 grid-rows-6 gap-3 grid-flow-row w-auto p-4"
	>
		<div
			class="col-span-4 rounded-2xl shadow-xl border-4 border-gray-100 flex flex-col place-items-end "
		>
			<Display value={$sum} />
			<Display value={$answer} />
		</div>
		<Button _class="btn-light-control" sign="AC" />
		<Button _class="btn-light-control" sign="/" type="operator" />
		<Button _class="btn-light-control" sign="x" type="operator" />
		<Button _class="btn-light-control" sign="DEL" />
		<Button _class="btn-light-number" sign="7" type="number" />
		<Button _class="btn-light-number" sign="8" type="number" />
		<Button _class="btn-light-number" sign="9" type="number" />
		<Button _class="btn-light-control" sign="-" type="operator" />
		<Button _class="btn-light-number" sign="4" type="number" />
		<Button _class="btn-light-number" sign="5" type="number" />
		<Button _class="btn-light-number" sign="6" type="number" />
		<Button _class="btn-light-control" sign="+" type="operator" />
		<Button _class="btn-light-number" sign="1" type="number" />
		<Button _class="btn-light-number" sign="2" type="number" />
		<Button _class="btn-light-number" sign="3" type="number" />
		<Button _class="row-span-2 btn-light-control-jumbo row-span-2" sign="=" />
		<Button _class="btn-light-number" sign="%" />
		<Button _class="btn-light-number" sign="0" type="number" />
		<Button _class="btn-light-number" sign="," />
	</div>
</div>
