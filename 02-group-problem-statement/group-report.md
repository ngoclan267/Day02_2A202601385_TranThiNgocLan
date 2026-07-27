# Group Report — Day 02

## Chủ đề nhóm

**Trợ lý tuyển sinh AI cho Trường X**

Hệ thống hỗ trợ học sinh và phụ huynh tra cứu 24/7 các thông tin như ngành học, học phí, học bổng, hồ sơ, phương thức xét tuyển và thời hạn đăng ký dựa trên tài liệu chính thức. Các trường hợp thiếu dữ liệu, phức tạp hoặc nhạy cảm được chuyển cho cán bộ tuyển sinh kèm ngữ cảnh hội thoại.

> **Lưu ý:** Nhóm chưa có log vận hành thực tế của Trường X. Các số liệu bên dưới là target cho pilot và cần được xác nhận bằng phỏng vấn hoặc log thật.

## Thành viên nhóm

| Họ và tên | Mã học viên | Đóng góp chính |
|---|---|---|
| Nguyễn Hoàng Biên | 2A202601233 | Problem owner, pain point tuyển sinh |
| Vũ Tú Quỳnh | 2A202601239 | Workflow, metric, tổng hợp report |
| Trần Thị Ngọc Lan | 2A202601385 | Shortlist và phương án thay thế |
| Nguyễn Đặng Kỳ Anh | 2A202601501 | Research và rủi ro |
| Nguyễn Ngọc Nam | 2A202601561 | Boundary, pilot và quyết định cuối |

---

# 1. Problem được chọn

## 1.1. Tác vụ lặp lại

Trong mùa tuyển sinh, cán bộ phải trả lời lặp lại các câu hỏi về:

- Học phí và học bổng.
- Ngành học và chương trình đào tạo.
- Phương thức, điều kiện xét tuyển.
- Hồ sơ và thời hạn đăng ký.
- Điểm chuẩn các năm trước.

Phần lớn câu trả lời đã tồn tại trong website, thông báo hoặc PDF chính thức nhưng cán bộ vẫn phải đọc câu hỏi, tìm tài liệu và viết lại câu trả lời cho từng người.

## 1.2. Điểm đau

**Học sinh và phụ huynh:**

- Phải tìm và đối chiếu nhiều nguồn.
- Khó nhận phản hồi vào buổi tối, cuối tuần hoặc sát deadline.
- Có nguy cơ hiểu sai thông tin, thiếu hồ sơ hoặc bỏ lỡ thời hạn.

**Cán bộ tuyển sinh:**

- Bị quá tải bởi hàng trăm câu hỏi tương tự trong mùa cao điểm.
- Mất thời gian tra cứu và gõ lại thông tin.
- Phản hồi có thể chậm hoặc thiếu nhất quán.
- Ít thời gian cho các trường hợp cần tư vấn chuyên sâu.

## 1.3. AI có thể hỗ trợ gì?

AI có thể hiểu nhiều cách diễn đạt, tìm đúng đoạn trong nguồn chính thức, tạo câu trả lời dễ hiểu và kèm trích dẫn. Khi không đủ nguồn hoặc gặp trường hợp nhạy cảm, hệ thống phải chuyển cho cán bộ.

AI không được dự đoán chắc chắn khả năng trúng tuyển, tự phê duyệt hồ sơ hoặc tự thực hiện giao dịch.

---

# 2. Group Convergence

## 2.1. Candidates chính

| Candidate | Actor | Bottleneck chính | Nhận xét |
|---|---|---|---|
| Trợ lý tuyển sinh | Học sinh, phụ huynh, cán bộ | Chờ phản hồi và tra cứu thủ công | Workflow rõ, dễ giới hạn nguồn |
| Tổng đài ngân hàng quá tải | Khách hàng, tổng đài viên | Phải gọi lại nhiều lần | Impact cao nhưng phần lớn cần queue/callback |
| Lọc CV cho HR | HR, ứng viên | Đọc và đối chiếu CV thủ công | Có rủi ro bias |
| Tra cứu thông tin thuốc | Bệnh nhân | Thông tin khó hiểu và phân tán | Rủi ro y tế cao |
| Nhân viên tìm quy trình nội bộ | CBNV, mentor | Không biết đúng từ khóa/tài liệu | Phù hợp semantic search nhưng cần quyền dữ liệu |

