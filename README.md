# Trang cập nhật NSNN (GitHub Pages)

Phần mềm NSNN đọc `https://luandiepueh.github.io/NSNN/version.json` để biết có bản mới
(`nsnn/updater.py` › `UPDATE_MANIFEST_URL`). Gói cài `NSNN_<phiên bản>.zip` nằm ở GitHub Releases
của kho `luandiepueh/NSNN`. Thư mục này không được đóng gói vào NSNN.exe.

## Thiết lập lần đầu

1. Trên github.com tạo kho **Public** tên `NSNN` (tài khoản `luandiepueh`), không cần README.
2. Mở PowerShell tại thư mục `update_site\`:

   ```powershell
   git init
   git add .
   git commit -m "Khoi tao trang cap nhat NSNN"
   git branch -M main
   git remote add origin https://github.com/luandiepueh/NSNN.git
   git push -u origin main
   ```

3. Kho → **Settings › Pages** → Source: branch `main`, thư mục `/ (root)`. Sau vài phút mở
   `https://luandiepueh.github.io/NSNN/version.json` phải thấy nội dung tệp.
4. Cài GitHub CLI (`winget install --id GitHub.cli`) rồi `gh auth login`.

Đổi tên kho khác thì sửa `GITHUB_REPO`, `UPDATE_MANIFEST_URL` trong `nsnn/updater.py` và `$REPO` trong
`tools\phat_hanh.ps1`.

## Mỗi lần phát hành

1. Sửa `version.json`: `version`, `release_date`, `download_url`
   (`https://github.com/luandiepueh/NSNN/releases/download/<phiên bản>/NSNN_<phiên bản>.zip`), `changelog`.
2. `powershell -ExecutionPolicy Bypass -File tools\phat_hanh.ps1`.

Các máy đang dùng NSNN.exe tự kiểm tra mỗi 6 giờ (và khi mở phần mềm); thấy bản mới thì hiện nút
**Bản mới …** trên thanh trên cùng → Hệ thống › Cập nhật phần mềm → **Tải và cài đặt** (chỉ Quản trị).

Lưu ý: bản đầu tiên có chức năng cập nhật (1.2.0) phải cài tay một lần; từ đó về sau mới tự cập nhật.
