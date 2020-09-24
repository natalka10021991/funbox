<template lang="pug">
	ul.cards-list
		li.card__wrapper(
			v-for="card in cards" 
			:key="card.id"
			)
			.card(
				:class="'card_state_' + card.state"
				v-on:click.prevent="changeState(card)"

			)
				.card__info
					p.card__subtitle Сказочное заморское яство
					h2.card__title 
						| Нямушка 
						span.card__title-type {{ card.type }}
					ul.card__params-list
						li.card__params-item {{ card.portion }} порций
						li.card__params-item {{ card.present }}
						li.card__params-item {{ card.additional }}
				img.card__image(src='../assets/cat.png')
				.card__weight
					span.card__weight-value {{ card.weight }}
					span.card__weight-unit кг
			p.card__caption(
				v-if="card.state === 'default'"
			)
				| Чего сидишь? Порадуй котэ, 
				a.card__caption-link(
					href="#"
					v-on:click.prevent="changeState(card)"
					
					) купи
			p.card__caption(
				v-if="card.state === 'selected'"
			)
				| Головы щучьи с чесночком да свежайшая семгушка
			p.card__caption.card__caption_state_disabled(
				v-if="card.state === 'disabled'"
			)
				| Печалька, {{ card.type }} закончился

</template>

<script>
	export default {
		name: 'Card',
		props: {
			
		},
		data() {
			return {
				cards: [],
				selectedCards: []
			}
		},
		created() {
			console.log(this.selectedCards)
			this.cards = require("../data/cards.json");
		},
		methods: {
			changeState(card) {
				console.log(card.state)
				if(card.state === "disabled") {
					return
				} else if(card.state === "default") {
					card.state = "selected"
				} else {
					card.state = "default"
				}
			}
		}
	}
</script>

<style lang="sass" scoped>
	$color-default: #1698d9
	$color-selected: #d91667
	$color-disabled: #b3b3b3

	.cards-list
		display: flex
		flex-wrap: wrap
		justify-content: center

	.card__wrapper
		width: 320px
		margin: 40px
		margin-top: 0

	.card
		position: relative
		height: 480px
		border-radius: 12px
		background: url('../assets/bg-default.png') center center no-repeat
		margin-bottom: 10px
		overflow: hidden

		&:hover,
		&:focus 
			cursor: pointer

		&.card_state_disabled
			&:hover,
			&:focus 
			cursor: default
			

		&_state_selected
			background: url('../assets/bg-selected.png') center center no-repeat

			.card__weight
				background-color: $color-selected

		&_state_disabled
			background: url('../assets/bg-disabled.png') center center no-repeat
			position: relative

			&:after 
				position: absolute
				content: ''
				display: block
				background: url('../assets/bg-disabled.png') center center no-repeat
				opacity: 0.5
				top: 0
				bottom: 0
				left: 0
				right: 0

			.card__weight
				background-color: $color-disabled

	.card__info
		padding: 20px 50px

	.card__subtitle
		margin-bottom: 8px

	.card__title
		font-size: 48px
		color: #000000
		font-weight: bold
		

	.card__title-type
		display: block
		font-size: 24px
		margin-bottom: 10px

	.card__params-list
		font-size: 14px
		line-height: 16px
		font-weight: bold

	.card__weight
		width: 80px
		height: 80px
		border-radius: 40px
		color: #ffffff
		
		display: flex
		justify-content: center
		align-items: center
		flex-direction: column
		position: absolute
		bottom: 15px
		right: 15px
		background-color: $color-default
			

	.card__weight-value
		font-size: 42px
		line-height: 32px
		margin-top: 5px

	.card__weight-unit
		font-size: 20px

	.card__image
		position: relative
		left: -20px
		top: 10px

	.card__caption 
		font-size: 13px
		line-height: 16px
		color: #ffffff
		text-align: center
		filter: drop-shadow(0px 1px 0.5px #000000)

		&_state_disabled
			color: #ffff66

	.card__caption-link
		color: $color-default

</style>