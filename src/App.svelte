<script lang="javascript">
	import { onMount } from "svelte";
	import { io } from "socket.io-client";

	import SHeader from "./components/siderbar/Header.svelte";
	import Search from "./components/siderbar/Search.svelte";
	import Chat from "./components/siderbar/Chat.svelte";

	let socket;
	let myRoom;
	let elmRef;
	let msg;
	let sendToRoom;

	const userUuid = "3a702eff-2a20-4415-9c05-cb96308a368c";

	onMount(() => {
		socket = io("ws://localhost:3001/chat", { autoConnect: false });

		socket.on("connect", function () {
			socket.emit("create", { room: myRoom })
		});

		socket.on("wellcome", (msg) => console.log(msg));
		socket.on("disconnect", (msg) => console.log(msg));
		socket.on("msg from", msg => console.log(msg))
	});

	const handlerDisconnect = () => {
		socket.disconnect();
	};

	const handlerConnect = () => {
		myRoom = elmRef.value;
		socket.connect();
	};

	const sendMessage = () => {
		socket.emit("msg to",{room: sendToRoom, msg});
		msg = "";
		sendToRoom = "";
	};
</script>

<div class="container">
	<div class="content">
		<section class="sidebar">
			<SHeader />
			<Search />
			<button on:click={handlerDisconnect}> disconnnect</button>

			<section class="chats">
				<Chat typing="true" />
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
		<section class="message">
			{#if myRoom}

			  <h2>I am {myRoom}</h2>

				<label for="">
					Enviar a:
					<input type="text" bind:value={sendToRoom} />
				</label>
				<textarea bind:value={msg} />
				<input type="button" value="enviar" on:click={sendMessage} />

			{:else}
				<input type="text" bind:this={elmRef} />
				<input type="button" value="login" on:click={handlerConnect} />
			{/if}
		</section>
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

	.chats {
		display: block;
		position: relative;
		overflow: auto;
		height: 100%;
	}

	.message {
		width: 100%;
		padding: 1rem;
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
