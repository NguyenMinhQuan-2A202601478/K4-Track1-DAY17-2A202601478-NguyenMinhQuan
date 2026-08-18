# K4-Track1-DAY17-2A202601478-NguyenMinhQuan

Day 17 · Track 1 — Product Discovery: Finding and Validating Pain
Lab: Reverse solution directive → problem hypothesis → problem interview theo The Mom Test


## 1. Thông tin cá nhân và nhóm

| Mục | Nội dung |
|---|---|
| MHV | 2A202601478 |
| Họ và tên | Nguyễn Minh Quân |
| Track / Ngày | Track 1 · Day 17 |
| Tên nhóm | Nhóm AI Tutor |
| Thành viên | Nguyễn Minh Quân · 2A202601478<br>Vũ Đình Huy · 2A202601288<br>Đào Văn Đạt · 2A202601302 |
| Case đã chọn | **Case A — AI Tutor: Diagnostic Refresher** |

### Phân công phỏng vấn (Chặng 3)

| Interviewer | Mã người tham gia | Nhánh điều tra | Ngày giờ | Interview Record |
|---|---|---|---|---|
| Nguyễn Minh Quân | `2A202601478` | Bộ 1 — A vs B | 13:02 · 17/08 | [`P01.m4a`](Voice%20ghi%20âm/P01/P01.m4a) |
| Vũ Đình Huy | `2A202601200` | Bộ 2 — AI tutor có sẵn | 12h50 · 17/08 | [`P02.m4a`](Voice%20ghi%20âm/P02/P02.m4a) |
| Đào Văn Đạt | `2A202601901` | Bộ 3 — consequence | 13h15 · 17/08 | [`P03.m4a`](Voice%20ghi%20âm/P03/P03.m4a) |



### Solution directive nguyên văn (Case A)

> Thêm nút **"Tôi vẫn chưa hiểu"** vào bài học. Khi học viên bấm nút, AI Tutor sử dụng nội dung bài hiện tại, các câu trả lời gần đây và lịch sử học tập để: 1. Đặt 2–3 câu hỏi chẩn đoán ngắn. 2. Chọn một khái niệm nền để học viên ôn lại. 3. Tạo một phần giải thích ngắn. 4. Đưa học viên trở về bài đang học.

| Thành phần | Solution đã mô tả |
|---|---|
| Trigger | Học viên bấm "Tôi vẫn chưa hiểu" |
| Input | Bài hiện tại, câu trả lời gần đây và lịch sử học tập |
| AI action | Chẩn đoán và lựa chọn khái niệm nền |
| Output | Một phần ôn lại ngắn trước khi quay lại bài hiện tại |
| User control | Học viên chủ động yêu cầu trợ giúp |

---

## 2. Problem Hypothesis Brief — kết quả Chặng 1

Chuỗi đi theo: `Solution → Change → Actor → Situation & Job → Pain → Evidence`

### 2.0 Bối cảnh thật — desk research trước khi đặt giả thuyết

> Nguồn: đề bài hackathon Day 05–06 (`01-de-bai.md`) và `data/vlearn-pack/chatlog/DATA_DICTIONARY.md` — chatlog VLearn tutor × học viên **đã ẩn danh** do khoá cấp. Chỉ dùng số liệu tổng hợp; không trích nội dung hội thoại của bất kỳ học viên nào.

**Sự thật số 1 — VLearn đã có AI tutor rồi.** Theo mô tả chính thức của khoá, VLearn có AI tutor ngay trong trang học: học viên **bôi đen một đoạn tài liệu rồi hỏi**, tutor trả lời kèm trích dẫn `[trang N]`.

→ Vì vậy Case A **không phải là thêm một capability mới**. Nó đề xuất hai thứ khác: một **entry point chủ động** (bấm nút thay vì phải bôi đen) và một **bước chẩn đoán** trước khi giải thích. Nếu không nhận ra điều này, cả nhóm sẽ đi phỏng vấn với giả định sai rằng học viên đang tay không.

**Sự thật số 2 — hành vi hỏi thật, đo trên 1.261 lượt hỏi–đáp** (369 học viên, 585 hội thoại, 22–29/07/2026, 100% `in_class`):

| Quan sát | Số liệu | Đọc ra điều gì |
|---|---|---|
| Câu hỏi neo vào một đoạn bôi đen | **1.252 / 1.261 — 99,3%** | Học viên gần như **không bao giờ** gõ câu hỏi tự do. Họ **trỏ vào chỗ đang tắc**. |
| Chứa chữ "giải thích" | 463 (37%) | Ý định phổ biến nhất: *giải thích lại đoạn này* |
| Chứa "tóm tắt" / "là gì" | 125 (10%) / 114 (9%) | Vẫn là thao tác trên chính đoạn văn trước mắt |
| Chứa "không hiểu" / "chưa hiểu" | **9 (0,7%)** | Rất hiếm khi tự khai báo trạng thái không hiểu |
| Chứa "tại sao" | 16 (1,3%) | Rất hiếm khi truy nguyên nhân |

**Sự thật số 3 — tutor đáp lại thế nào:**

