<template lang="html">
	<blockquote class="Quote">


		<p v-text="quote.body">
			<slot></slot>
		</p>
		<div class="Quote__footer">
			<span>-</span>
			<cite class="Quote__cite">
				{{ cite }}
			</cite>
		</div>
	</blockquote>
</template>



<script>
var axios = require('axios')

export default {
  name: 'Quote',
  props: {
		cite: {
			type: String,
			default: () => ''
		}
	}
}
</script>
