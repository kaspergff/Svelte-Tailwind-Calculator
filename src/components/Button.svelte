<script>
	import { evaluate } from 'mathjs';
	import { answer, sum } from '../stores.js';

	export let _class;
	export let sign;
	export let type = '';

	const buttonClicked = () => {
		// user inputs a number
		if (type === 'number') {
			// check if answer is showing on screen
			if ($answer) {
				// if true answer is transferd to upper row
				answer.set('');
				sum.set(sign);
				// else add number in upper row
			} else sum.update((n) => n + `${sign}`);
			// user inputs a operator -> x / + -
		} else if (type === 'operator') {
			//  // check if answer is showing on screen
			if ($answer) {
        // if true answer is transferd to upper row
				sum.set($answer);
				answer.set('');
        // add operator after old awnser
				sum.update((n) => n + ` ${sign} `);
			} else {
				// need to het the last character to check if is a number or operator
				let lastChar = $sum.trim().slice(-1);
        // check if last char is a number
				if (isCharNumber(lastChar)) {
          // if true add operator after number
					sum.update((n) => n + ` ${sign} `);
				} else if (!isCharNumber(lastChar)) {
          // else remove old operator and add new operator
					sum.update((n) => n.slice(0, -2) + ` ${sign} `);
				}
			}// user clears everything on screen
		} else if (sign === 'AC') {
			sum.set('');
			answer.set('');
      // delete last character
		} else if (sign === 'DEL') {
			sum.update((n) => n.slice(0, -1));

      // add dot on screen
		} else if (sign === ',') {
      // only add dot when last number doesnt have a dot 
      let lastNumber = $sum.split().pop()
      console.log(lastNumber);
      if (/^\d{1,}$/.test(lastNumber)) sum.update((n) => n + '.')
      else if(lastNumber.trim().slice(-1) === 'x' || lastNumber.trim().slice(-1) === '/' || lastNumber.trim().slice(-1) === '+' || lastNumber.trim().slice(-1) === '-'){
        sum.update((n) => n + ' 0.')
      }

      // calculate sum and set answer
		} else if (sign === '=') {
			let ans = evaluate($sum.replace('x', '*'));
			if (ans) {
				answer.set(ans);
			}
		}
	};
// function to check if a char is a number
	function isCharNumber(c) {
		return c >= '0' && c <= '9';
	}
</script>

<div class={_class} on:click={buttonClicked}>
	{sign}
</div>
