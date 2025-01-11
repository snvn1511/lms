# Tool tạo nhanh ô tìm kiếm trong bảng


## B1 Hiển thị bảng trên trang web
## B2 Bấm F12 để vào cửa sổ console
## B3 Paste code dưới đây vào cửa sổ console enter

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
## B4 Sau khi tìm kiếm có thể chọn cả bảng và copy bảng


# Tool tạo nút export bảng thành file csv

```
// Hàm xuất bảng HTML ra file CSV với mã hóa UTF-8 để tránh lỗi font
function exportTableToCSV(filename) {
    const table = document.querySelector('#inspection-body table');
    let csv = [];

    // Lặp qua từng hàng của bảng
    table.querySelectorAll('tr').forEach(row => {
        let rowData = [];
        // Lặp qua từng ô của hàng
        row.querySelectorAll('th, td').forEach(cell => {
            rowData.push('"' + cell.innerText.replace(/"/g, '""') + '"');
        });
        csv.push(rowData.join(','));
    });

    // Tạo file CSV với mã hóa UTF-8
    const csvContent = '\ufeff' + csv.join('\n');
    const csvFile = new Blob([csvContent], { type: 'text/csv;charset=utf-8;' });
    const csvUrl = URL.createObjectURL(csvFile);

    // Tạo thẻ a để tải file
    const downloadLink = document.createElement('a');
    downloadLink.href = csvUrl;
    downloadLink.download = filename;
    document.body.appendChild(downloadLink);
    downloadLink.click();
    document.body.removeChild(downloadLink);
}
// tạo nút bấm

  $("#inspection-body").prepend( jQuery('<button onclick="exportTableToCSV(\'bang_du_gio.csv\')">Export CSV</button>') );
// Gọi hàm khi click vào nút
// <button onclick="exportTableToCSV('table_export.csv')">Export CSV</button>

```