## 2.2. Shortlist và score

Thang điểm 1–5.

| Candidate | Actor rõ | Workflow rõ | Impact đo được | Dễ pilot | Rủi ro kiểm soát được | Tổng |
|---|---:|---:|---:|---:|---:|---:|
| Trợ lý tuyển sinh | 5 | 5 | 5 | 5 | 4 | **24** |
| Tổng đài ngân hàng | 5 | 5 | 5 | 3 | 2 | 20 |
| Lọc CV | 5 | 4 | 4 | 4 | 2 | 19 |
| Tra cứu thuốc | 5 | 4 | 5 | 2 | 1 | 17 |

**Nhóm chọn: Trợ lý tuyển sinh AI.**

### Vì sao chọn?

- Actor và workflow rõ.
- Câu hỏi lặp lại có nguồn chính thức.
- Có thể pilot với một trường và một mùa tuyển sinh.
- Dễ đo thời gian phản hồi, độ chính xác và tỷ lệ giảm tải.
- Có thể kết hợp Rule, AI và Human Review.

### Vì sao không chọn các bài khác?

- **Tổng đài ngân hàng:** bottleneck chính có thể giải bằng hàng đợi và callback, chưa chắc cần AI.
- **Lọc CV:** có nguy cơ bias và ảnh hưởng cơ hội của ứng viên.
- **Thông tin thuốc:** hậu quả khi AI sai quá cao đối với pilot ngắn.

---

# 3. Quick Validation

## 3.1. Trạng thái

Nhóm chưa phỏng vấn chính thức cán bộ tuyển sinh của Trường X. Validation hiện tại gồm thảo luận nhóm và desk research. Vì vậy, baseline về số lượng câu hỏi và thời gian xử lý vẫn cần đo trước pilot.

## 3.2. Tín hiệu ban đầu

| Nguồn | Tín hiệu xác nhận | Giới hạn | Điều chỉnh của nhóm |
|---|---|---|---|
| Ý tưởng và trải nghiệm của thành viên | Câu hỏi tuyển sinh lặp lại, nhiều nguồn và có mùa cao điểm | Chưa có log thật | Ghi rõ metric là target pilot |
| Quy định tuyển sinh của Bộ GDĐT | Thông tin thay đổi theo năm và phải dựa trên nguồn chính thức | Không thay thế đề án riêng của trường | Mọi câu trả lời phải có năm và citation |
| Chatbot tuyển sinh tại một số trường | Pattern tư vấn 24/7 đã tồn tại | Không có đủ số liệu công khai về accuracy | Không khẳng định hiệu quả nếu chưa đo |
| Tài liệu về knowledge source/RAG | Có thể giới hạn AI trong nguồn được duyệt | Không tự bảo đảm tài liệu còn hiệu lực | Bổ sung content owner và kiểm soát phiên bản |

## 3.3. Problem sau khi thu hẹp

Ban đầu: **Chatbot AI tư vấn và cá nhân hóa toàn bộ hành trình tuyển sinh.**

Sau khi challenge:

> Hỗ trợ trả lời các câu hỏi tuyển sinh phổ biến của một trường, trong một mùa tuyển sinh, dựa trên nguồn chính thức được duyệt; trường hợp thiếu nguồn, phức tạp hoặc nhạy cảm phải chuyển cán bộ.

---

# 4. Research giải pháp hiện có

