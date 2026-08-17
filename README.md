# K4-Track1-DAY17-2A202601478-NguyenMinhQuan

Day 17 · Track 1 — Product Discovery: Finding and Validating Pain
Lab: Reverse solution directive → problem hypothesis → problem interview theo The Mom Test

> **Trạng thái nộp bài:** Chặng 1 và Chặng 2 đã hoàn thành. Chặng 3 (phỏng vấn thật) và Chặng 4 (Practice Reflection) **chưa thực hiện** — các mục có dấu `⬜ CẦN ĐIỀN SAU KHI PHỎNG VẤN` phải được điền bằng dữ liệu thật trước khi nộp. Xem [AI Support Log](#5-ai-support-log).

---

## 1. Thông tin cá nhân và nhóm

| Mục | Nội dung |
|---|---|
| MHV | 2A202601478 |
| Họ và tên | Nguyễn Minh Quân |
| Track / Ngày | Track 1 · Day 17 |
| Tên nhóm | ⬜ *điền tên nhóm* |
| Thành viên | ⬜ *điền 3 thành viên (họ tên · MHV)* |
| Case đã chọn | **Case A — AI Tutor: Diagnostic Refresher** |

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

> ⚠️ **Giới hạn của desk research.** Số liệu trên cho biết học viên **hỏi như thế nào**, không cho biết họ **trải nghiệm ra sao** hay **vì sao** họ hỏi như vậy. Nó chỉ dùng để làm sắc giả thuyết và chọn câu hỏi phỏng vấn — **không thay thế evidence từ interview**, và không được dùng để tuyên bố validated.

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

> ⚠️ **Rủi ro của việc actor ở ngay cạnh mình:** dễ trượt thành trò chuyện đồng cảm (*"ừ tao cũng thế"*) thay vì moi ra sự kiện. Người phỏng vấn phải giữ kỷ luật hỏi quá khứ cụ thể, không gật gù chia sẻ trải nghiệm của chính mình.

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

> ⚠️ **A và B có thể cùng đúng, nối tiếp nhau:** không chẩn đoán được là rào cản thứ nhất; kể cả chẩn đoán xong, chi phí quay lại vẫn là rào cản thứ hai. Nếu phỏng vấn cho ra cả hai, **đừng ép chọn một** — ghi lại cả chuỗi.

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

> ✅ **CHECKPOINT 1 — Problem Hypothesis**
> Đã đi đủ chuỗi Solution → Change → Actor → Situation & Job → Pain → Evidence; có hai cách giải thích cạnh tranh (A/B) và nói rõ điều gì có thể làm giả thuyết được chọn trở nên sai.

---

## 3. Conversation Guide — phiên bản cuối

> ⚠️ Đây là **phiên bản trước khi phỏng vấn**. Sau Chặng 3 phải sửa lại guide này dựa trên trải nghiệm luyện tập và ghi rõ đã sửa gì ở mục [4.3](#43-sau-khi-luyện-nhóm-đã-sửa-conversation-guide-ở-đâu-và-vì-sao).
>
> 📄 Bản cầm tay để dùng lúc phỏng vấn: [`interview/interview-script.md`](interview/interview-script.md) — cùng nội dung nhưng chia theo block thời gian, kèm danh sách câu không được hỏi và checklist tự kiểm.

### 3.1 Big 3 — ba điều quan trọng nhất cần học

| # | Điều cần học | Evidence cần tìm | Điều gì khiến nhóm xem lại giả thuyết |
|---|---|---|---|
| 1 | Việc mắc kẹt có thật và gần đây không — lúc đó chuyện gì thực sự xảy ra? | Một sự kiện cụ thể: tên bài, thời điểm, hành vi ngay sau đó | Không kể được lần nào cụ thể, chỉ nói chung chung |
| 2 | **Lúc mắc kẹt, họ có tự chỉ ra được mình thiếu gì không?** *(câu "đáng sợ")* | Cách họ mô tả chỗ vướng — có nêu được khái niệm nền hay chỉ nói "khó quá" | Họ nêu chính xác và ngay lập tức → giả thuyết nghiêng sang **B** |
| 3 | Họ đã làm gì và trả giá bao nhiêu? | Workaround cụ thể, công sức bỏ ra, hậu quả sau đó | Không làm gì và không hậu quả gì → pain không đủ ý nghĩa |

*Điều "đáng sợ" là #2:* câu trả lời có thể lật giả thuyết A sang B và làm mất phần đắt nhất của solution directive.

### 3.2 Tiêu chí tuyển người

> Chúng tôi cần nói chuyện với người đã **học một bài học online và gặp một đoạn không hiểu** trong vòng **7** ngày gần đây.

**Recruitment check** *(chỉ để tuyển đúng người, không tính là evidence chính)*:

> "Trong 7 ngày gần đây, có lần nào bạn đang học một bài mà gặp một đoạn không hiểu không? Lần gần nhất là bài gì?"

### 3.3 Lời mở đầu

> "Cảm ơn bạn dành thời gian. Mình đang tìm hiểu cách mọi người tự học online — cụ thể là những lúc đang học mà bị vướng. Mình muốn nghe **chuyện đã xảy ra thật** của bạn, chứ không hỏi ý kiến hay xin feedback về bất cứ thứ gì. Không có câu trả lời đúng hay sai, và bạn không cần chuẩn bị gì cả. Mình sẽ hỏi khoảng 15 phút.
> Bạn cho phép mình **ghi âm** để nghe lại cho khỏi sót không? Bản ghi chỉ mình và nhóm mình dùng để học, không chia sẻ công khai."

*Rà soát: không nhắc solution, không nói "bọn mình muốn xin feedback về tính năng".*

### 3.4 Story opener

> "Kể mình nghe về **lần gần nhất** bạn đang học một bài mà gặp một đoạn không hiểu — hôm đó là bài gì, và bạn đang làm gì lúc đó?"

### 3.5 Big 3 Questions

| # | Điều cần học | Câu hỏi sẽ dùng |
|---|---|---|
| 1 | Situation có thật | "Lần gần nhất đó là khi nào, bạn đang ở đâu và đang làm gì? Kể lại giúp mình từ lúc bạn nhận ra mình không hiểu." |
| 2 | Chẩn đoán hay gián đoạn *(A vs B)* | "Lúc dừng lại ở đoạn đó, trong đầu bạn nghĩ gì? Bạn có nói ra được là mình đang thiếu cái gì không, hay chỉ thấy đoạn đó khó?" |
| 3 | Workaround và hậu quả | "Sau đó bạn làm gì? Kể mình nghe từng bước — mất khoảng bao lâu, và cuối cùng bài đó bạn có học xong không?" |

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
- [ ] ⬜ Interviewee đã đáp ứng tiêu chí tuyển *(xác nhận khi tuyển được người)*
- [ ] ⬜ Đã biết mình sẽ phỏng vấn ai *(phân công trong nhóm)*

> ✅ **CHECKPOINT 2 — Interview-ready**
> Guide bắt đầu từ một sự kiện gần đây; ba câu hỏi chính nối trực tiếp với Big 3; probe bank đào hành vi–workaround–hậu quả; và không để lộ solution directive.

---

## 4. Practice Reflection — Chặng 4

> ⬜ **CẦN ĐIỀN SAU KHI PHỎNG VẤN.** Ba câu dưới đây phải được viết sau khi tự nghe lại cuộc phỏng vấn của chính mình. Không được để AI viết thay — xem mục 5.

### 4.1 Câu hỏi nào đã giúp user kể một tình huống cụ thể?

⬜ *…*

### 4.2 Chỗ nào mình cần làm tốt hơn ở lần phỏng vấn thật?

⬜ *…*

### 4.3 Sau khi luyện, nhóm đã sửa Conversation Guide ở đâu và vì sao?

⬜ *…*

> ⬜ **CHECKPOINT 3 — Practice completed:** chưa đạt. Cần hoàn thành một lượt làm interviewer, có Interview Record trong `interview/notes.md` và bản ghi đã được người tham gia đồng ý.

---

## 5. AI Support Log

*Khai báo theo yêu cầu của lab: "Mọi cách dùng AI phải được khai báo trong README của repo."*

**Công cụ đã dùng:** Claude (Claude Code), ngày 17/08/2026.

| # | AI đã giúp gì | Trạng thái |
|---|---|---|
| 1 | Đọc và tóm tắt 6 trang tài liệu lab (Đề bài, Ba case, Chặng 1–4) để xác định đúng yêu cầu của "Repo cá nhân cần nộp" | Hỗ trợ đọc hiểu |
| 2 | Dựng cấu trúc repo và khung 5 phần của README theo đúng đặc tả Chặng 4 | Hỗ trợ định dạng |
| 3 | **Soạn bản nháp Chặng 1** (capability trung tính, chuỗi Change, bảng Actor, Situation & Job, JTBD, hai Pain Hypothesis A/B, bảng Evidence, Solution Parking Lot) | ⚠️ **Bản nháp — cần nhóm tự rà soát và sửa lại bằng lập luận của nhóm** |
| 4 | **Soạn bản nháp Conversation Guide** (Big 3, lời mở đầu, story opener, 3 câu hỏi chính, ba phản xạ) và rà soát xem câu hỏi có làm lộ solution / có hỏi ý kiến hay dự đoán tương lai không | ⚠️ **Bản nháp — cần nhóm chốt lại ở Chặng 2** |
| 5 | Soạn `interview/interview-script.md` — kịch bản cầm tay 15 phút chia theo block thời gian, danh sách câu không được hỏi, và checklist tự kiểm sau phỏng vấn | ⚠️ **Bản nháp — công cụ luyện tập, không phải dữ liệu** |
| 6 | Soạn `practice/rehearsal-roleplay.md` — hội thoại **hư cấu** để đóng vai tập phản xạ Deflect/Anchor/Dig | ⚠️ **HƯ CẤU 100%.** Đã bị thay thế bởi dòng 8. |
| 7 | Quét `DAY 01` → `DAY 17` lấy bối cảnh thật: chương trình học, đề bài hackathon Day 05–06, và **thống kê tổng hợp** từ `DATA_DICTIONARY.md` của chatlog VLearn đã ẩn danh → viết mục 2.0 và bổ sung Pain Hypothesis C | Hỗ trợ desk research. **Chỉ dùng số liệu tổng hợp, không trích nội dung hội thoại của học viên nào.** |
| 8 | Soạn `practice/3-bo-cau-hoi-va-kich-ban.md` — ba bộ câu hỏi phân công cho ba thành viên + ba kịch bản trả lời **hư cấu** (P01/P02/P03) | ⚠️ Phần câu hỏi là công cụ thật; **phần kịch bản trả lời HƯ CẤU 100%**, không dòng nào được sang `notes.md`. |

**AI KHÔNG được dùng cho:**

- ❌ Tạo interview data hoặc bịa quote — `interview/notes.md` là khung trống, mọi nội dung phải do chính người phỏng vấn ghi lại.
- ❌ Suy diễn chi tiết user chưa nói.
- ❌ Viết Practice Reflection thay cho việc tự nghe lại cuộc phỏng vấn — mục 4 để trống có chủ đích.

**Điểm nào hời hợt / sai và mình đã tự sửa thế nào:**

⬜ *Cần điền sau khi nhóm rà soát lại mục 2 và mục 3. Lab quy định AI chỉ nên dùng để "gợi ý cách diễn đạt hoặc rà soát câu hỏi dẫn dắt"; phần nội dung nháp ở trên vượt quá mức đó, nên nhóm phải tự đọc lại, sửa và ghi rõ đã sửa gì tại đây thì bài mới hợp lệ.*

---

## Kiểm tra trước khi nộp

- [ ] ⬜ Repo đúng tên theo quy định lab: `Track1_Day17_MHV_HoVaTen` *(thư mục hiện tại đang theo quy ước lớp `K4-Track1-DAY17-…` — cần xác nhận với giảng viên/TA dùng tên nào)*
- [x] `README.md` đủ năm phần
- [ ] ⬜ `interview/notes.md` là notes của chính lượt mình làm interviewer
- [ ] ⬜ Bản ghi hoặc recording link mở được với giảng viên/TA *(và không để chế độ công khai)*
- [ ] ⬜ Người được phỏng vấn đã đồng ý cho ghi lại
- [x] Conversation Guide không làm lộ solution
- [ ] ⬜ Conversation Guide đã được sửa sau khi luyện

## Bốn gate đánh giá — tự chấm

| Gate | Trạng thái | Ghi chú |
|---|---|---|
| 1. Problem Framing | ✅ Đạt | Đi đủ chuỗi Solution → Evidence; giả thuyết cụ thể và có thể bị bác bỏ (mục 2.7) |
| 2. Interview Design | ✅ Đạt | Big 3 nối với điều cần học; câu hỏi hỏi quá khứ, không lộ solution (mục 3) |
| 3. Interview Practice | ⬜ Chưa đạt | Chưa thực hiện Chặng 3 |
| 4. Reflection & Revision | ⬜ Chưa đạt | Chưa có trải nghiệm luyện để phản tư |
