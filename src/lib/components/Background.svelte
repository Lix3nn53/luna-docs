<div data-page="home" class="page-bg" />

<style>
	.page-bg,
	.page-bg::after {
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
	}

	.page-bg::after {
		content: '';
		bottom: 0;
	}

	.page-bg[data-page='home'] {
		height: 100%;
		z-index: -1;
	}

	.page-bg[data-page='home']::after {
		background: rgb(var(--color-base-50));
	}
</style>
