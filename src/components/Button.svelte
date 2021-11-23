<script>
	import { evaluate } from 'mathjs';
	import { answer, sum } from '../stores.js';

	export let _class;
	export let sign;
	export let type;


	const buttonClicked = () => {
		if (type === 'number') {

			sum.update((n) => n + `${sign}`);

		} else if (type === 'operator') {
			let lastChar = $sum.trim().slice(-1);
			if (isCharNumber(lastChar)) {
				sum.update((n) => n + ` ${sign} `);
			} else if (!isCharNumber(lastChar)) {
				sum.update((n) => n.slice(0, -2) + ` ${sign} `);
			}
		} else if (sign === 'AC') {
			sum.set('');
			answer.set('');
		} else if (sign === 'DEL') {
			sum.update((n) => n.slice(0, -1));
		} else if (sign === '%') {
			// TO DO
		} else if (sign === ',') {
			// TO DO
		} else if (sign === '=') {
      let ans = evaluate($sum.replace('x','*'))
      if(ans){
      answer.set(ans)
      }

		}
	};

	function isCharNumber(c) {
		return c >= '0' && c <= '9';
	}
</script>

<div class={_class} on:click={buttonClicked}>
	{sign}
</div>
