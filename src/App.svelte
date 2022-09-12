<script>
	import { Col, Container, Row } from "sveltestrap";
	import Frame from "./Frame.svelte";
	import Frames from "./Frames.svelte";
	import Process from "./Process.svelte";
	import Thread from "./Thread.svelte";

	import { selectedThreadIdx } from "./stores.js";

	import { onMount } from "svelte";

	let crashDump;
	let _selectThreadIdx;
	async function getData() {
		const response = await fetch("/data");
		const response_json = await response.json();
		selectedThreadIdx.set(response_json.crashing_thread.threads_index);
		_selectThreadIdx = response_json.crashing_thread.threads_index;
		return response_json;
	}

	onMount(async () => {
		crashDump = await getData();
	});

	selectedThreadIdx.subscribe((value) => {
		_selectThreadIdx = value;
	});
</script>

<Container fluid>
	{#if !crashDump}
		<p>Getting the data...</p>
	{:else}
		<Row>
			<Col>
				<Process
					threadName={crashDump.crashing_thread.thread_name}
					crashInfo={crashDump.crash_info}
					systemInfo={crashDump.system_info}
				/>
			</Col>
			<Col>
				<Thread threads={crashDump.threads} />
				<Frame />
			</Col>
		</Row>
		<Row>
			<Col>
				<Frames frames={crashDump.threads[_selectThreadIdx].frames} />
			</Col>
		</Row>
	{/if}
</Container>
