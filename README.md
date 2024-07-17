## I.Folder components chứa các components : nav, footer, userlisting, userlistings, spinner
 1. Component nav (được gọi ở component userListings) nhận prop deleteUserChecked: chứa 2 button delete và add employee
        -  khi ta nhấn vào button add employee thì sẽ chuyển hướng sang trang addemployee nhờ sử dụng router link. Ở component add employee chúng ta sử dụng usesate để set thông tin của employee mới. Component adduserpage nhận vào một prop addUserSubmit nhận dữ liệu là một new employee trong function submitForm. function submitForm được gọi trong sự kiện onsubmit ở form điền thông tin của employee. Ở component main sẽ có một function adduser sử dụng phương thức post để add employee, function adduser sẽ được gọi thông qua  prop addUserSubmit trong component add employee.
        -  khi ta nhấn vào button delete: sự kiện onclick được kích hoạt và gọi funtion deleteUserChecked
 2. component userlistings (render tất cả employee, được gọi trong component Homepage)
        -  sử dụng usesate để set dữ liệu
        -  sử dụng useeffect để lấy dữ liệu từ api
        -  function deleteUser xóa dữ liệu qua id nhận vào bằng phương thức delete
        -   funciton hanleCheckboxChange để lưu id của employee đã được chọn
        -  function deleteUserChecked xóa các employee được chọn bằng cách map dữ liệu từ checkedUser để lấy id đã được lưu ở function hanleCheckboxChange
        -  function hanlePageClick nhận dữ liệu data setCurrentPage cập nhận trang hiện tại
        -  offset: vị trí bắt đầu của dữ liệu tính bằng cách lấy trang hiện tại nhân với số phần tử của trang
        -  currentUsers:  dữ liệu của User được tính bằng cách cắt dữ liệu từ vị trí bắt đầu  -> vị trí bắt đầu - số phần tử của trang
        -  totalPages là tổng số trang được tính làm tròn lên lấy chiều dài của mảng user chia số phần tử
        -  Nhận component Nav gọi funciton deleteUserChecked qua prop deleteUserChecked
        -  Phần tbody ta cho currentUsers.map truyền dữ liệu cho component UserListing để render ra màn hình. Ở component UserListing có 3 prop user, deleteUser và handleCheckboxChange lần lượt nhận các dữ liệu và hàm tương ứng
        - component Footer có prop handlePageClick nhận function handlePageClick và prop totalPages dữ liệu totalPages
 3. Component userlisting(render dữ liệu từng emloyee,được gọi ở component userListings):sử dụng link trong router, toast trông react-toastify
    nhận vào 3 prop user, deleteUser và handleCheckboxChange
        - function onDeleteClick nhận dữ liệu id trong hàm này sẽ  truyền id vào prop deleteUser để xóa User tương ứng. nếu xóa thành công sẽ hiển thị toast để thông báo.function được gọi khi người dùng nhấn vào button trash.
        - funtion onchangeChecked lấy dữ liệu của người được checked và gửi dữ liệu đó vào prop handleCheckboxChange. function được gọi trong input checkbox và sự kiện onchange .
        - khi button eye được click vào sẽ chuyên sang userPage để show tất cả dữ liệu của employee đó
        - khi click vào button pen sẽ chuyển sang Editpage
        - khi click vào button trash thì sẽ gọi đến function onDeleteClick
 4. Component Footer (chứa phần phân trang của trang web,được gọi ở component userListings): sử dụng ReactPaginate trong react-paginate. nhận vào 2 prop handlePageClick và totalPages
