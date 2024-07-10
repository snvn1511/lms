Tool tạo nhanh ô tìm kiếm trong bảng

```
$(document).ready(function(){

  $("#inspection-body").prepend( jQuery('<input type="text" id="mySearch" placeholder="Nhập từ khóa cần tìm, VD: Nguyễn Văn A" style="width:100%; padding: 10px;    border-radius: 10px;    background-color: yellow;    border-color: red;" />') );

  $( "#inspection-body" ).on( "keyup", '#mySearch', function( event ) {
    event.preventDefault();
        
        var value = $(this).val().toLowerCase();
      console.log(value);
        $("#inspection-body  table tbody tr").filter(function() {
          $(this).toggle($(this).text().toLowerCase().indexOf(value) > -1)
        });
    
    });
});

```