| Nguồn / case | Phần được giải quyết | Bài học cho nhóm |
|---|---|---|
| [Quy chế tuyển sinh — Bộ GDĐT](https://moet.gov.vn/) | Quy định và mốc tuyển sinh chính thức | Bot phải phân biệt năm và nguồn có thẩm quyền |
| [Cổng tuyển sinh Bộ GDĐT](https://tuyensinh.moet.gov.vn/) | Tập hợp thông tin tuyển sinh chung | Luôn giữ link nguồn để người dùng kiểm chứng |
| [UEF Admission AI Chatbot](https://www.uef.edu.vn/) | Hỏi đáp ngành học, học phí, học bổng và xét tuyển | Scope có thể bắt đầu từ nhóm câu hỏi phổ biến |
| [Microsoft Copilot Studio Knowledge](https://learn.microsoft.com/en-us/microsoft-copilot-studio/knowledge-copilot-studio) | Quản lý và giới hạn nguồn tri thức | Nguồn vẫn cần owner, trạng thái và ngày hiệu lực |

## Research takeaway

Không nên xây một agent tự xử lý toàn bộ tuyển sinh. Hướng phù hợp hơn là:

```text
Chuẩn hóa nguồn
→ Rule kiểm tra scope/rủi ro
→ AI tìm và diễn giải thông tin
→ Trả lời có citation
→ Cán bộ xử lý case ngoại lệ
```

---

# 5. Current Workflow

```text
CURRENT STATE

[1. Người dùng có câu hỏi]
→ [2. Tự tìm website, bài đăng, PDF: 10–30']
→ [3. Không chắc chắn nên gửi tin nhắn/email/hotline]
→ [4. Chờ cán bộ tiếp nhận: vài phút đến nhiều giờ]  <-- bottleneck
→ [5. Cán bộ đọc và phân loại: 1–3']
→ [6. Cán bộ tìm tài liệu: 3–10']                    <-- bottleneck
→ [7. Cán bộ viết và gửi câu trả lời: 2–5']
→ [8. Người dùng hỏi lại nếu chưa rõ]

Failure:
- Dùng nhầm thông tin cũ.
- Cùng câu hỏi được gửi trên nhiều kênh.
- Khi đổi cán bộ, người dùng phải kể lại từ đầu.
```

## Bottleneck và impact

| Bottleneck | Impact |
|---|---|
| Mọi câu hỏi đều phải chờ cán bộ | Người dùng không được hỗ trợ tức thì, đặc biệt ngoài giờ |
| Cán bộ phải tra cứu và viết lại câu trả lời | Hàng đợi tăng và cán bộ không có thời gian cho case khó |
| Nguồn nằm rải rác, có thể khác năm | Nguy cơ trả lời sai hoặc thiếu nhất quán |

---

# 6. Future Workflow

```text
FUTURE STATE

[1. Người dùng nhập câu hỏi]
→ [2. Rule kiểm tra scope, dữ liệu nhạy cảm và nhóm rủi ro]
→ [3. AI tìm trong nguồn chính thức đúng năm]
→ [4. Kiểm tra nguồn có đủ và không mâu thuẫn?]
   ├─ Có → [5. AI trả lời + citation + ngày cập nhật]
   │       → [6. Người dùng đánh giá hữu ích]
   └─ Không / high-risk
           → [5b. Tạo handoff kèm câu hỏi, tóm tắt và nguồn đã kiểm tra]
           → [6b. Cán bộ kiểm tra và trả lời]

Fallback:
- Không có nguồn hoặc confidence thấp → không tự suy đoán.
- Bot lỗi → hiển thị FAQ và kênh liên hệ cán bộ.
```

## Human boundary

AI được phép:

- Trả lời câu hỏi thông tin phổ biến có nguồn.
- Hỏi lại để xác định đúng năm, chương trình hoặc loại hồ sơ.
- Tóm tắt hội thoại cho cán bộ.

AI không được phép:

- Cam kết thí sinh chắc chắn trúng tuyển.
- Phê duyệt hoặc từ chối hồ sơ.
- Tự nộp hồ sơ hay thanh toán.
- Trả lời khi nguồn thiếu, cũ hoặc mâu thuẫn.
- Thay cán bộ xử lý trường hợp cá nhân đặc biệt.

---

# 7. Before / After Impact

Các target sau dùng cho pilot và sẽ điều chỉnh sau khi đo baseline.

| Metric | Trước | Sau kỳ vọng | Cách đo |
|---|---|---|---|
| First response time | Vài phút đến nhiều giờ | Dưới 15 giây với câu hỏi in-scope | Log timestamp |
| Tỷ lệ tự phục vụ | 0% nếu chưa có chatbot | ≥70% câu hỏi in-scope | Phiên resolved không cần cán bộ |
| Thời gian cán bộ cho câu hỏi phổ biến | Chưa đo; giả định 5–15 phút/case | Giảm ≥40% | Time study trước/sau |
| Factual accuracy | Chưa có benchmark | ≥95%, 0 critical error | Gold set do cán bộ chấm |
| Citation correctness | Không chuẩn hóa | ≥98% | Audit câu trả lời và nguồn |
| Câu trả lời AI có citation | Không áp dụng | 100% | Log |
| CSAT | Chưa đo | ≥4/5 | Rating cuối phiên |

**Bottleneck mới:** cán bộ review case ngoại lệ. Đây là điểm nghẽn chấp nhận được vì con người tập trung vào các trường hợp cần phán đoán.

---

# 8. Problem Statement v0

| Field | Nội dung |
|---|---|
| Actor | Học sinh, phụ huynh và cán bộ tuyển sinh |
| Workflow | Người dùng tự tìm nhiều nguồn; nếu chưa rõ thì hỏi cán bộ; cán bộ tra cứu và trả lời |
| Bottleneck | Chờ phản hồi và cán bộ phải xử lý nhiều câu hỏi lặp lại |
| Impact | Người dùng chờ lâu, cán bộ quá tải |
| Success metric | Trả lời nhanh và giảm tải |
| Boundary | Chuyển câu hỏi khó cho cán bộ |

## Điểm yếu của v0

- Actor và phạm vi còn rộng.
- “Nhanh” và “giảm tải” chưa có con số.
- Chưa nói rõ nguồn nào được sử dụng.
- Chưa xác định câu hỏi nào phải chuyển người thật.
- Chưa có điểm can thiệp cụ thể của AI.

---

# 9. So sánh No AI / Rule / Workflow / Agent

| Mức | Phương án | Điểm mạnh | Giới hạn | Chọn? |
|---|---|---|---|---|
| **No AI** | Gom tài liệu, chuẩn hóa FAQ và một kênh tư vấn | Ít rủi ro, bắt buộc phải làm | Người dùng vẫn phải tìm đúng từ khóa | Làm nền tảng |
| **Rule** | Menu, decision tree, keyword và mẫu trả lời cố định | Dễ kiểm soát và audit | Khó xử lý nhiều cách hỏi và câu hỏi kết hợp | Dùng cho guardrail |
| **Workflow** | Rule → retrieval → AI trả lời có nguồn → handoff | Linh hoạt nhưng vẫn kiểm soát từng bước | Cần kiểm soát hallucination và nguồn cũ | **Chọn** |
| **Agent** | AI tự chọn công cụ và thực hiện nhiều hành động | Có thể xử lý nhiệm vụ động | Quá rộng, khó audit, nhiều rủi ro quyền hạn | Không chọn |

## Vì sao chọn Workflow?

- Quy trình tuyến tính và điểm can thiệp của AI rõ.
- Rule đủ cho điều kiện cố định và guardrail.
- AI hữu ích khi hiểu cách hỏi và diễn giải tài liệu.
- Cán bộ vẫn kiểm tra case rủi ro.
- Chưa cần AI tự lập kế hoạch hoặc tự hành động như Agent.

---

# 10. Problem Statement v1

| Field | Nội dung |
|---|---|
| **Actor** | Học sinh lớp 12 và phụ huynh tìm hiểu một mùa tuyển sinh cụ thể của Trường X; actor vận hành là cán bộ tuyển sinh |
| **Workflow** | Tự tìm website/PDF → gửi câu hỏi → chờ cán bộ → cán bộ phân loại, tìm nguồn, trả lời và xử lý follow-up |
| **Bottleneck** | Mọi câu hỏi đều phải chờ cán bộ; cán bộ mất thời gian tìm và viết lại thông tin đã tồn tại |
| **Impact** | Người dùng có thể nhận thông tin chậm hoặc sai thời điểm; cán bộ quá tải và ít thời gian cho case chuyên sâu |
| **Baseline** | Chưa có log; cần đo first response time, handling time và tỷ lệ câu hỏi lặp lại trong ít nhất một tuần |
| **Success metric** | First response <15 giây; ≥70% câu hỏi in-scope tự phục vụ; factual accuracy ≥95%; citation correctness ≥98%; 0 critical error; effort cán bộ giảm ≥40% |
| **Boundary** | Một trường, một mùa tuyển sinh, chỉ nguồn approved; không dự đoán đỗ, không phê duyệt/nộp hồ sơ, không thanh toán; case thiếu nguồn hoặc high-risk chuyển cán bộ |
| **AI intervention point** | Sau khi nhận và kiểm tra scope của câu hỏi, trước bước cán bộ phải tự tìm tài liệu và viết câu trả lời |
| **Mức chọn** | Workflow: Rule kiểm tra → AI retrieval và draft → citation/validation → trả lời hoặc handoff |
| **Rủi ro và người kiểm tra** | Hallucination, nguồn hết hiệu lực, citation sai. Content owner duyệt nguồn; cán bộ xử lý case escalated và audit câu trả lời |

## Problem Statement 1 câu

> Trong mùa tuyển sinh, học sinh và phụ huynh của Trường X phải tự tìm nhiều nguồn hoặc chờ cán bộ trả lời các câu hỏi phổ biến, trong khi cán bộ phải tra cứu và viết lại cùng một tập thông tin; nhóm đề xuất pilot workflow hỏi đáp từ nguồn chính thức có citation và human handoff, nhằm tự phục vụ ít nhất 70% câu hỏi in-scope, đạt factual accuracy tối thiểu 95% và không có lỗi nghiêm trọng về học phí, điều kiện hoặc deadline.

---

# 11. Final Decision

## Decision

**GO cho pilot nhỏ; NOT YET cho production.**

## Lý do

- Problem, actor và workflow đã rõ.
- AI nằm ở một bước cụ thể, không ôm toàn bộ quy trình.
- Có nguồn chính thức để bắt đầu.
- Có human handoff và fallback.
- Chưa đủ baseline, log thật và content owner để triển khai production.

## Pilot nhỏ nhất

- Một trường và một mùa tuyển sinh.
- 5–8 nhóm câu hỏi phổ biến.
- 30–50 nguồn chính thức được duyệt.
- Web chatbot read-only.
- Gold set 150–200 câu hỏi để đánh giá.
- Không tích hợp hồ sơ, thanh toán hoặc CRM ở vòng đầu.

## Quality gate

- Factual accuracy ≥95%.
- Citation correctness ≥98%.
- 0 critical error.
- High-risk escalation ≥95%.
- Self-service ≥70%.
- CSAT ≥4/5.

## Exit / Rollback

- Nếu xuất hiện lỗi nghiêm trọng về học phí, điều kiện hoặc deadline: tắt AI answer và quay về FAQ + cán bộ.
- Nếu AI thường xuyên dùng sai nguồn hoặc cán bộ phải viết lại phần lớn câu trả lời: hạ xuống Rule/Search.
- Không Go production nếu chưa có content owner, source of truth, cơ chế handoff và log audit.

---

# 12. Kết luận

Nhóm chọn **Workflow**, không chọn Agent. Giải pháp phù hợp nhất là kết hợp:

```text
Nguồn chính thức được quản trị
+ Rule cho scope và guardrail
+ AI cho semantic retrieval và diễn giải
+ Cán bộ cho case phức tạp và quyết định cuối
```

Giá trị của giải pháp không chỉ là “có chatbot”, mà là trả lời nhanh, có nguồn kiểm chứng, giảm công việc lặp lại và biết dừng đúng lúc khi AI không đủ chắc chắn.
