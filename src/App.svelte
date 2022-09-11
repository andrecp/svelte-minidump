<script>
	import { Col, Container, Row } from "sveltestrap";
	import Frame from "./Frame.svelte";
	import Frames from "./Frames.svelte";
	import Process from "./Process.svelte";
	import Thread from "./Thread.svelte";
</script>

<Container>
	<Row>
		<Col>
			<Process />
		</Col>
		<Col>
			<Thread />
			<Frame />
		</Col>
	</Row>
	<Row>
		<Col>
			<Frames />
		</Col>
	</Row>
</Container>
