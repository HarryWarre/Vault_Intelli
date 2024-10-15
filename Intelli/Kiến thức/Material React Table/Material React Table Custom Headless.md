Tags: #muiReactTable #tables #react #mui 

Reference: [Custom Headless](https://www.material-react-table.com/docs/examples/custom-headless)

# Introduce
- Custom headless là việc tự hiển thị bảng dữ liệu bằng cách sử dụng các thư viện khác như React hoặc Vue
- Có thể sử dụng các hàm khác của MRRT để thao tác vơi dữ liệu và cấu hình của bảng
![[Pasted image 20241015111331.png]]

# Example

```js
muiPaginationProps: {
58      rowsPerPageOptions: [5, 10, 15],
59      variant: 'outlined',
60    },
61    paginationDisplayMode: 'pages',
```
Đoạn code trên dùng để custom :
- Số lượng record được tùy chọn để trả về mỗi trang
- Kiểu phân trang

`MRT_GlobalFilterTextField`: được dùng để gọi tool Filter
`MRT_TablePagination`: được dùng để gọi phân trang


```js
return (

65    <Stack sx={{ m: '2rem 0' }}>
66      <Typography variant="h4">My Custom Headless Table</Typography>
67      <Box
68        sx={{
69          display: 'flex',
70          justifyContent: 'space-between',
71          alignItems: 'center',
72        }}
73      >
74        {/**
75         * Use MRT components along side your own markup.
76         * They just need the `table` instance passed as a prop to work!
77         */}
78        <MRT_GlobalFilterTextField table={table} />
79        <MRT_TablePagination table={table} />
80      </Box>
81      {/* Using Vanilla Material-UI Table components here */}
82      <TableContainer>
83        <Table>
84          {/* Use your own markup, customize however you want using the power of TanStack Table */}
85          <TableHead>
86            {table.getHeaderGroups().map((headerGroup) => (
87              <TableRow key={headerGroup.id}>
88                {headerGroup.headers.map((header) => (
89                  <TableCell align="center" variant="head" key={header.id}>
90                    {header.isPlaceholder
91                      ? null
92                      : flexRender(
93                          header.column.columnDef.Header ??
94                            header.column.columnDef.header,
95                          header.getContext(),
96                        )}
97                  </TableCell>
98                ))}
99              </TableRow>
100            ))}
101          </TableHead>
102          <TableBody>
103            {table.getRowModel().rows.map((row, rowIndex) => (
104              <TableRow key={row.id} selected={row.getIsSelected()}>
105                {row.getVisibleCells().map((cell, _columnIndex) => (
106                  <TableCell align="center" variant="body" key={cell.id}>
107                    {/* Use MRT's cell renderer that provides better logic than flexRender */}
108                    <MRT_TableBodyCellValue
109                      cell={cell}
110                      table={table}
111                      staticRowIndex={rowIndex} //just for batch row selection to work
112                    />
113                  </TableCell>
114                ))}
115              </TableRow>
116            ))}
117          </TableBody>
118        </Table>
119      </TableContainer>
120      <MRT_ToolbarAlertBanner stackAlertBanner table={table} />
121    </Stack>
122  );
123};
124
125 export default Example;
```

