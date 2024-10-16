Tags: #muiReactTable #tables #react #mui 

Reference: [Minimal Example](https://www.material-react-table.com/docs/examples/minimal)
Version: 3.0.1
# Introduce
- Đối với minimal table, nó thường sẽ tối giản hơn, có nghĩa là nó sẽ không cần thiết phải có các cột chức năng custom thêm mà chỉ hiển thị tối giản hết mức
- Để làm được điều đó chúng ta sẽ thực hiện gọi các hàm enable... và set nó thành false vì mặc định nó hiện tại đang được bật lên

# Example
``` js
const table = useMaterialReactTable({
	columns,
	data, //data must be memoized or stable (useState, useMemo, defined outside of this component, etc.)
	enableKeyboardShortcuts: false,
	enableColumnActions: false,
	enableColumnFilters: false,
	enablePagination: false,
	enableSorting: false,
	mrtTheme: (theme) => ({
	baseBackgroundColor: theme.palette.background.default, //change default background color
	}),
	muiTableBodyRowProps: { hover: false }, // Tắt hover khi đưa chuột vào hàng 
	muiTableProps: {
	sx: {
	 border: '1px solid rgba(81, 81, 81, .5)',
	caption: {
	captionSide: 'top',
	},
	},
	},
	muiTableHeadCellProps: {
	sx: {
	 border: '1px solid rgba(81, 81, 81, .5)',
	fontStyle: 'italic',
	fontWeight: 'normal',
	},
	},
	muiTableBodyCellProps: {
	sx: {
	border: '1px solid rgba(81, 81, 81, .5)',
	},
	},
	renderCaption: ({ table }) =>
	   `Here is a table rendered with the lighter weight MRT_Table sub-component, rendering ${table.getRowModel().rows.length} rows.`,
 });
```
Giải thích

```js
enableKeyboardShortcuts: false,
enableColumnActions: false,
enableColumnFilters: false,
enablePagination: false,
enableSorting: false,
```

Các props này được dùng để tắt các phần chức năng thêm, có tác dụng làm cho bảng càng thêm đơn giản

```js
muiTableBodyRowProps: { hover: false }, // Tắt hover khi đưa chuột vào hàng 
	muiTableProps: {
	sx: {
	 border: '1px solid rgba(81, 81, 81, .5)',
	caption: {
	captionSide: 'top',
	},
	},
	},
	muiTableHeadCellProps: {
	sx: {
	 border: '1px solid rgba(81, 81, 81, .5)',
	fontStyle: 'italic',
	fontWeight: 'normal',
	},
	},
	muiTableBodyCellProps: {
	sx: {
	border: '1px solid rgba(81, 81, 81, .5)',
	},
	},
```

Các phần mui... này được dùng để custom các phần trong bảng
Example: muiTableBodyRowProps được dùng để custom body row (hàng trong bảng)
muiTableHeadCellProps: Custom header
muiTableBodyCellProps: Custom cells trong bảng
