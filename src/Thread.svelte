<script>
    import {
        Dropdown,
        DropdownToggle,
        DropdownMenu,
        DropdownItem,
        Table,
    } from "sveltestrap";
    let threadName = "WRRenderBackend#1 (29995)";
    let last_error_value = "ERROR_SUCCESS";
</script>

<h2>Thread</h2>
<Dropdown>
    <DropdownToggle caret>{threadName}</DropdownToggle>
    <DropdownMenu>
        <DropdownItem>Another thread</DropdownItem>
    </DropdownMenu>
</Dropdown>
<Table striped>
    <tbody>
        <tr>
            <td>Last Error Value</td>
            <td>{last_error_value}</td>
        </tr>
    </tbody>
</Table>
