# Code thống kê điểm danh

⚠️WARNING⚠️ *** Khi xảy ra lỗi cần bấm F5 để tải lại trang web để xác thực danh tính thành công mới dùng tiếp được ***

## Bước 1: Mở trang GV vào phần Lớp của tôi 
==> Bấm vào tên 1 lớp sau đó bấm phím F12 để mở cửa sổ Console

## Bước 2: Copy code dưới đây paste vào rồi xem log. 
Khi hiện ra danh sách thì copy vào file excel là ok

```
var pathArray=window.location.pathname.split("/");let lop=pathArray[pathArray.length-1];var group_name="",psubject_code="",psubject_name="";let link_lop="https://gv.poly.edu.vn/teacher/group/get_by_id/"+lop+"?campus_code=ph";fetch(link_lop).then(function(e){return e.json()}).then(function(e){group_name=e.data.group_name,psubject_code=e.data.psubject_code,psubject_name=e.data.psubject_name,fetch("https://gv.poly.edu.vn/teacher/group/get_attendance_by_group_id/"+lop+"?campus_code=ph").then(function(e){return e.json()}).then(function(e){let t="Lớp	M\xe3 m\xf4n	M\xe3 sinh vi\xean	Họ v\xe0 t\xean	Số buổi nghỉ\n";e.data.members.forEach(e=>{e.absent>0&&(t+=group_name+"	"+psubject_code+"	"+e.user_code+"	"+e.fullname+"	"+e.absent+"\n")}),console.log(t); document.write("<h2>Copy nội dung paste vào excel sẽ tự chia cột</h2><a href='https://gv.poly.edu.vn/teacher/my_class'>Trở lại DS lớp</a><br><br><br><textarea cols='100' rows='20'>" + t + "</textarea>");})});
```

## Bước 3: Trong file excel có thể xử lý dữ liệu như thế nào đó thì tùy theo nhu cầu của mỗi GV
Chúc mọi người thành công!
