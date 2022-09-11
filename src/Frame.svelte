<script>
    import {
        Dropdown,
        DropdownToggle,
        DropdownMenu,
        DropdownItem,
        Table,
    } from "sveltestrap";
    let frameName = "0";
    let registers = {
        r10: "0x0000000001932010",
        r11: "0x0000000000000000",
        r12: "0x0000000000000000",
        r13: "0x000000000ece5fb8",
        r14: "0x0000000000000000",
        r15: "0x000000000df59c40",
        r8: "0x0000000000000000",
        r9: "0x0000000000000001",
        rax: "0x0000000000000000",
        rbp: "0x00007ffbea10ffc0",
        rbx: "0x00007ffbea10ffc0",
        rcx: "0x00007ffbd45d9e60",
        rdi: "0x00007ffdb36f8e30",
        rdx: "0x00007ffbd45f050e",
        rip: "0x0000000000000000",
        rsi: "0x0000000000000000",
        rsp: "0x00007ffdb36f8e28",
    };
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
        {#each Object.entries(registers).sort((a, b) => a[0] - b[0]) as [name, content]}
            <tr>
                <td>{name}</td>
                <td>{content}</td>
            </tr>
        {/each}
    </tbody>
</Table>

<style>
    tbody {
        overflow-y: scroll;
        height: 120px;
        position: absolute;
    }
</style>
