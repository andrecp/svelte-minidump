<script>
    import {
        Dropdown,
        DropdownToggle,
        DropdownMenu,
        DropdownItem,
        Table,
    } from "sveltestrap";
    export let threadName;
    export let threadIndex;
    export let threads;
</script>

<h2>Thread</h2>
<Dropdown>
    <DropdownToggle caret
        >{threadName ? threadName : threadIndex}</DropdownToggle
    >
    <DropdownMenu>
        {#each threads as thread, idx}
            <DropdownItem>{thread.name ? thread.name : idx}</DropdownItem>
        {/each}
    </DropdownMenu>
</Dropdown>
<Table striped>
    <tbody>
        <tr>
            <td>Last Error Value</td>
            <td
                >{threads[threadIndex].last_error_value
                    ? threads[threadIndex].last_error_value
                    : "n/a"}</td
            >
        </tr>
    </tbody>
</Table>

<style>
    :global(.dropdown-menu) {
        max-height: 280px;
        overflow-y: auto;
    }
</style>
