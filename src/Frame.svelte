<script>
    import {
        Dropdown,
        DropdownToggle,
        DropdownMenu,
        DropdownItem,
        Table,
    } from "sveltestrap";
    let frameName = "00 - RustMozCrash(char const*, int, char const*)";
    let registers = [
        { name: "rax", value: "0x0004abccdd" },
        { name: "rdx", value: "0x0006abccdd" },
        { name: "rcx", value: "0x0007abccdd" },
        { name: "rbx", value: "0x0009abccdd" },
    ];
</script>

<h2>Frame</h2>
<Dropdown>
    <DropdownToggle caret>{frameName}</DropdownToggle>
    <DropdownMenu>
        <DropdownItem>Another frame</DropdownItem>
    </DropdownMenu>
</Dropdown>
<Table striped>
    <tbody>
        {#each registers as register}
            <tr>
                <td>{register.name}</td>
                <td>{register.value}</td>
            </tr>
        {/each}
    </tbody>
</Table>