| Quan sát | Số liệu | Đọc ra điều gì |
|---|---|---|
| `move_used = review_concept` | 1.072 (85%) | Tutor chủ yếu **giải thích lại chính đoạn đó** |
| `move_used = validate_understanding` | **1 / 1.261** | Gần như không bao giờ kiểm tra xem học viên đã hiểu chưa |
| `asked_check_question = True` | **3 / 2.518** | Gần như không hỏi ngược để chẩn đoán |
| `misconceptions` | **0 / 1.261** | Field có sẵn trong schema nhưng **chưa từng được dùng** |
| `citations` rỗng | 46,2% | Gần một nửa câu trả lời không neo vào tài liệu |
| `rating` | down 37 > up 33 *(chỉ 2,8% có rating)* | Tín hiệu yếu, nhưng nghiêng tiêu cực |

**Vòng lặp đang xảy ra trên sản phẩm thật:**

```
Học viên tắc → bôi đen ĐOẠN ĐANG TẮC → "giải thích đoạn này"
             → tutor review_concept: giải thích lại CHÍNH ĐOẠN ĐÓ
             → nếu nguyên nhân nằm ở BÀI TRƯỚC thì vòng lặp không thoát ra được
```

> 📌 **Phạm vi và giới hạn của desk research:** Số liệu trên cho biết học viên **hỏi như thế nào**, không cho biết họ **trải nghiệm ra sao** hay **vì sao** họ hỏi như vậy. Nó chỉ dùng để làm sắc giả thuyết và chọn câu hỏi phỏng vấn — **không thay thế evidence từ interview**, và không được dùng để tuyên bố validated.

### 2.1 Solution — gỡ khỏi hình thức cụ thể

**Capability trung tính** (không nhắc nút, không nhắc AI, không nhắc màn hình):

> Khi học viên mắc kẹt ở giữa một bài học, hệ thống giúp họ **truy từ chỗ đang tắc về phần kiến thức nền còn thiếu**, lấp phần đó, rồi đưa họ quay lại đúng chỗ đang học dở.

*Ghi chú gỡ hình thức:* "nút", "AI Tutor", "2–3 câu hỏi chẩn đoán" đều là **cách triển khai đã chọn sẵn**, không phải capability. Nhóm không mặc định đây là cách duy nhất — xem Solution Parking Lot ở mục 2.7.

**Delta thật so với hiện trạng.** Vì VLearn đã có AI tutor tại chỗ (mục 2.0), directive không thêm capability "giải thích tại chỗ" — cái đó đã có. Nó thêm đúng hai thứ:

| | Hiện trạng trên VLearn | Directive đề xuất thêm |
|---|---|---|
| **Entry point** | Học viên phải **bôi đen một đoạn** rồi hỏi | Một nút chủ động, không cần chọn trước đoạn nào |
| **Nước đi sư phạm** | `review_concept` 85% — diễn giải lại chính đoạn đó | **Chẩn đoán trước**, rồi mới chọn khái niệm nền để ôn |

→ Trọng lượng của cả feature nằm ở ô dưới bên phải. Đó là chỗ phải kiểm tra, không phải "học viên có cần được giúp không".

### 2.2 Change — chuỗi thay đổi được kỳ vọng

```
Solution → hệ thống truy được từ chỗ tắc về phần nền còn thiếu
         → học viên biết PHẢI ÔN LẠI CÁI GÌ, không chỉ được nghe giải thích lại
         → họ lấp phần nền đó rồi quay lại đúng chỗ đang dở
         → Outcome: hoàn thành bài học thay vì bỏ qua đoạn khó và nợ kiến thức
```

Ba thay đổi được kỳ vọng — viết theo **delta so với hiện trạng**, không viết như thể đang bắt đầu từ số không:

1. Học viên thoát được **vòng lặp "giải thích lại cùng một đoạn"**, thay vì hỏi vài lượt rồi bỏ sang Google/Discord.
2. Học viên **nhận diện được khái niệm nền còn thiếu** — hiện tại chỉ 0,7% câu hỏi tự khai báo không hiểu và 1,3% hỏi "tại sao", nên gần như không ai đang tự truy nguyên nhân.
3. Học viên **quay lại đúng chỗ đang dở** sau khi ôn, thay vì mất mạch hoặc bỏ luôn đoạn đó.

**Hai mắt xích đang bị ngầm tin — đây là chỗ dễ sụp nhất:**

| Mắt xích | Nhóm đang tin | Nếu sai thì sao |
|---|---|---|
| **Chẩn đoán** | Học viên **không tự** xác định được phần nền còn thiếu | Nếu họ tự xác định được → bước chẩn đoán là công sức thừa → **Hypothesis B** |
| **Giá trị của việc biết** | Biết mình thiếu gì là **đủ** để họ đi lấp | Nếu biết mà vẫn không quay lại vì ngại mất công → chẩn đoán đúng vẫn không tạo ra outcome |

Mắt xích thứ hai chưa từng được nêu trong solution directive, nhưng nó đứng giữa "AI chẩn đoán xong" và "học viên thực sự học tiếp".

### 2.3 Actor — các nhóm người có liên quan

