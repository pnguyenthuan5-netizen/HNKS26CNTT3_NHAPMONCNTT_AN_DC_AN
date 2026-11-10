# BÀI LÀM –(CHỦ ĐỀ QUẢN LÝ MODEL AI)

- **Mã đề:**
- **Họ tên:*Nguyễn Thuận Phát*
- **Lớp:*CNTT3*
- **Link repository:**
- **Hệ điều hành (Windows/macOS):**

## 4.2. Thao tác máy tính cơ bản bằng CLI

### Các lệnh đã chạy

```shell
ls -Force
 mv .\tai_lieu_ban_giao.txt .\docs\
 mkdir backup                                                                 cp .\data\chi_phi_model_thang_11.xlsx .\backup\
    rm .\model_cache_01.tmp
cd .\logs\
### Kết quả liệt kê toàn bộ dự án (Windows: Get-ChildItem -Recurse -Force; macOS: ls -aR)

```text
 Directory:
    C:\Users\admin\Downloads\MiniPrjoect\starter-kit\quan-ly-model-ai\logs


Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a----        11/10/2026   1:41 PM           1234 inference.log


PS C:\Users\admin\Downloads\MiniPrjoect\starter-kit\quan-ly-model-ai\logs>

```

## 4.3. Lọc log vận hành Model AI

### a) Lệnh lọc các dòng ERROR

```shell
 cat .\logs\inference.log | Select-String "ERROR" > .\logs\loi_model.txt

```

### 2 dòng đầu tiên trong logs/loi_model.txt

```text
2026-11-10 08:27:45 ERROR POST /v1/chat/completions model=CLAUDE-35
2026-11-10 08:31:12 ERROR POST /v1/audio/transcriptions model=WHISPER-V3

```

### b) Lệnh đếm số dòng WARNING và kết quả

```shell
 (cat .\logs\inference.log | Select-String "WARNING").count

```

```text
5
```

## 4.4. Chạy script tong_hop (.ps1 hoặc .sh)

### Lệnh chạy (Windows: nếu dùng Phụ lục 2 thì ghi cả 2 lệnh)

```shell
Get-Content .\logs\inference.log | Select-String "WARNING" >> .\logs\tong_hop.txt
Get-Content .\logs\inference.log | Select-String "ERROR" | Measure-Object >> .\logs\tong_hop.txt

```

### Nội dung file logs/tong_hop.txt

```text
# Script: tong_hop.ps1
# Tac gia: Nguyen Thuan Phat
# Ngay tao: 10/11/2026
Write-Host "Dang tao bao cao ... "
" === BAO CAO VAN HANH MODEL AI === " > >logs/tong_hop.txt
Get-Content .\logs\inference.log | Select-String "WARNING" >> .\logs\tong_hop.txt
Get-Content .\logs\inference.log | Select-String "ERROR" | Measure-Object >> .\logs\tong_hop.txt
Write-Host "Hoan thanh!"

```

## 4.5. README.md và bảo vệ thông tin bí mật

> README.md, .gitignore và .env.example được chấm trực tiếp trên file ở gốc dự án. Đánh dấu `[x]` vào các mục đã làm để tự kiểm tra.

- [ ] README.md: Heading 1, hình ảnh (`![Alt](path)`), mô tả có **in đậm**, _in nghiêng_ và `inline code`, bảng, code block, task list, blockquote
- [ ] .gitignore có dòng `.env` (tên file đúng, không có đuôi .txt)
- [ ] .env.example có đủ tên biến, giá trị để trống (tên file đúng, không có đuôi .txt)

## 4.6. Kiểm tra trang web bằng DevTools (F12) và báo cáo lỗi

### Bảng lỗi

| STT | Tab DevTools phát hiện lỗi | Tên file hoặc thông báo lỗi | Cách khắc phục |
| --- | -------------------------- | --------------------------- | -------------- |
| 1   | Network                           |     file:///D:/MiniPrjoect/starter-kit/quan-ly-model-ai/web/images/logo.png                            |    Sửa lại đường dẫn file/tên file            |
| 2   | Console                           |     GET file:///D:/MiniPrjoect/starter-kit/quan-ly-model-ai/web/images/logo.png net::ERR_FILE_NOT_FOUND                        |   Sửa lại đường dẫn file/tên file             |

> Ảnh chụp màn hình lưu trong thư mục `evidence/` (network.png, console.png).

### Báo cáo lỗi gửi trưởng nhóm

- Context: Tên file trong index.html bị nhập sai/sai đường dẫn
Expected: Lỗi được sửa, web chạy mượt mà không báo lỗi
Actual: Lỗi chưa được sửa, web vẫn báo lỗi
Log: GET file:///D:/MiniPrjoect/starter-kit/quan-ly-model-ai/web/images/logo.png net::ERR_FILE_NOT_FOUND

### Câu tìm kiếm Google

```text
site:stackoverflow.com "ERR_FILE_NOT_FOUND"

```

## 4.7. Excel

> Phần Excel được chấm trực tiếp trên file `data/chi_phi_model_thang_11.xlsx`, không cần ghi vào đây.
