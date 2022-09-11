<script>
    import { Table } from "sveltestrap";
    let process = {
        os: "windows",
        os_version: "10.0.19044",
        cpu: "amd64",
        cpu_info: "Family 6 model 165 stepping 2",
        crash_reason: "EXCEPTION_BREAKPOINT",
        crash_assertion: "",
        crash_address: "0x000777fcd99eda",
        crashing_thread: "WRRenderBackend#1 (29995)",
    };
</script>

<h2>Process</h2>
<Table striped>
    <tbody>
        <tr>
            <td>OS</td>
            <td>{process.os}</td>
        </tr>
        <tr>
            <td>OS version</td>
            <td>{process.os_version}</td>
        </tr>
        <tr>
            <td>CPU</td>
            <td>{process.cpu}</td>
        </tr>
        <tr>
            <td>CPU info</td>
            <td>{process.cpu_info}</td>
        </tr>
        <tr>
            <td>Crash Reason</td>
            <td>{process.crash_reason}</td>
        </tr>
        <tr>
            <td>Crash Assertion</td>
            <td>{process.crash_assertion}</td>
        </tr>
        <tr>
            <td>Crash Address</td>
            <td>{process.crash_address}</td>
        </tr>
        <tr>
            <td>Crashing Thread</td>
            <td>{process.crashing_thread}</td>
        </tr>
    </tbody>
</Table>
