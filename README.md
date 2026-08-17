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

### 2.1 Solution — gỡ khỏi hình thức cụ thể

**Capability trung tính** (không nhắc nút, không nhắc AI, không nhắc màn hình):

> Khi học viên mắc kẹt ở giữa một bài học, hệ thống giúp họ xác định đúng chỗ hiểu sai, lấp lại phần kiến thức nền còn thiếu, rồi đưa họ quay lại đúng chỗ đang học dở.

*Ghi chú gỡ hình thức:* "nút", "AI Tutor", "2–3 câu hỏi chẩn đoán" đều là **cách triển khai đã chọn sẵn**, không phải capability. Nhóm không mặc định đây là cách duy nhất — xem Solution Parking Lot ở mục 2.7.

### 2.2 Change — chuỗi thay đổi được kỳ vọng

```
Solution → học viên có cách xử lý ngay tại chỗ khi mắc kẹt
         → họ không rời khỏi bài / không bỏ dở đoạn khó
         → họ hiểu được phần nền còn thiếu và học tiếp
         → Outcome: hoàn thành bài học thay vì bỏ giữa chừng hoặc hiểu lỏng lẻo
```

Ba thay đổi được kỳ vọng:

1. Khi mắc kẹt, học viên xử lý **ngay trong bài** thay vì rời khỏi bài (mở Google/YouTube, hỏi bạn) hoặc bỏ qua đoạn đó.
2. Học viên **nhận diện được khái niệm nền còn thiếu**, chứ không chỉ biết mơ hồ là "mình không hiểu".
3. Học viên **quay lại đúng chỗ đang dở** và học tiếp, thay vì mất mạch và phải bắt đầu lại.

*Mắt xích đang bị ngầm tin:* team đang tin rằng học viên **không tự chẩn đoán được** phần nền còn thiếu. Đây là mắt xích yếu nhất — toàn bộ giá trị của bước "AI chẩn đoán" nằm ở đây.

### 2.3 Actor — các nhóm người có liên quan

| Actor | Họ đang làm gì | Pain hoặc hậu quả có thể có | Họ hưởng lợi thế nào |
|---|---|---|---|
| **Học viên đang học giữa bài** *(chọn)* | Đọc/xem một bài học mới, làm quiz trong bài | Mắc kẹt ở một đoạn, không rõ mình thiếu gì, mất mạch | Học xong bài, giữ được đà học |
| Học viên đã bỏ dở khóa | Không quay lại khóa học | Đã mất đà từ lâu, rào cản quay lại lớn | Có đường quay lại rõ ràng |
| Giảng viên / TA | Trả lời câu hỏi của học viên ngoài giờ | Cùng một câu hỏi lặp lại; không biết cả lớp vướng ở đâu | Giảm câu hỏi lặp, thấy được điểm vướng chung |
| Người biên soạn nội dung | Viết và sửa bài học | Không biết đoạn nào của bài gây vướng | Có tín hiệu để sửa nội dung |

**Actor nhóm chọn để điều tra trước:** Học viên tự học online, trong 7 ngày gần đây đã có lần đang học giữa một bài và gặp một đoạn không hiểu.

**Vì sao chọn nhánh này thay vì actor khác:** đây là actor **trực tiếp trải nghiệm pain** và cũng là actor **phải thay đổi hành vi** thì outcome mới xảy ra. Giảng viên chỉ chịu hậu quả gián tiếp; người biên soạn nội dung không có mặt tại thời điểm pain xảy ra. Nếu học viên không thực sự mắc kẹt theo cách nhóm đang hình dung, hoặc đã có workaround đủ tốt, thì cả chuỗi phía sau sụp — nên phải kiểm tra nhánh này trước.

### 2.4 Situation & Job

**Mô tả Situation & Job:**

> Khi **đang học giữa một bài mới và gặp một đoạn không hiểu**, **học viên tự học online** đang cố **hoàn thành bài học đó** bằng cách **đọc lại đoạn đó nhiều lần, tua lại video, hoặc mở nguồn ngoài để tra**.

**JTBD Hypothesis:**

> Khi **tôi đang học giữa bài và gặp một đoạn không hiểu**, tôi muốn **nhanh chóng biết mình đang thiếu kiến thức nền nào và lấp được nó**, để có thể **học tiếp bài đang dở mà không mất mạch**.

