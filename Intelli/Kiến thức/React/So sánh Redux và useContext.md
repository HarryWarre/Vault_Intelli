Tags: #redux #usecontext #compare
- useContext và Redux đều cung cấp các cách để quản lý và chia sẻ trạng thái giữa các thành phầm. Cả hai ddeeif hoạt động và quản lý dữ lieuj toàn cục để chia sẻ và truy cập từ bất kỳ thành phần nào có trong cây DOM.
- Nhưng chúng có mục đích và trường hợp sử dụng khác nhau

Menu
- [[UseContext]]
- [[Redux]]
- [[#Sự khác nhau Redux và useContext]]

# Sự khác nhau Redux và useContext


| Tiêu chí               | Redux                                                            | useContext                                                              |
| ---------------------- | ---------------------------------------------------------------- | ----------------------------------------------------------------------- |
| Mục đích               | Quản lý state toàn cục phức tạp một cách tổ chức                 | Truyền dữ liệu giữa các component mà không cần truyền props             |
| Khả năng mở rộng       | Phù hợp với ứng dụng lớn, nhiều state phức tạp                   | Phù hợp với ứng dụng nhỏ và trung bình với state không quá phức tạp     |
| Cơ chế cập nhật state  | Sử dụng action và reducer để cập nhật state theo cách có tổ chức | State được cập nhật trực tiếp hoặc thông qua hàm trong context provider |
| Tối ưu hiệu suất       | Tối ưu hóa re-renders với các selector và midleware              | Dễ gây ra re-renders không cần thiết                                    |
| Tích hợp middleware    | Dễ dàn tích hợp midleware                                        | Không có midleware sẵn có                                               |
| Boilerplate            | Yêu cầu nhiều boilerplate (action, reducer, store, etc)          | Ít boiler hơn so với Redux                                              |
| Khả năng chia sẻ state | Tất cả component trong ứng dụng có thể truy cập cùng một store   | Chỉ các component con của Context.Prover có thể truy cập                |

