## Thao tác sử dụng Redux để lưu trạng thái các state
- Sử dụng redux để lưu state đóng mở của các dropdown
Hiện tại có 2 widget 

1 widget bên ngoài 
1 widget con
widget con chứa 1 state
state đó để mở sub menu
vấn đề: khi chuyển trang thì sub menu đó cũng sẽ mất đi
Và mỗi lần tạo item mới sẽ reset states vì vậy nên lưu ở đó không có nghĩa

Item chứa states và widget chứa nhiều items

Code redux cho menu Item

`// state submenu from Redux`
`const subMenuState = useSelector(`

`(state: IMState) =>`

`state.widgetsState?.[${eSidebar.storeKey}]?.submenu || {}`

`);`



`// Function toggle submenu use dispatch to change state submenu`

`const handleToggleSubMenu = (index: number) => {`

`const updatedSubMenuState = {`

`...subMenuState,`

`[index]: !subMenuState[index], // Confirm atr: index existed`

`};`

  

`dispatch(`

`appActions.widgetStatePropChange(`

`eSidebar.storeKey,`

`eSidebar.sectionKey,`

`updatedSubMenuState`

`)`

`);`

`};`