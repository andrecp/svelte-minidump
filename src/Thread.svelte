<script>
    import {
        Dropdown,
        DropdownToggle,
        DropdownMenu,
        DropdownItem,
        Table,
    } from "sveltestrap";

    import { selectedThreadIdx } from "./stores.js";

    let isLoading = true;

    export let threads;
    let threadName = "";
    let selectedThread = null;
    let _selectThreadIdx = null;
    selectedThreadIdx.subscribe((value) => {
        _selectThreadIdx = value;
        selectedThread = threads[value];
        threadName = selectedThread.thread_name || value;
        isLoading = false;
    });

    function updateSelectedThread(e) {
        selectedThreadIdx.set(e.target.value);
    }
</script>

<h2>Thread</h2>
{#if isLoading}
    <p>Fetching thread data</p>
{:else}
    <select class="form-select" on:change={updateSelectedThread}>
        {#each threads as thread, idx}
            <option selected={idx == _selectThreadIdx} value={idx}
                >{thread.name || idx}</option
            >
        {/each}
    </select>
    <Table striped>
        <tbody>
            <tr>
                <td>Last Error Value</td>
                <td>{selectedThread.last_error_value || "n/a"}</td>
            </tr>
        </tbody>
    </Table>
{/if}

<style>
    :global(.dropdown-menu) {
        max-height: 280px;
        overflow-y: auto;
    }
</style>
