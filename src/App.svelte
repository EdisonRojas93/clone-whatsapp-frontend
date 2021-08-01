<script>
	import SHeader from "./components/siderbar/Header.svelte";
	import Search from "./components/siderbar/Search.svelte";
	import Chat from "./components/siderbar/Chat.svelte";
</script>

<div class="container">
	<div class="content">
		<section class="sidebar">
			<SHeader />
			<Search />
			
			<section class="chats">
				<Chat typing="true"/>
				<Chat />
				<Chat />
				<Chat />
				<Chat />
				<Chat />
				<Chat />
				<Chat />
				<Chat />
				<Chat />
				<Chat />
				<Chat />
				<Chat />
			</section>
		</section>
		<section class="message">aqui va los mensajes</section>
	</div>
</div>

<style>
	.container {
		display: block;
		height: 100vh;
		background: var(--background-beige);
	}

	.container::before {
		background: var(--background-green);
		position: fixed;
		width: 100vw;
		content: "";
		height: 130px;
		top: 0;
		left: 0;
	}

	.content {
		max-width: 1440px;
		margin: 0 auto;
		background: var(--background-white);
		position: relative;
		width: 100%;
		top: 20px;
		height: calc(100vh - 40px);
		border-radius: 0px;
		box-shadow: 0px 1px 1px 1px rgba(0, 0, 0, 0.2);
		display: flex;
		flex-direction: row;
		justify-content: flex-start;
	}

	.sidebar {
		max-width: 400px;
		width: 100%;
		height: 100%;
		box-shadow: 1px 0px 1px rgba(0, 0, 0, 0.2);
		overflow: hidden;
	}

	.chats{
		display: block;
		position: relative;
		overflow: auto;
		height: 100%;
	}

	.message {
		width: 100%;
	}



	@media (prefers-color-scheme: dark) {
		.container {
			background: var(--background-dark);
		}
		.container::before {
			background: var(--background-dark);
		}
	}
</style>