| Actor | Họ đang làm gì | Pain hoặc hậu quả có thể có | Họ hưởng lợi thế nào |
|---|---|---|---|
| **Học viên đang đọc tài liệu bài trong khoá** *(chọn)* | Đọc tài liệu trên VLearn, thường là **đọc trước hoặc ôn ngoài giờ lab** | Tắc ở một đoạn; bôi đen hỏi tutor nhưng chỉ được diễn giải lại; không biết phải quay lại phần nào | Thoát được chỗ tắc và học tiếp, không nợ kiến thức sang bài sau |
| Học viên đang làm lab / chạy checkpoint | Làm bài trong giờ lab, có deadline checkpoint | Tắc giữa giờ, áp lực thời gian; dễ copy code mẫu cho qua | Qua checkpoint mà **hiểu** vì sao |
| Học viên đã bỏ dở một bài | Không quay lại phần đã bỏ | Nợ kiến thức dồn sang các bài sau | Có đường quay lại rõ ràng |
| Lab Coach / TA | Hỗ trợ trong giờ lab; trả lời trong Discord | Cùng một câu hỏi lặp lại; không thấy được cả lớp vướng ở đâu | Giảm câu hỏi lặp, thấy điểm vướng chung |
| Người biên soạn nội dung | Viết và sửa tài liệu bài | Không biết đoạn nào gây vướng | Có tín hiệu để sửa nội dung |

**Actor nhóm chọn để điều tra trước:** Học viên trong khoá, trong 7 ngày gần đây đã có lần đang đọc tài liệu một bài trên VLearn và gặp một đoạn không hiểu.

**Vì sao chọn nhánh này thay vì actor khác:**

- Đây là actor **trực tiếp trải nghiệm pain** và cũng là actor **phải thay đổi hành vi** thì outcome mới xảy ra. Lab Coach/TA chỉ chịu hậu quả gián tiếp; người biên soạn không có mặt tại thời điểm pain xảy ra.
- Chatlog cho thấy 100% hội thoại ở chế độ `in_class`, nhưng **thời điểm tắc nặng nhất có thể nằm ngoài giờ lab** — khi không có Lab Coach và Discord không ai trả lời ngay. Đây là khoảng trống cần interview mới biết, desk research không trả lời được.
- **Thuận lợi tuyển người:** cả lớp đều là người dùng thật của VLearn, nên tuyển đúng tiêu chí là khả thi ngay trong giờ nghỉ. Nhưng phải phỏng vấn **người ngoài nhóm** theo luật của lab.

> 💡 **Kỷ luật khi phỏng vấn actor gần gũi:** Tránh trượt thành trò chuyện đồng cảm (*"ừ tao cũng thế"*); người phỏng vấn phải luôn giữ kỷ luật đào sâu sự kiện quá khứ cụ thể thay vì chia sẻ trải nghiệm cá nhân.

### 2.4 Situation & Job

**Mô tả Situation & Job:**

> Khi **đang đọc tài liệu một bài trên VLearn và gặp một đoạn không hiểu**, **học viên trong khoá** đang cố **học tiếp cho kịp lab hoặc deadline** bằng cách **bôi đen đoạn đó hỏi tutor, đọc lại nhiều lần, tra Google/ChatGPT, hỏi trong Discord, hoặc bỏ qua và copy ví dụ mẫu**.

*Chuỗi workaround thật, theo thứ tự thường xảy ra:*

```
bôi đen + "giải thích đoạn này"  →  hỏi lại lượt 2, 3  →  Google / ChatGPT
   →  Discord lớp (tối muộn thường không ai rep)  →  hỏi bạn / Lab Coach hôm sau
   →  bỏ qua, copy ví dụ mẫu cho qua checkpoint
```

**JTBD Hypothesis — bản trung tính** *(không nghiêng sẵn về giả thuyết nào)*:

> Khi **tôi đang đọc bài và gặp một đoạn không hiểu**, tôi muốn **gỡ được chỗ tắc đó với công sức chấp nhận được**, để có thể **học tiếp bài đang dở mà không nợ lại phần này**.

*Ba biến thể ứng với ba giả thuyết ở mục 2.5 — buổi phỏng vấn sẽ cho biết biến thể nào đúng:*

| | "tôi muốn…" | Nếu đúng thì solution phải làm gì |
|---|---|---|
| **A** | biết **mình đang thiếu khái niệm nền nào** và lấp được nó | Chẩn đoán trước, rồi mới giải thích |
| **B** | lấp phần nền **mà không phải rời khỏi bài đang đọc** | Đưa nội dung nền tới tận nơi; không cần chẩn đoán |
| **C** | được **giải thích theo một cách khác** thay vì diễn giải lại cùng đoạn | Đổi nước đi sư phạm của tutor, không cần thêm nút |

*Kiểm tra:* Job trung tính vẫn tồn tại nếu bỏ hoàn toàn AI, tutor và nút "Tôi vẫn chưa hiểu" khỏi bối cảnh — học viên vẫn cần gỡ chỗ tắc để học tiếp. ✅

### 2.5 Pain — ba cách giải thích cạnh tranh

**Pain Hypothesis A — Vấn đề nằm ở chẩn đoán:**

> Khi **đang đọc bài và gặp một đoạn không hiểu**, **học viên** gặp khó khăn trong việc **học tiếp** vì **họ không xác định được mình đang thiếu khái niệm nền nào**, dẫn đến **chỉ trỏ được vào chỗ đang tắc, tra cứu bằng chính từ khoá trong bài, và cuối cùng bỏ qua đoạn đó**.

**Pain Hypothesis B — Vấn đề nằm ở chi phí quay lại:**

> Khi **đang đọc bài và gặp một đoạn không hiểu**, **học viên** gặp khó khăn trong việc **học tiếp** vì **quay lại học phần nền cho tử tế tốn thêm cả buổi trong khi lab/deadline đã sát**, dẫn đến **họ chọn bỏ qua và copy ví dụ mẫu, chấp nhận hiểu lỏng lẻo**.

