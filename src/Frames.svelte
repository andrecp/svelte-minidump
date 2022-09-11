<script>
    import { Table } from "sveltestrap";
    export let frames = [];
</script>

<Table striped>
    <thead>
        <tr>
            <th>Frame</th>
            <th>Module</th>
            <th>Source</th>
            <th>Signature</th>
        </tr>
    </thead>
    <tbody>
        {#each frames as frame}
            <tr>
                <td>{frame.frame}</td>
                <td>{frame.module ? frame.module : ""}</td>
                <td
                    >{frame.file ? frame.file : ""}{frame.line
                        ? ":" + frame.line
                        : ""}</td
                >
                <td>{frame.function ? frame.function : ""}</td>
            </tr>
        {/each}
    </tbody>
</Table>
