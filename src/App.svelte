<script>
	import { Col, Container, Row } from "sveltestrap";
	import Frame from "./Frame.svelte";
	import Frames from "./Frames.svelte";
	import Process from "./Process.svelte";
	import Thread from "./Thread.svelte";

	const fetchDump = (async () => {
		const response = await fetch("http://localhost:8000/data.json");
		return await response.json();
	})();
	fetchDump.then(function (result) {
		console.log(result); // "Some User token"
	});

	const threadIdx = 0;
</script>

<Container fluid>
	{#await fetchDump}
		<p>Getting the data...</p>
	{:then fetchDump}
		<Row>
			<Col>
				<Process
					threadName={fetchDump.crashing_thread.thread_name}
					crashInfo={fetchDump.crash_info}
					systemInfo={fetchDump.system_info}
				/>
			</Col>
			<Col>
				<Thread
					threadName={fetchDump.crashing_thread.thread_name}
					threadIndex={fetchDump.crashing_thread.threads_index}
					threads={fetchDump.threads}
				/>
				<Frame />
			</Col>
		</Row>
		<Row>
			<Col>
				<Frames frames={fetchDump.threads[threadIdx].frames} />
			</Col>
		</Row>
	{:catch error}
		<p>An error occurred getting the JSON data</p>
	{/await}
</Container>