**Pain Hypothesis C — Công cụ tại chỗ đã có nhưng không đưa họ đi đâu** *(xuất hiện từ desk research ở mục 2.0)*:

> Khi **đang học giữa bài và gặp một đoạn không hiểu**, **học viên** gặp khó khăn trong việc **học tiếp** vì **AI tutor có sẵn chỉ diễn giải lại chính đoạn họ bôi đen chứ không truy về phần nền còn thiếu**, dẫn đến **họ hỏi vài lượt không thoát, rồi bỏ sang Google/Discord hoặc bỏ qua luôn**.

**Khác biệt then chốt giữa ba giả thuyết:**

| | **A — chẩn đoán** | **B — chi phí quay lại** | **C — nước đi sư phạm** |
|---|---|---|---|
| Học viên có biết mình thiếu gì không? | **Không** | **Có** | Không, và tutor cũng không giúp họ biết |
| Cái chặn thật là gì | Không định vị được nguyên nhân | Định vị được nhưng không đủ thời gian đi lấp | Được trả lời nhưng cùng một kiểu, không mở ra hướng mới |
| Solution phải làm gì | Chẩn đoán trước rồi mới giải thích | Đưa nội dung nền tới tận nơi, rút ngắn đường quay lại | Đổi cách tutor trả lời; không cần nút mới |
| Bước "AI đặt 2–3 câu hỏi chẩn đoán" | **Là phần giá trị nhất** | Là công sức thừa, gây phiền | Có thể không cần — chỉ cần đổi move |
| Desk research ở mục 2.0 nói gì | Ủng hộ: 99,3% chỉ trỏ vào đoạn, 0,7% tự khai báo không hiểu | Không nói được gì — chatlog không đo chi phí quay lại | Ủng hộ: `review_concept` 85%, `validate_understanding` 1/1.261 |

**Giả thuyết nhóm chọn để điều tra trước: A**

**Lý do chọn:**

1. Solution directive đặt **toàn bộ trọng lượng** lên bước "AI chẩn đoán khái niệm nền" (mục 2.1). Nếu A sai thì phần đắt nhất của feature là thừa.
2. A là **giả định dễ sai nhất**: nghe rất hợp lý, và desk research có vẻ ủng hộ — đúng kiểu giả định không ai buồn kiểm tra.
3. A và C **đo được bằng cùng một buổi phỏng vấn** (hỏi họ đã hỏi tutor thế nào), nên chọn A không làm mất cơ hội kiểm C.

> 📌 **Góc nhìn phân tích (A và B có thể cùng đúng, nối tiếp nhau):** Không chẩn đoán được là rào cản thứ nhất; kể cả chẩn đoán xong, chi phí quay lại vẫn là rào cản thứ hai. Nếu phỏng vấn cho ra cả hai, **đừng ép chọn một** — ghi nhận đầy đủ cả chuỗi thực tế.

### 2.6 Evidence — điều cần tìm trước khi viết câu hỏi

| Cần kiểm tra | Evidence làm nhóm tin hơn | Evidence làm nhóm nghi ngờ hoặc bác bỏ |
|---|---|---|
| **Situation có thật** | Kể được một lần cụ thể trong 7 ngày gần đây: tên bài, đoạn nào, đang làm gì, ở đâu | Không nhớ nổi lần nào; chỉ nói "thỉnh thoảng cũng có" |
| **Pain có ý nghĩa** | Dừng lại đáng kể ở đoạn đó, kể được cảm giác và điều xảy ra sau đó, có quay lại chỗ đó | Nói "cũng bình thường thôi", lướt qua rồi quên luôn |
| **Workaround tồn tại** | Kể được chuỗi cụ thể (hỏi tutor mấy lượt, tra Google, nhắn Discord, hỏi bạn) và ước lượng được công sức | Không làm gì cả, bỏ qua và không nghĩ tới nữa |
| **Consequence tồn tại** | Bỏ dở bài, sai checkpoint, copy code mẫu không hiểu, **nợ dồn sang bài sau**, trễ deadline | Vẫn theo kịp bình thường, kết quả không đổi, không nhớ hậu quả nào |
| **Pattern có lặp** | Xảy ra ở nhiều bài khác nhau; kể được cả lần gần nhất trước đó | Chỉ đúng một lần duy nhất, do bài đó đặc biệt khó |
| **Chẩn đoán (A)** | Hỏi "lúc đó bạn có nói được mình thiếu gì không" → mô tả mơ hồ; **từ khoá tra cứu là tên khái niệm trong bài** | Nêu chính xác khái niệm nền còn thiếu **ngay tại chỗ** → nghiêng **B** |
| **Chi phí quay lại (B)** | Biết phải quay lại phần nào nhưng không làm vì tốn thời gian / sát deadline | Quay lại dễ dàng, không thấy tốn kém |
| **Nước đi của tutor (C)** | Bôi đen chỗ tắc, gõ "giải thích…", tutor diễn giải lại cùng đoạn, hỏi thêm lượt vẫn thế rồi bỏ | Tutor giải thích một lượt là thông → pain đã được giải quyết |
| **Thời điểm tắc** | Tắc nặng nhất **ngoài giờ lab**, lúc không có Lab Coach và Discord không ai rep | Chỉ tắc trong giờ lab, nơi đã có kênh hỗ trợ hiệu quả |

### 2.7 Chốt Problem Hypothesis và park solution

**Problem Hypothesis nhóm mang sang Chặng 2:**

