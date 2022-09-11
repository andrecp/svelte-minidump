<script>
    import { Table } from "sveltestrap";

    export let crashInfo = {};
    export let threadName = null;
    export let systemInfo = {};
</script>

<h2>Process</h2>
<Table striped>
    <tbody>
        <tr>
            <td>OS</td>
            <td>{systemInfo.os}</td>
        </tr>
        <tr>
            <td>OS version</td>
            <td>{systemInfo.os_ver}</td>
        </tr>
        <tr>
            <td>CPU</td>
            <td>{systemInfo.cpu_arch}</td>
        </tr>
        <tr>
            <td>CPU info</td>
            <td>{systemInfo.cpu_info}</td>
        </tr>
        <tr>
            <td>Crash Reason</td>
            <td>{crashInfo.type}</td>
        </tr>
        <tr>
            <td>Crash Assertion</td>
            <td>{crashInfo.crash_assertion ? crashInfo.crash_assertion : ""}</td
            >
        </tr>
        <tr>
            <td>Crash Address</td>
            <td>{crashInfo.address}</td>
        </tr>
        <tr>
            <td>Crashing Thread</td>
            <td>{threadName ? threadName : crashInfo.crashing_thread}</td>
        </tr>
    </tbody>
</Table>

<style>
    .table td,
    .table th {
        min-width: 100px;
    }
</style>
