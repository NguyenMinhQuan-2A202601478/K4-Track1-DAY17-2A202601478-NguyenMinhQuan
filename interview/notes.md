# Interview Record — lượt Nguyễn Minh Quân làm interviewer

## Thông tin buổi phỏng vấn

| Mục | Nội dung |
|---|---|
| Interviewer | Nguyễn Minh Quân · 2A202601478 |
| Mã người tham gia | `2A202601478` |
| Ngày / giờ | 13:02 · 17/08/2026 |
| Hình thức | Trực tiếp |
| Đúng tiêu chí tuyển | **Có** — có sự kiện cụ thể trong 7 ngày gần đây |
| Đã xin phép ghi âm trước khi bắt đầu | **Có** — P01: *"Ừ được, thoải mái đi."* |
| File bản ghi | [`Voice ghi âm/P01/P01.m4a`](../Voice%20ghi%20âm/P01/P01.m4a) |
| Nhánh điều tra | Bộ 1 — phân định A vs B |

---

## Interview Record — Facts

| Điều cần giữ lại | Ghi chép |
|---|---|
| **Câu chuyện gần nhất:** user đang ở đâu và cố làm gì? | **Tối trước hôm có lab, khoảng hơn 22h.** Ngồi trong phòng, mở laptop **đọc trước tài liệu cho kịp buổi lab hôm sau**. Đã đọc qua phần bảng thuật ngữ, tự thấy *"hiểu hiểu"*. **Tắc ở đoạn RRF.** |
| **User đã thực sự làm gì?** | Nghĩ tới việc đọc lại phần trước nhưng **không thực hiện**. Mở tab mới, tra Google với từ khoá **"RRF reranking là gì"**. Kết quả ra các bài tiếng Anh. Hôm sau vào lab thì làm bài bằng **code mẫu**. |
| **Khó khăn và workaround đã dùng** | Khó khăn: **không định vị được phần nào cần đọc lại** — *"không biết đọc lại từ chỗ nào. Tài liệu dài, cuộn lên thì thấy toàn chữ."* Workaround: tra Google → thất bại (*"ra mấy bài tiếng Anh, đọc còn khó hơn"*) → hôm sau dựa vào code mẫu. |
| **Hậu quả hoặc chi phí** | Qua được phần code nhờ mẫu, **nhưng không giải thích được lựa chọn**: *"đến phần phải giải thích vì sao chọn top-k đó thì mình chịu, ghi đại."* Tức là hoàn thành về hình thức, còn nguyên lỗ hổng bên dưới. |
| **Điều bất ngờ, trái giả thuyết, hoặc một exact quote** | Quote đắt nhất, P01 tự tổng kết: <br>*"Cái cảm giác biết là mình hổng mà không biết hổng chỗ nào để đi vá."* <br>Đây là tín hiệu phù hợp với Hypothesis A, không phải kết luận xác nhận giả thuyết. |

---

## Đọc kết quả theo Big 3

| # | Điều cần học | User đã nói gì | Làm nhóm tin hơn / nghi ngờ? |
|---|---|---|---|
| 1 | Việc mắc kẹt có thật và gần đây không? | Tối trước hôm lab, ~22h, trong phòng, laptop, đọc trước tài liệu, tắc ở đoạn RRF | **Tin hơn.** Có mốc thời gian, nơi chốn, động cơ (kịp lab) và tên đoạn cụ thể |
| 2 | Lúc mắc kẹt, họ có tự chỉ ra được mình thiếu gì không? *(A vs B)* | *"không biết đọc lại từ chỗ nào"*; từ khoá tra cứu là **"RRF reranking"** — tên khái niệm **trong bài** | **Tin hơn rõ rệt vào A.** Hai bằng chứng độc lập cùng chỉ một hướng |
| 3 | Họ đã làm gì và trả giá bao nhiêu? | Google thất bại → dựa vào code mẫu → *"ghi đại"* phần giải thích top-k | **Tin hơn.** Có consequence quan sát được, không chỉ là khó chịu thoáng qua |

**Tạm nghiêng về Pain Hypothesis nào sau buổi này: A**

**Vì sao:** P01 nói họ *đã nghĩ tới* việc đọc lại nhưng *"không biết đọc lại từ chỗ nào"*. Cùng với việc tra cứu `RRF reranking` — tên khái niệm đang gặp — đây là tín hiệu nghiêng về khó khăn định vị phần nền. Một lượt ngắn chưa đủ để kết luận P01 hoàn toàn không xác định được nguyên nhân.

**Hypothesis C: chưa kiểm.** Buổi này không có câu nào hỏi về AI tutor trên VLearn.

---

## Tín hiệu trái chiều — phải giữ, không được làm tròn

Câu *"Tài liệu dài, cuộn lên thì thấy toàn chữ"* mang màu **Hypothesis B**: kể cả khi biết phải quay lại, việc điều hướng ngược trong tài liệu dài tự nó đã là một rào cản. Buổi này nghiêng A nhưng **có thành phần B xen vào**, không phải A thuần.

---

## Đối chiếu với lượt P02

| | Định vị được phần nền tại chỗ? | Cái chặn thật | Nghiêng về |
|---|---|---|---|
| **P01** *(lượt này)* | ❌ Không — *"không biết đọc lại từ chỗ nào"* | Không chẩn đoán được | **A** |
| **P02** *(lượt Huy)* | Có nêu *"chưa đọc mấy cuốn sách cô gợi ý"*, nhưng chưa biết họ nhận ra điều này lúc nào | Sợ lỡ bài sau nếu dừng lại | **Tạm nghiêng B** |

Hai buổi cho hai kết quả ngược nhau. Đây **không phải lỗi phỏng vấn** — nó gợi ý rằng A và B là hai rào cản khác nhau ở hai nhóm người khác nhau, hoặc hai giai đoạn khác nhau của cùng một người. Cần thêm buổi để biết rào cản nào phổ biến hơn.

---

## Khoảng trống của lượt này

| Chưa hỏi | Mất gì |
|---|---|
| *"Biết ngay lúc đó hay nghĩ lại mới biết?"* | Chưa loại trừ hoàn toàn khả năng P01 chỉ mơ hồ khi kể lại |
| *"Có bôi đen hỏi tutor không?"* | **Hypothesis C không được kiểm** |
| *"Dừng ở đó bao lâu? Tra bao lâu?"* | Không đo được độ lớn của pain |
| *"Có hỏi ai không — Discord, bạn, Lab Coach?"* | Không biết các kênh hỗ trợ hiện có đã được thử chưa |
| *"Lần trước đó bạn tắc kiểu vậy là bài nào?"* | Chưa xác nhận pattern có lặp |

---

## Cảnh báo tự kiểm

- Không có lời khen hay câu "mình sẽ dùng" nào trong buổi này ✅
- Không có câu nào làm lộ solution ✅
- Câu hỏi thứ hai bị hỏi thành **câu kép** (*"gặp khó khăn gì, xảy ra khi nào?"*) — P01 chỉ trả lời vế thời gian; vế nội dung phải hỏi vòng sau mới ra. Đã sửa trong guide, xem [README mục 3.9](../README.md#39-đã-sửa-gì-sau-khi-luyện--changelog).
- Đây là buổi luyện tập — **không tuyên bố validated**.