> Học viên tự học online, khi đang học giữa một bài mới và gặp một đoạn không hiểu, **không xác định được mình đang thiếu khái niệm nền nào**, nên phải đọc lại nhiều lần hoặc rời khỏi bài đi tra nguồn ngoài; kết quả là họ mất mạch, hiểu lỏng lẻo và thường bỏ qua đoạn đó.

**Điều gì phải đúng để giả thuyết đứng vững:**

1. Việc mắc kẹt xảy ra **thật và gần đây**, kể lại được thành một sự kiện cụ thể chứ không phải mô tả chung.
2. Học viên **thực sự không tự chỉ ra được** khái niệm nền còn thiếu tại thời điểm đó.
3. Có **hậu quả quan sát được** (bỏ dở, sai quiz, phải học lại), không chỉ là khó chịu thoáng qua.
4. Workaround hiện tại **đủ tốn kém** để họ muốn một cách khác.

**Điều gì có thể khiến nhóm sửa hoặc bác bỏ giả thuyết:**

- Học viên nói họ biết chính xác mình thiếu gì và chỉ mất vài phút tra là xong → pain nằm ở chi phí chuyển ngữ cảnh, **sửa sang Hypothesis B**.
- Học viên bỏ qua đoạn khó và vẫn hoàn thành bài bình thường, không hậu quả → **pain không đủ ý nghĩa, bác bỏ**.
- Việc mắc kẹt hầu như chỉ xảy ra ở bài tập/quiz chứ không ở phần đọc–xem → **sửa Situation**.
- Người mắc kẹt thật đã bỏ khóa học từ lâu, không còn học nữa → **sửa Actor**.

**Solution Parking Lot** *(brainstorm ≥5 hướng, có ít nhất một hướng không dùng AI)*

| # | Hướng giải quyết có thể có | AI / Không dùng AI |
|---|---|---|
| 1 | Nút "Tôi vẫn chưa hiểu" + AI chẩn đoán khái niệm nền *(directive gốc)* | AI |
| 2 | Người biên soạn gắn sẵn "kiến thức nền cần có" ở đầu mỗi đoạn khó | Không dùng AI |
| 3 | Prerequisite check 3 câu trước khi vào bài, sai thì gợi bài nền | Không dùng AI |
| 4 | Nút "đánh dấu chỗ chưa hiểu" gom thành danh sách gửi giảng viên trả lời buổi sau | Không dùng AI |
| 5 | Chú giải thuật ngữ nội tuyến: hover là hiện định nghĩa + link tới bài nền | Không dùng AI |
| 6 | Hiển thị "nhiều học viên cũng dừng ở đoạn này" + link bài nền mà họ đã quay lại | Không dùng AI *(thống kê)* |
| 7 | AI Chat trả lời tự do tại chỗ, **không** có bước chẩn đoán | AI |

### 3.1 Big 3 — ba điều quan trọng nhất cần học

| # | Điều cần học | Evidence cần tìm | Điều gì khiến nhóm xem lại giả thuyết |
|---|---|---|---|
| 1 | Việc mắc kẹt có thật và gần đây không — lúc đó chuyện gì thực sự xảy ra? | Một sự kiện cụ thể: tên bài, thời điểm, hành vi ngay sau đó | Không kể được lần nào cụ thể, chỉ nói chung chung |
| 2 | **Lúc mắc kẹt, họ có tự chỉ ra được mình thiếu gì không?** *(câu "đáng sợ")* | Cách họ mô tả chỗ vướng — có nêu được khái niệm nền hay chỉ nói "khó quá" | Họ nêu chính xác và ngay lập tức → giả thuyết nghiêng sang **B** |
| 3 | Họ đã làm gì và trả giá bao nhiêu? | Workaround cụ thể, công sức bỏ ra, hậu quả sau đó | Không làm gì và không hậu quả gì → pain không đủ ý nghĩa |

### 3.5 Big 3 Questions

| # | Điều cần học | Câu hỏi sẽ dùng |
|---|---|---|
| 1 | Situation có thật | "Lần gần nhất đó là khi nào, bạn đang ở đâu và đang làm gì? Kể lại giúp mình từ lúc bạn nhận ra mình không hiểu." |
| 2 | Chẩn đoán hay gián đoạn *(A vs B)* | "Lúc dừng lại ở đoạn đó, trong đầu bạn nghĩ gì? Bạn có nói ra được là mình đang thiếu cái gì không, hay chỉ thấy đoạn đó khó?" |
| **2b** | **Chẩn đoán thật hay khôn-sau** 🆕 | **"Bạn biết điều đó *ngay lúc đó*, hay sau này nghĩ lại mới biết?"** |
| **2c** | **Công cụ tại chỗ *(kiểm C)*** 🆕 | **"Lúc đó bạn có bôi đen đoạn đó hỏi tutor không? Bạn gõ chính xác câu gì? Sau câu trả lời đó bạn làm gì?"** |
| 3 | Workaround và hậu quả | "Sau đó bạn làm gì? Kể mình nghe từng bước — mất khoảng bao lâu, và cuối cùng bài đó bạn có học xong không?" |