*Kiểm tra:* Job này vẫn tồn tại nếu bỏ hoàn toàn AI và nút "Tôi vẫn chưa hiểu" khỏi bối cảnh — học viên vẫn cần lấp phần nền còn thiếu để học tiếp. ✅

### 2.5 Pain — hai cách giải thích cạnh tranh

**Pain Hypothesis A — Vấn đề nằm ở chẩn đoán:**

> Khi **đang học giữa bài và gặp một đoạn không hiểu**, **học viên** gặp khó khăn trong việc **học tiếp** vì **họ không xác định được mình đang thiếu khái niệm nền nào**, dẫn đến **đọc lại cùng một đoạn nhiều lần hoặc tra lan man, cuối cùng bỏ qua đoạn đó**.

**Pain Hypothesis B — Vấn đề nằm ở chi phí gián đoạn (cách giải thích cạnh tranh):**

> Khi **đang học giữa bài và gặp một đoạn không hiểu**, **học viên** gặp khó khăn trong việc **học tiếp** vì **rời khỏi bài để đi tìm lời giải thích ở nơi khác làm họ mất mạch và tốn thời gian**, dẫn đến **họ chọn bỏ qua đoạn đó và học tiếp trong trạng thái hiểu lỏng lẻo**.

**Khác biệt then chốt giữa A và B:**

| | A — chẩn đoán | B — chi phí gián đoạn |
|---|---|---|
| Học viên có biết mình thiếu gì không? | **Không** | **Có**, nhưng đi lấp thì tốn kém |
| Giải pháp phải làm gì? | Chẩn đoán rồi mới giải thích | Chỉ cần đưa nội dung nền tới tận nơi |
| Bước "AI đặt 2–3 câu hỏi chẩn đoán" | Là phần giá trị nhất | Là công sức thừa, gây phiền |

**Giả thuyết nhóm chọn để điều tra trước: A**

**Lý do chọn:** Solution directive đặt toàn bộ trọng lượng lên bước "AI chẩn đoán khái niệm nền". Nếu thực tế là B — học viên biết khá rõ mình thiếu gì nhưng ngại rời bài đi tra — thì phần chẩn đoán là công sức thừa và feature nên đơn giản hơn nhiều (chỉ cần gắn sẵn nội dung nền tại chỗ). A là **giả định đắt nhất và dễ sai nhất**, nên phải kiểm tra trước.

### 2.6 Evidence — điều cần tìm trước khi viết câu hỏi

| Cần kiểm tra | Evidence làm nhóm tin hơn | Evidence làm nhóm nghi ngờ hoặc bác bỏ |
|---|---|---|
| **Situation có thật** | Kể được một lần cụ thể trong 7 ngày gần đây: tên bài, đoạn nào, đang làm gì, ở đâu | Không nhớ nổi lần nào; chỉ nói "thỉnh thoảng cũng có" |
| **Pain có ý nghĩa** | Dừng lại đáng kể ở đoạn đó, kể được cảm giác và điều xảy ra sau đó, có quay lại chỗ đó | Nói "cũng bình thường thôi", lướt qua rồi quên luôn |
| **Workaround tồn tại** | Kể được thao tác cụ thể (mở Google, hỏi bạn, tua lại video, ghi lại để hỏi sau) và ước lượng được công sức bỏ ra | Không làm gì cả, bỏ qua và không nghĩ tới nữa |
| **Consequence tồn tại** | Bỏ dở bài, làm sai quiz sau đó, phải học lại, trễ deadline, mất tự tin | Vẫn hoàn thành bài bình thường, kết quả không đổi, không nhớ hậu quả nào |
| **Pattern có lặp** | Xảy ra ở nhiều bài khác nhau; kể được cả lần gần nhất trước đó | Chỉ đúng một lần duy nhất, do bài đó đặc biệt khó |
| **Chẩn đoán vs. gián đoạn (A hay B)** | Khi được hỏi "lúc đó bạn có nói được mình thiếu gì không", họ mô tả mơ hồ, không chỉ ra được khái niệm nền | Họ nêu chính xác khái niệm còn thiếu ngay lập tức → nghiêng về B |

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
