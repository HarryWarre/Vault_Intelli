Tags: #muiReactTable #tables #react #mui

[Link example](https://www.material-react-table.com/docs/examples/basic)

# Cấu trúc của một  Material React Table

## Data
- Types: Type Data đầu vào, thường là một OBJECT 
```js
type Person = {
	name: {
		firstName: string;
		lastName: string;
	};
	address: string;
	city: string;
	state: string;
};
```
- Dữ liệu đầu vào:
	- Là dự liệu sẽ được hiển thị lên bảng dựa vào cấu trúc Type được khai báo lúc đầu

`const data: Person[] = [
`{`
`name: {`
`firstName: 'John',`
`lastName: 'Doe',`
 `},`
`address: '261 Erdman Ford',`
`city: 'East Daphne',`
 `state: 'Kentucky',`
`}, .../`

## Tables
### Columns
- Cấu trúc của một columns:
	- accessorKey
	- header
	- size
	- ...
- Thông thường, có thể thêm dạng type data vào đầu phần declares để khai báo kiểu (optional)
- Số cột bắt buộc phải tương ứng với phần data
Examples:
```js
const columns = useMemo<MRT_ColumnDef<Person>[]>( () => [ 
{
	accessorKey: 'name.firstName', //access nested data with dot
	notation header: 'First Name', 
	size: 150, 
},
```

### Material React Table
- Tạo bảng
	- Có thể khai báo theo dạng HTML Element
	- Hoặc khai báo theo dạng [Component](https://github.com/HarryWarre/ArcGIS-Training-ITL-Client/blob/main/your-extensions/widgets/tab-table-view/src/components/tab-table.tsx)
```typescript
const table = useMaterialReactTable({
	columns,
	data, //data must be memoized or stable (useState, useMemo, defined outside of this component, etc.)
});

return <MaterialReactTable table={table} />;
```

