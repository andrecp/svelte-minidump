<script>
    import { Table } from "sveltestrap";
    let frames = [
        {
            id: 0,
            trust: "context",
            module: "xul.dll",
            source: "wrapers.cpp:18",
            signature: "RustMozCrash(char const*, int, char const*)",
        },
    ];
</script>

<Table striped>
    <thead>
        <tr>
            <th>Frame</th>
            <th>Trust</th>
            <th>Module</th>
            <th>Source</th>
            <th>Signature</th>
        </tr>
    </thead>
    <tbody>
        {#each frames as frame}
            <tr>
                <td>{frame.id}</td>
                <td>{frame.trust}</td>
                <td>{frame.module}</td>
                <td>{frame.source}</td>
                <td>{frame.signature}</td>
            </tr>
        {/each}
    </tbody>
</Table>
