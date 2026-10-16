# Spare Brain

**Remember less. Live more.**

Ứng dụng web nhỏ để quản lý đồ dùng và voucher trong cuộc sống cá nhân: món nào để ở đâu, món nào sắp hết hạn, voucher nào sắp mất hiệu lực.

Toàn bộ app là **một file `index.html`**. Không cần cài đặt, không cần build, không cần tài khoản. Mở file bằng trình duyệt là dùng được. Dữ liệu nằm trong trình duyệt của bạn.

> **Trạng thái:** bản khởi đầu (skeleton). Đủ dùng và đủ để hình dung hướng phát triển, nhưng còn nhiều thứ chưa có. Xem phần [Chưa có](#chưa-có) và [Hướng phát triển](#hướng-phát-triển).

<!-- Thêm ảnh chụp màn hình vào đây, ví dụ: ![Trang Cần chú ý](docs/screenshot-attention.png) -->

## Tính năng

**Cần chú ý**: trang tổng hợp những thứ cần xử lý ngay.
- Hai nhóm tách biệt: **Đã quá hạn** (đồ đã hết hạn) và **Sẽ hết hạn** (voucher trong 24 giờ tới và đồ dùng trong vòng N ngày).
- N mặc định là 3, nhập lại được ngay trên tiêu đề mục và kết quả cập nhật theo. Voucher có đếm ngược.
- Số đỏ trên menu và dải cảnh báo ở đầu trang khi có voucher sắp hết hạn.

**Kho đồ dùng**: mỗi món có tên, phân loại, số lượng, đơn vị, hạn sử dụng, giá mua, ngày mua, vị trí lưu trữ và ghi chú. Hạn sử dụng và số lượng là bắt buộc với mọi món.
- **Thanh tìm kiếm** ở đầu trang: gõ tên món để tìm trong toàn bộ kho, không phân biệt hoa thường và dấu tiếng Việt. Kết quả cho biết món đó đang được cất ở đâu (cột Vị trí). Tìm kiếm chỉ khớp theo tên món, không khớp theo vị trí, phân loại hay ghi chú.
- Bên dưới là dropdown *Tìm theo phân loại*: chọn một phân loại (hoặc Tất cả) để xem danh sách đồ bên trong.
- Có sẵn 13 phân loại (Skincare, Đồ tươi sống, Đồ khô, ...).
- **Vị trí lưu trữ** là ô nhập tự do khi thêm món (ví dụ "ngăn mát tủ lạnh"), không bắt buộc và không có danh sách vị trí hay bộ lọc theo vị trí.
- Thêm, đổi tên, xóa phân loại ngay trong app. Thêm mới nhanh ngay trong form "Thêm đồ dùng".
- **Phân loại mặc định của app** (13 mục) chỉ xóa được, không đổi tên được; nếu không có mục phù hợp, hãy tạo mục mới. Mục bạn tự tạo thì sửa và xóa thoải mái. Xóa một mục mặc định rồi tạo lại đúng tên đó thì mục mới được tính là của bạn: sửa được và không bị dịch theo ngôn ngữ.
- Chỉnh nhanh số lượng bằng nút +/−.

**Kho voucher**: tên voucher, voucher của app nào, ngày giờ hết hạn. Đánh dấu "Đã dùng" thì voucher không còn được báo. Voucher xếp theo mức khẩn cấp.

**Ideas**: chỗ ghi nhanh những ý tưởng chợt nảy ra. Thêm, sửa, xóa, đánh số, sao chép tất cả. Ý tưởng lưu trong trình duyệt như mọi dữ liệu khác và nằm trong file sao lưu JSON.

**Cài đặt**: gồm hai phần riêng là *Ngôn ngữ* và *Sao lưu*. Mục *Sao lưu* dùng để xuất và nhập dữ liệu bằng JSON hoặc CSV, có kiểm tra dữ liệu trùng.

**Cài đặt**: đổi ngôn ngữ giữa **Tiếng Việt** và **English**. Tên món, phân loại, vị trí do bạn tự nhập được giữ nguyên, không bị dịch. Các phân loại mặc định (Đồ tươi sống, Đồ khô, ...) hiển thị theo ngôn ngữ đang chọn. Ngày hiển thị dạng `dd/mm/yyyy` (Tiếng Việt) hoặc `14 Oct 2026` (English).

**Giao diện**: ưu tiên máy tính, tự co lại cho điện thoại (menu chuyển xuống thanh dưới, bảng chuyển thành thẻ). Tự đổi sáng/tối theo hệ thống.

## Cách chạy

1. Tải `index.html` về.
2. Mở bằng trình duyệt (Chrome, Edge, Firefox, Safari).

Hoặc đưa lên bất kỳ dịch vụ host tĩnh nào (GitHub Pages, Netlify, Vercel, Cloudflare Pages).

Có thể nhập thử [`sample-data.json`](sample-data.json) qua **Cài đặt → Sao lưu → JSON** để xem app khi đã có dữ liệu.

Lưu ý: app tải font Be Vietnam Pro từ Google Fonts. Không có mạng thì app vẫn chạy, chỉ dùng font hệ thống thay thế.

## Dữ liệu

Dữ liệu lưu trong `localStorage` của trình duyệt, khóa `sparebrain:v1` (ngôn ngữ lưu riêng ở khóa `sparebrain:lang`). Không có gì được gửi đi đâu cả.

**Hệ quả cần biết:**
- Dữ liệu gắn với một trình duyệt trên một thiết bị. Xóa dữ liệu duyệt web hoặc đổi máy là mất nếu chưa sao lưu.
- Mở file bằng `file://` và mở từ một địa chỉ web là hai nơi lưu khác nhau, dữ liệu không dùng chung.
- Hãy xuất file JSON định kỳ.

**Cấu trúc dữ liệu** (cũng là cấu trúc file JSON khi xuất):

```json
{
  "items": [],
  "cats": ["Skincare", "Đồ tươi sống"],
  "vouchers": [],
  "ideas": []
}
```

| Món đồ (`items`) | Ý nghĩa |
|---|---|
| `id` | Mã định danh |
| `name` | Tên món |
| `category` | Phân loại (khớp với `cats`) |
| `location` | Vị trí lưu trữ, văn bản tự do |
| `qty`, `unit` | Số lượng, đơn vị |
| `expiry` | Hạn dùng, dạng `yyyy-mm-dd`, bắt buộc |
| `price` | Giá mua (VND) |
| `purchased` | Ngày mua, dạng `yyyy-mm-dd`, có thể để trống |
| `note` | Ghi chú |

| Voucher (`vouchers`) | Ý nghĩa |
|---|---|
| `id` | Mã định danh |
| `name`, `app` | Tên voucher, app phát hành |
| `expiry` | Hạn dùng, dạng `yyyy-mm-ddTHH:mm` (giờ địa phương) |
| `used` | `true` nếu đã dùng |

| Ý tưởng (`ideas`) | Ý nghĩa |
|---|---|
| `id` | Mã định danh |
| `t` | Nội dung ý tưởng |
| `d` | Ngày tạo, dạng `yyyy-mm-dd` |
| `ts` | Mốc thời gian lúc tạo, dùng để sắp xếp |
| `edited` | Ngày sửa gần nhất (chỉ có khi đã sửa) |

## Sao lưu (xuất/nhập dữ liệu)

| | JSON | CSV |
|---|---|---|
| Gồm | Món đồ, voucher, phân loại, ý tưởng | Chỉ món đồ |
| Dùng để | Sao lưu và chuyển máy | Xem hoặc sửa trong Excel, Google Sheets |

**Kiểm tra trùng khi nhập:**
- Món trùng khớp hoàn toàn với dữ liệu hiện có ở mọi trường thì bị bỏ qua. Nếu toàn bộ file đều trùng, app báo cảnh báo và không đổi gì.
- Chỉ cần khác một trường là món được thêm mới. Với JSON, nếu cùng `id` mà nội dung khác thì cập nhật món đó.
- Nhập là **gộp** vào dữ liệu hiện có, không thay thế. Món bạn đã xóa sau lần sao lưu sẽ quay lại nếu nhập file cũ.

**Định dạng CSV:** mã hóa UTF-8, dòng đầu là `sep=,` (để Excel tách cột đúng), dòng tiếp theo là tiêu đề: `Tên món, Phân loại, Số lượng, Đơn vị, Hạn sử dụng, Giá mua (VND), Ngày mua, Vị trí, Ghi chú` (khi giao diện là English thì tiêu đề là `Item name, Category, Quantity, Unit, Expiry date, Price (VND), Purchase date, Location, Notes`). Khi nhập, app nhận tiêu đề của cả hai ngôn ngữ. Khi nhập, app nhận cả ngày `yyyy-mm-dd` và `dd/mm/yyyy`. Cần có cột `Tên món` (hoặc `Item name`); dòng nào thiếu tên, hạn sử dụng hoặc số lượng sẽ bị bỏ qua.

## Chưa có

- **Dữ liệu chỉ ở một thiết bị**, chưa đồng bộ giữa điện thoại và máy tính.
- **Nhắc hạn chỉ hiện khi đang mở app**, chưa có thông báo đẩy.
- Chưa phải PWA (chưa cài được lên màn hình chính như app).
- Chỉ có hai ngôn ngữ (Tiếng Việt, English), tiền tệ cố định là VND.
- Chưa có kiểm thử tự động.
- CSV chưa gồm voucher.
- Toàn bộ code nằm trong một file, chưa tách module.

## Hướng phát triển

- [ ] Thu/chi theo tháng/năm, biểu đồ
- [ ] Tiết kiệm/đầu tư, nhắc đáo hạn, bảng lãi suất ngân hàng (nhập tay)
- [ ] To-do hằng ngày
- [ ] Wishlist theo tháng/quý
- [ ] Bảo hành và hóa đơn
- [ ] Giấy tờ và hạn định kỳ (đăng kiểm, bảo hiểm, hộ chiếu)
- [ ] Chi phí định kỳ và gói đăng ký
- [ ] Danh sách đi chợ tự gợi ý từ món sắp hết
- [ ] Ngân sách theo danh mục, sổ nợ, mục tiêu tiết kiệm
- [ ] Quét mã vạch để thêm đồ nhanh
- [ ] PWA và thông báo đẩy
- [ ] Đồng bộ nhiều thiết bị (cần backend, ví dụ Supabase hoặc Firebase)
- [ ] Tách mã nguồn thành project nhiều thư mục

## Đóng góp

Mọi góp ý và pull request đều được hoan nghênh. Nếu muốn thêm một module mới, hãy mở issue mô tả ý tưởng trước.

## Giấy phép

[Chọn giấy phép, ví dụ MIT] — xem file `LICENSE`.
