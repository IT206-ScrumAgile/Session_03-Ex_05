# THIẾT KẾ BACKLOG CHO TÍNH NĂNG THEO DÕI CHUYẾN GHÉP

## Phần 1 – Thiết kế

**Bài toán tự xác định:** khách đi xe ghép không biết xe đang đón ai, bao giờ đến lượt mình và phải làm gì khi có vấn đề. Phạm vi Epic gồm hai nhóm giá trị: (1) biết tình hình chuyến đi, (2) được hỗ trợ khi có sự cố.

```
EPIC: Theo dõi chuyến ghép
│
├── FEATURE 1: Nắm tình hình chuyến đi
│   ├── US1: As a khách đi ghép, I want xem vị trí xe theo thời gian thực trên bản đồ,
│   │        so that tôi biết xe đang ở đâu và đã đi được bao xa.
│   └── US2: As a khách đi ghép, I want xem thứ tự đón các khách cùng chuyến (tên rút gọn)
│            và giờ dự kiến đến lượt mình, so that tôi biết xe đang đón ai và chuẩn bị đúng lúc.
│
└── FEATURE 2: Hỗ trợ khi có sự cố
    ├── US3: As a khách đi ghép, I want bấm nút báo sự cố ngay trong chuyến và chọn loại sự cố,
    │        so that tôi được hỗ trợ nhanh mà không phải tự tìm cách xử lý.
    └── US4: As a khách đi ghép, I want gọi hoặc nhắn nhanh cho tài xế hoặc tổng đài trong ứng dụng,
             so that tôi liên hệ được ngay khi cần mà không phải thoát khỏi chuyến đi.
```

---

## Phần 2 – Sắp xếp Product Backlog (theo giá trị cho khách)

| Thứ tự | User Story | Lý do xếp vị trí này |
|---|---|---|
| 1 | **US2** – Thứ tự đón và giờ dự kiến đến lượt | Trả lời trực tiếp 2 trong 3 nỗi đau của khách ("xe đón ai", "bao giờ đến lượt mình"); dựa trên lộ trình hệ thống đã lập nên không phụ thuộc dữ liệu từ đối tác bản đồ. |
| 2 | **US3** – Báo sự cố trong chuyến | Trả lời nỗi đau thứ 3 ("có vấn đề thì phải làm gì") và liên quan đến an toàn của khách. |
| 3 | **US1** – Vị trí xe thời gian thực | Giá trị cao nhưng phụ thuộc dữ liệu vị trí từ đối tác bản đồ nên rủi ro hơn, đặt sau các story tự làm được. |
| 4 | **US4** – Liên hệ nhanh tài xế/tổng đài | Hữu ích nhưng khách vẫn xử lý được bằng cách khác (US3 đã có kênh báo sự cố), giá trị thấp hơn nên xếp cuối. |

**Story cần chi tiết nhất: US2** (đầu Backlog, sắp vào Sprint tới). Theo D.E.E.P:
- **D**etailed appropriately: story ở đầu cột phải chi tiết nhất (quy tắc hiển thị tên rút gọn, cách tính giờ dự kiến, Acceptance Criteria) để Developers không phải hỏi lại; US4 ở cuối chỉ cần tiêu đề ngắn.
- **E**stimated: US2 được ước lượng kỹ hơn, US4 chỉ cần ước lượng sơ bộ.
- **E**mergent: US3, US1, US4 còn có thể thay đổi, bổ sung sau khi có phản hồi từ khách và từ Sprint đầu.
- **P**rioritized: thứ tự trên được sắp theo giá trị cho khách và do PO Đức quyết định.

---

## Phần 3 – Xử lý tình huống

**Tình huống 1: Đường Burndown đi ngang 3 ngày liền vì chưa có dữ liệu vị trí từ đối tác bản đồ**
- **Dấu hiệu nhận biết:** đường thực tế đi ngang (khối lượng còn lại không giảm) trong 3 ngày liên tiếp và nằm trên đường lý tưởng, khoảng cách tới đường lý tưởng ngày càng xa.
- **Ai xử lý:**
  - **Developers** báo đây là impediment ngay trong Daily Scrum của ngày đầu tiên đường đi ngang, đồng thời dùng dữ liệu giả lập (mock) để làm tiếp phần giao diện và logic không phụ thuộc đối tác.
  - **Scrum Master Lan** làm việc với đối tác bản đồ để đòi bàn giao dữ liệu, nếu cần thì leo thang lên quản lý.
  - **PO Đức** cân nhắc đổi sang làm story không phụ thuộc đối tác (như US3) hoặc cắt bớt phạm vi nếu dữ liệu vẫn chưa về, để giữ Sprint Goal.

**Tình huống 2: Đức muốn đưa nguyên Epic vào Sprint Backlog để "làm một lần cho xong"**
- **Cách xử lý:** Epic quá lớn và chưa được làm mịn nên không thể hoàn thành trong một Sprint; Sprint Backlog chỉ nên chứa các User Story đã sẵn sàng, đạt INVEST và vừa năng lực của đội.
- **Ai xử lý:**
  - **Scrum Master Lan** giải thích nguyên tắc này với Đức, nói rõ rủi ro khi nhồi cả Epic (quá tải, không có sản phẩm dùng được cuối Sprint).
  - **PO Đức** giữ Epic trong Product Backlog và chọn các story ưu tiên cao nhất (bắt đầu từ US2) cho Sprint Planning.
  - **Developers** tự quyết định số story có thể cam kết trong Sprint, phần còn lại tiếp tục được làm mịn cho các Sprint sau.