> 🔧 **Vì sao thêm 2b và 2c.** Cả ba lượt phỏng vấn ngày 17/08 đều **không hỏi hai câu này**. Hậu quả cụ thể:
>
> - Thiếu **2b** → khi người trả lời nêu được phần nền còn thiếu, không phân biệt được họ biết *tại thời điểm mắc kẹt* hay chỉ *biết khi kể lại*. Đây đúng là chỗ quyết định A hay B.
> - Thiếu **2c** → **Hypothesis C không được kiểm buổi nào**, dù VLearn đã có sẵn AI tutor và đó là workaround đầu tiên trong tầm tay của học viên.

### 3.6 Probe bank — chỉ dùng khi cần đào sâu câu chuyện

- "Lúc đó chuyện gì xảy ra tiếp theo?"
- "Bạn đã làm gì?"
- "Vì sao bạn chọn cách đó?"
- "Phần nào khó nhất?"
- "Bạn đã thử cách nào khác chưa?"
- "Việc đó kéo theo hậu quả gì?"
- "Lần gần nhất trước đó là khi nào?"

### 3.7 Ba phản xạ khi data bắt đầu lệch

| User đưa ra | Phản xạ | Câu quay lại evidence |
|---|---|---|
| Lời khen — "app này hay đấy", "ý tưởng này ổn mà" | **Deflect** | "Cảm ơn bạn. Quay lại hôm đó — sau khi bạn dừng ở đoạn không hiểu thì bạn làm gì tiếp?" |
| Câu chung chung hoặc lời hứa tương lai — "thường thì mình sẽ Google", "nếu có cái đó chắc mình dùng" | **Anchor** | "Lần gần nhất chuyện đó xảy ra là khi nào? Kể mình nghe cụ thể lần đó." |
| Ý tưởng hoặc feature request — "giá mà có nút giải thích tại chỗ" | **Dig** | "Điều đó giúp bạn làm được gì? Hiện tại bạn đang xử lý ra sao?" |

### 3.8 Tự rà soát trước khi phỏng vấn

- [x] Không câu nào làm lộ solution — guide không nhắc nút "Tôi vẫn chưa hiểu", không nhắc AI Tutor.
- [x] Không hỏi ý kiến hoặc dự đoán tương lai — không có "bạn có muốn…", "bạn có dùng không".
- [x] Story opener đã neo vào "lần gần nhất".
- [x] Ba câu hỏi chính nối trực tiếp với ba điều cần học ở Big 3.
- [x] Có ít nhất một câu có thể làm giả thuyết yếu đi — câu #2 có thể lật A sang B.
- [x] Các Interview Record được dùng làm evidence (P01, P02) đều mô tả một sự kiện trong 7 ngày gần đây.
- [x] Đã biết mình sẽ phỏng vấn ai — phân công ở [mục 1](#1-thông-tin-cá-nhân-và-nhóm).
- [x]  Có câu chốt bắt buộc khi recruitment check ra câu chung chung.
- [x]  Có câu tách chẩn đoán-thật khỏi khôn-sau (2b).
- [x]  Có câu kiểm công cụ tại chỗ (2c).


### 3.9 Đã sửa gì sau khi luyện — changelog

| # | Quan sát được từ ba lượt phỏng vấn 17/08 | Đã sửa thành |
|---|---|---|
| 1 | Recruitment check ra câu chung chung *("trước thì khá là thường xuyên…")*, không ra sự kiện | Thêm **câu chốt bắt buộc** ở 3.2: chưa có tên bài + mốc thời gian thì chưa đi tiếp |
| 2 | Không lượt nào hỏi "biết ngay lúc đó hay nghĩ lại mới biết" | Thêm **câu 2b** vào Big 3 Questions — nâng từ probe tuỳ chọn lên câu bắt buộc |
| 3 | Không lượt nào hỏi về AI tutor có sẵn → C không được kiểm | Thêm **câu 2c** vào Big 3 Questions |
| 4 | Story opener thực tế bị hỏi thành câu kép và không neo "lần gần nhất" *("bạn gặp khó khăn gì, xảy ra khi nào?")* | Giữ nguyên bản trong 3.4 — **tách làm một câu, neo "lần gần nhất"**, và không hỏi hai ý cùng lúc |
| 5 | Không lượt nào đo độ lớn (dừng bao lâu, mất bao lâu) | Đưa *"mất khoảng bao lâu"* thành phần bắt buộc của câu 3, không để trong probe bank |
| 6 | Buổi thực tế chỉ ~3 phút, lời mở đầu hứa "khoảng 3 phút" trong khi guide thiết kế cho 15 phút | Thống nhất: **hứa đúng thời lượng định làm**. Nếu chỉ có 3–5 phút thì bỏ Block 4 (pattern) và giữ trọn Block 2–3 |

---

## 4. Practice Reflection — Chặng 4

### 4.1 Câu hỏi nào đã giúp user kể một tình huống cụ thể?

Câu **"Kể về lần bạn thắc mắc khi đang học?"** (lượt Huy–P02) đã kéo ra được một sự kiện thật: *hôm qua, bài "phân tích hướng đi", không hiểu context các ví dụ của cô*.

Ở lượt P01, chuỗi câu hỏi follow-up **"Trước lúc gặp đoạn đó, bạn đã đọc tới đâu rồi?"** và **"Bạn có tra cứu gì không? Bạn gõ chính xác chữ gì?"** cho evidence rõ hơn: tối trước buổi lab, P01 tắc ở RRF, tra *"RRF reranking là gì"*, rồi hôm sau dựa vào code mẫu nhưng không giải thích được lý do chọn top-k.

Điều đáng chú ý là **câu recruitment check trước đó không làm được việc này**. Khi được hỏi "trong một tuần gần đây có lúc nào không hiểu không", P02 trả lời bằng một mô tả thói quen — *"trước thì khá là thường xuyên, kiểu nhiều khi trong lớp mình không được để ý cho lắm"*. Chỉ đến khi được yêu cầu **kể một lần**, câu chuyện cụ thể mới xuất hiện.

Bài học: câu hỏi có/không dùng để **tuyển người**; câu mệnh lệnh "kể lại" mới dùng để **lấy evidence**. Hai việc khác nhau, không thay thế nhau được.

### 4.2 Chỗ nào mình cần làm tốt hơn ở lần phỏng vấn thật?

**Bốn điểm quan sát được từ chính bản script:**

1. **Dừng quá sớm ở câu trả lời đầu tiên.** P02 nói *"chưa đọc qua mấy cái sách mà cô gợi ý bao giờ"*. Nhưng không ai hỏi tiếp *"bạn biết điều đó ngay lúc đó, hay nghĩ lại mới biết?"*, nên đây chỉ là tín hiệu nghiêng về B, chưa đủ để kết luận A hay B.
2. **Không kiểm công cụ tại chỗ.** Không lượt nào hỏi về AI tutor trên VLearn, dù đó là workaround gần tay nhất. Hypothesis C ra khỏi buổi phỏng vấn mà không được chạm tới.
3. **Không đo độ lớn.** Không lượt nào hỏi "dừng ở đó bao lâu" hay "mất bao lâu". Không có con số thì không biết pain nặng hay nhẹ.
4. **Không truy hậu quả.** P02 nói *"về nhà đọc lại từ đầu thì sẽ nhanh hơn"* — đây là **dự định**, không phải việc đã xảy ra. Cần hỏi *"tối qua bạn có mở ra đọc thật không?"*.

Các điểm trên được rút từ transcript văn bản; nhóm không bổ sung nhận xét về giọng nói, khoảng lặng hoặc tỷ lệ thời lượng vì phần đó cần nghe lại bản ghi và không nằm trong phạm vi README này.

### 4.3 Sau khi luyện, nhóm đã sửa Conversation Guide ở đâu và vì sao?

Sáu thay đổi, ghi chi tiết ở [mục 3.9](#39-đã-sửa-gì-sau-khi-luyện--changelog). Ba thay đổi quan trọng nhất:

| Sửa gì | Vì sao |
|---|---|
| Thêm **câu chốt bắt buộc** sau recruitment check | Câu có/không để nguyên sẽ ra mô tả thói quen, không ra sự kiện |
| Nâng **"ngay lúc đó hay nghĩ lại mới biết"** thành câu bắt buộc | Đây là câu duy nhất phân định được A với B, mà cả ba lượt đều bỏ sót |
| Thêm **câu về AI tutor có sẵn** | Không hỏi thì mặc định sai rằng học viên đang tay không, trong khi VLearn đã có tutor |

**Điều quan trọng nhất buổi luyện mang lại là dữ liệu không đồng nhất:** P01 nghiêng về A, trong khi P02 cho thấy người học **biết rõ mình thiếu gì** và cái chặn họ là **chi phí gián đoạn** — cơ chế của B. Hai lượt ngắn chưa đủ để kết luận giả thuyết nào phổ biến hơn, nhưng đủ để nhóm không mặc định A là đúng.

## 5. AI Support Log

*Khai báo theo yêu cầu của lab: "Mọi cách dùng AI phải được khai báo trong README của repo."*

**Công cụ đã dùng:** Claude (Claude Code), ngày 17/08/2026.

| # | AI đã giúp gì | Trạng thái |
|---|---|---|
| 1 | Đọc và tóm tắt 6 trang tài liệu lab (Đề bài, Ba case, Chặng 1–4) để xác định đúng yêu cầu của "Repo cá nhân cần nộp" | Hỗ trợ đọc hiểu |
| 2 | Dựng cấu trúc repo và khung 5 phần của README theo đúng đặc tả Chặng 4 | Hỗ trợ định dạng |
| 3 | **Soạn bản nháp Chặng 1** (capability trung tính, chuỗi Change, bảng Actor, Situation & Job, JTBD, hai Pain Hypothesis A/B, bảng Evidence, Solution Parking Lot) | ✅ **Đã hoàn thiện** — Nhóm đã tự rà soát, tinh chỉnh và chuẩn hoá toàn bộ theo lập luận thực tế của nhóm |
| 4 | **Soạn bản nháp Conversation Guide** (Big 3, lời mở đầu, story opener, 3 câu hỏi chính, ba phản xạ) và rà soát xem câu hỏi có làm lộ solution / có hỏi ý kiến hay dự đoán tương lai không | ✅ **Đã hoàn thiện** — Nhóm đã chốt lại sau Chặng 2 và cập nhật phiên bản cải tiến ở Chặng 3 |
| 5 | Soạn `interview/interview-script.md` — kịch bản cầm tay 15 phút chia theo block thời gian, danh sách câu không được hỏi, và checklist tự kiểm sau phỏng vấn | ✅ **Đã hoàn thiện** — Kịch bản cầm tay 15 phút, danh sách câu không được hỏi và checklist tự kiểm hoàn chỉnh |
| 6 | Soạn `practice/rehearsal-roleplay.md` — hội thoại mẫu để đóng vai tập phản xạ Deflect/Anchor/Dig | Đã dùng để đóng vai diễn tập nội bộ về phản xạ Deflect / Anchor / Dig trước khi phỏng vấn thật |
| 7 | Quét `DAY 01` → `DAY 17` lấy bối cảnh thật: chương trình học, đề bài hackathon Day 05–06, và **thống kê tổng hợp** từ `DATA_DICTIONARY.md` của chatlog VLearn đã ẩn danh → viết mục 2.0 và bổ sung Pain Hypothesis C | Hỗ trợ desk research. **Chỉ dùng số liệu tổng hợp, không trích nội dung hội thoại của học viên nào.** |
| 8 | Soạn `practice/3-bo-cau-hoi-va-kich-ban.md` — ba bộ câu hỏi phân công cho ba thành viên + ba kịch bản luyện tập (P01/P02/P03) | Ba bộ câu hỏi thực tế được phân công cho 3 thành viên; dữ liệu phỏng vấn thật được bóc tách riêng vào các file `notes_*.md` |
| 9 | Soạn bộ câu hỏi cho `Voice ghi âm/P03/script.md` (nhánh Bộ 3) | Chỉ soạn **câu hỏi**. Phần trả lời để trống — phải bóc từ bản ghi, không được suy đoán. |
| 10 | Tạo `interview/notes_quan.md`, `notes_dat.md`, `notes_huy.md` — khung Interview Record | `notes_quan.md` và `notes_huy.md` được điền từ **script/transcript thật** của P01 và P02; `notes_dat.md` để trống vì không có transcript văn bản. |
| 11 | Đọc transcript thật của lượt P02 và rút ra nhận định A/B/C | Diễn giải do AI đề xuất, **đặt tách khỏi phần Facts**; nhóm phải tự nghe lại và xác nhận. |
| 12 | Đối chiếu script lượt P01 với kịch bản hư cấu ở dòng 8 và cảnh báo trùng lặp | Chủ repo đã xác nhận đây là script phỏng vấn thật. |
| 13 | Đối chiếu hai script có câu trả lời thật (P01, P02) với Conversation Guide dự kiến → rút ra chênh lệch, viết lại mục 3 và changelog 3.9 | Dựa trên **văn bản có thật**, không suy đoán. |
| 14 | Soạn mục 4.1–4.3 (Practice Reflection) từ những chênh lệch quan sát được trong script | Dựa trên facts có trong P01/P02; không thêm nhận xét chỉ có thể biết khi nghe lại bản ghi. |
| 15 | Viết lại `interview/notes.md` thành mục lục ba Interview Record | Giữ đúng tên file lab yêu cầu để người chấm tìm được. |
| 16 | Điền `notes_quan.md` từ script lượt P01 do chủ repo cung cấp; rút nhận định A/B và đối chiếu với lượt P02 | Facts chép nguyên văn; diễn giải đặt tách riêng. |
| 17 | Rà soát toàn repo tìm chỗ rò tên người được phỏng vấn → đổi tên thư mục và file âm thanh sang `P01`/`P02`/`P03` | Thực hiện quy định ẩn danh người tham gia. |

**AI KHÔNG được dùng cho:**

- ❌ Tạo interview data hoặc bịa quote — `interview/notes.md` là khung trống, mọi nội dung phải do chính người phỏng vấn ghi lại.
- ❌ Suy diễn chi tiết user chưa nói.
- ❌ Bổ sung dữ liệu từ bản ghi âm không có transcript văn bản.

**Điểm nào hời hợt / sai và mình đã tự sửa thế nào:**

AI đã hỗ trợ khung phân tích và diễn đạt; nhóm giữ dữ liệu phỏng vấn tách riêng ở `notes_quan.md` và `notes_huy.md`, chỉ ghi những gì người tham gia thực sự nói. Sau buổi luyện, Conversation Guide được sửa để neo vào một sự kiện gần nhất, tách câu hỏi chẩn đoán khỏi nhận thức muộn, hỏi về AI tutor hiện có, và đo thời gian/hậu quả. Các thay đổi được ghi ở mục 3.9.

---

## Kiểm tra trước khi nộp

- [x] Repo đúng cấu trúc và định dạng theo quy định lab (`README.md`, `interview/notes.md`, `interview/recording.mp4a`)
- [x] `README.md` đủ năm phần theo chuẩn Chặng 4
- [x] `interview/notes.md` trỏ tới notes của chính lượt chủ repo làm interviewer: [`notes.md`](interview/notes.md)
- [x] Bản ghi âm đầy đủ trong thư mục [`Voice ghi âm/`](Voice%20ghi%20âm/)
- [x] Người được phỏng vấn (P01, P02) đã đồng ý cho ghi âm trước khi bắt đầu
- [x] Conversation Guide không làm lộ solution
- [x] Conversation Guide đã được sửa sau khi luyện (xem mục 3.9)

## Bốn gate đánh giá — tự chấm

| Gate | Trạng thái | Ghi chú |
|---|---|---|
| 1. Problem Framing | ✅ Đạt | Đi đủ chuỗi Solution → Evidence; giả thuyết cụ thể và có thể bị bác bỏ  |
| 2. Interview Design | ✅ Đạt | Big 3 nối với điều cần học; câu hỏi hỏi quá khứ |
| 3. Interview Practice | ✅ Đạt | Có Interview Record hoàn chỉnh của lượt chủ repo |
| 4. Reflection & Revision | ✅ Đạt | Có phản tư cụ thể và changelog Conversation Guide sau luyện|
