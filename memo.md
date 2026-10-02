# Day 16 — Track 1 Product Teardown
# Memo Teardown — ChatGPT

**Họ tên:** Nguyễn Thùy Linh  
**MSV:** 2A202602497  
**Track:** Track 1 — Product Teardown  
**Sản phẩm phân tích:** ChatGPT  
**Thời điểm phân tích:** Tháng 10/2026  

## Vì sao chọn sản phẩm này

Tôi chọn ChatGPT vì đây là sản phẩm AI-native mà AI không chỉ là một tính năng bổ sung mà là phần cốt lõi của toàn bộ trải nghiệm. Từ khi ra mắt dưới dạng research preview năm 2022, ChatGPT đã thay đổi từ một chatbot hỏi–đáp thành một hệ thống có thể tìm kiếm web, nghiên cứu nhiều bước, sử dụng công cụ, truy cập dữ liệu doanh nghiệp và thực hiện các workflow dài. Quá trình này tạo ra một chuỗi quyết định sản phẩm đủ rõ để phân tích theo các nguyên lý x10, learning loop, wrapper/moat và định nghĩa lại “tốt”.

---

# §1. Timeline các cập nhật lớn

| Thời điểm | Cập nhật | Context lúc đó | Nguyên lý |
|---|---|---|---|
| **30/11/2022** | **ChatGPT ra mắt dưới dạng research preview.** OpenAI đưa một mô hình hội thoại tới người dùng phổ thông và chủ động thu thập feedback về điểm mạnh, điểm yếu. Nguồn: OpenAI — *Introducing ChatGPT*. | Trước ChatGPT, các mô hình ngôn ngữ lớn chủ yếu được tiếp cận qua API, demo hoặc sản phẩm dành cho nhóm kỹ thuật. ChatGPT giảm mạnh rào cản sử dụng bằng giao diện hội thoại đơn giản. | **Learning loop.** Cho nhiều người dùng thật tiếp xúc với AI → thu feedback thực tế → phát hiện failure mode → cải thiện model và product. Giá trị của launch không chỉ là tăng user mà còn là tạo vòng lặp học ở quy mô lớn. |
| **14/03/2023** | **GPT-4 được đưa vào ChatGPT Plus.** GPT-4 tăng khả năng xử lý bài toán phức tạp, factuality và multimodal input. OpenAI cũng cho biết feedback từ người dùng ChatGPT được dùng để cải thiện GPT-4. Nguồn: OpenAI — *GPT-4*. | Sau giai đoạn đầu, câu hỏi không còn là “AI có thể trò chuyện không?” mà là “AI có đủ tốt để xử lý công việc nghiêm túc không?”. Người dùng bắt đầu thử ChatGPT với code, học tập và công việc chuyên môn. | **Định nghĩa lại “tốt”.** Chất lượng sản phẩm dịch từ khả năng tạo hội thoại sang độ chính xác, reasoning, khả năng xử lý task khó và độ tin cậy. |
| **06/11/2023** | **Ra mắt GPTs — cho phép người dùng tự tạo phiên bản ChatGPT theo mục đích riêng bằng instructions, knowledge và capabilities.** Nguồn: OpenAI — *Introducing GPTs*. | Một ChatGPT chung không thể được OpenAI tối ưu thủ công cho mọi use case. Nhu cầu của giáo viên, developer, doanh nghiệp và người dùng cá nhân khác nhau đáng kể. | **Wrapper → Moat thông qua ecosystem.** Thay vì OpenAI phải tự xây từng use case, cộng đồng và doanh nghiệp có thể đóng gói knowledge/workflow riêng vào sản phẩm. Giá trị bắt đầu nằm ở hệ sinh thái, cấu hình và dữ liệu xung quanh model, không chỉ ở model nền. |
| **13/05/2024** | **GPT-4o đưa text, vision và audio gần hơn vào cùng một trải nghiệm thời gian thực.** OpenAI công bố thời gian phản hồi audio trung bình khoảng 320 ms trong demo, gần với nhịp hội thoại của con người. Nguồn: OpenAI — *Hello GPT-4o*. | ChatGPT đã hữu ích nhưng interaction vẫn chủ yếu xoay quanh gõ và đọc. Voice và vision trước đó tạo cảm giác tách rời hơn so với hội thoại tự nhiên. | **x10 về trải nghiệm, không chỉ benchmark.** Khi friction chuyển từ “gõ prompt → chờ → đọc” sang nói, nhìn và phản hồi gần thời gian thực, AI dễ đi vào những tình huống trước đây chatbot text khó phục vụ. |
| **31/10/2024** | **ChatGPT Search được tích hợp trực tiếp vào hội thoại và trả về thông tin thời sự kèm nguồn web.** Nguồn: OpenAI — *Introducing ChatGPT Search*. | Một điểm yếu lớn của chatbot là kiến thức có cutoff và người dùng thường phải rời ChatGPT sang Google để kiểm tra thông tin mới. | **Workflow moat / giảm context switching.** Thay vì ChatGPT chỉ sinh câu trả lời rồi buộc user sang search engine, search trở thành một bước bên trong workflow ChatGPT. Sản phẩm giữ được nhiều hơn chuỗi công việc của người dùng. |
| **02/02/2025** | **Deep Research ra mắt như một capability agentic có thể tự tìm kiếm, đọc, phân tích và tổng hợp nhiều nguồn để tạo báo cáo.** Nguồn: OpenAI — *Introducing Deep Research*. | Search giải quyết việc lấy thông tin mới nhưng user vẫn phải tự quyết định nhiều bước: tìm gì tiếp, đọc tài liệu nào và kết nối các bằng chứng ra sao. | **x10 productivity + chuyển từ answer sang outcome.** User không còn chỉ thuê AI “trả lời câu hỏi” mà bắt đầu thuê AI “thực hiện phần research”. Đơn vị giá trị chuyển từ một response sang một công việc nhiều bước. |
| **17/07/2025** | **ChatGPT Agent hợp nhất khả năng reasoning, research và sử dụng browser/tool để thực hiện task thay cho người dùng.** Operator trước đó cũng được tích hợp vào agent. Nguồn: OpenAI — *Introducing ChatGPT Agent*. | Deep Research đã chứng minh AI có thể tự chạy một chuỗi nghiên cứu. Bước tiếp theo là không chỉ “đọc và báo cáo” mà còn thao tác với website, file và ứng dụng. | **Moat từ workflow và tool use.** Nếu sản phẩm chỉ là wrapper quanh model, model thế hệ sau có thể hấp thụ feature đó. Khi AI có browser, file, app, context và quyền thực hiện hành động, giá trị nằm ở cả hệ thống thực thi chứ không chỉ ở chất lượng text generation. |
| **09/07/2026** | **ChatGPT Work được giới thiệu cho các công việc dài và phức tạp: thu thập context từ app/file, lập kế hoạch, thực hiện nhiều bước và tạo thành phẩm như spreadsheet, document, presentation hoặc website.** Work cũng hỗ trợ scheduled tasks và workflow kéo dài. Nguồn: OpenAI — *ChatGPT is now a partner for your most ambitious work*. | Đến 2026, OpenAI đã có Search, Deep Research, Agent, Projects, company knowledge và workspace agents. Rào cản tiếp theo không còn là “AI có biết làm không?” mà là liệu AI có thể mang context của tổ chức vào một workflow ổn định và tạo ra output sử dụng được hay không. | **Wrapper → workflow moat + logic Vertical AI.** ChatGPT Work vẫn là sản phẩm horizontal, nhưng hướng đi ngày càng giống công thức AI Expert + Domain/Company Context: AI được kết hợp với dữ liệu, best practice, app và quy trình riêng của từng nhóm. Moat chuyển dần sang context + workflow + execution. |

## Chuỗi quyết định tôi đọc được từ timeline

Nhìn toàn bộ timeline, tôi thấy ChatGPT không phát triển theo kiểu “thêm ngày càng nhiều feature độc lập”. Có một chuỗi khá nhất quán:

**Chat → Model tốt hơn → Customization → Multimodal → Search → Research → Action → Finished Work.**

Đơn vị giá trị của sản phẩm liên tục tăng lên.

Năm 2022, giá trị là **một câu trả lời hữu ích**.

Đến 2024, giá trị trở thành **một cuộc tương tác tự nhiên hơn và có thông tin thời sự**.

Đến 2025, ChatGPT bắt đầu chịu trách nhiệm cho **một chuỗi công việc nhiều bước**.

Đến 2026, OpenAI mô tả Work theo hướng biến một goal thành **finished work** chứ không chỉ thành một response.

Theo tôi, đây là quyết định chiến lược quan trọng nhất xuyên suốt sản phẩm: **ChatGPT đang di chuyển lên cao dần trong value chain của người dùng.**

## Vì sao tôi chọn những mốc này?

Tôi chọn 8 mốc trên vì mỗi mốc làm thay đổi ít nhất một trong ba thứ:

1. **Khả năng cốt lõi** mà ChatGPT có thể đảm nhận.
2. **Cách user tương tác** với sản phẩm.
3. **Phạm vi workflow** mà user có thể giao cho AI.

Tôi đã cân nhắc đưa **Operator (01/2025)** thành một milestone riêng. Tuy nhiên, tôi loại nó khỏi bảng cuối vì Operator chủ yếu là một bước trung gian thử nghiệm browser-use và sau đó được tích hợp trực tiếp vào ChatGPT Agent vào tháng 7/2025. Việc giữ cả Operator và Agent sẽ làm hai hàng phản ánh gần cùng một quyết định sản phẩm.

Tôi cũng không chọn các lần đổi UI, tăng context window, điều chỉnh rate limit hoặc thay model nhỏ làm milestone vì chúng chủ yếu là **optimization**. Chúng có thể quan trọng về vận hành nhưng chưa đủ làm thay đổi JTBD hoặc vị trí của ChatGPT trong workflow của người dùng.

---

# §2. Tệp user & JTBD

## 2.1. So sánh early adopters và tệp hiện tại

| | Early adopters | Tệp hiện tại |
|---|---|---|
| **Đặc điểm** | Developer junior, sinh viên kỹ thuật và knowledge worker thích thử công nghệ mới; đã quen Google, Stack Overflow, documentation và các công cụ số; chấp nhận việc AI đôi khi trả lời sai để đổi lấy tốc độ. | Knowledge worker và team làm việc thực tế: marketing, operations, finance, sales, analyst, engineering và các nhóm doanh nghiệp cần AI làm việc với file, email, tài liệu, dashboard, app nội bộ và quy trình của công ty. ChatGPT Work hiện được OpenAI định vị cho nhiều function như Finance, Ops, Marketing, Sales, Data Analytics và Engineering. |
| **JTBD chính** | “Khi tôi gặp một vấn đề chưa biết cách xử lý, tôi muốn AI giải thích, brainstorm hoặc tạo bản nháp ngay để tôi không phải mất nhiều thời gian tìm kiếm và ghép thông tin thủ công.” | “Khi tôi có một nhiệm vụ dài gồm nhiều nguồn và nhiều bước, tôi muốn giao cho AI thu thập context, phân tích và tạo ra bản đầu ra có thể review để tôi tập trung vào judgement và quyết định.” |
| **Trước đó họ làm bằng cách nào** | Google → mở nhiều link → Stack Overflow/documentation → copy/paste → tự tổng hợp → viết bản nháp. | Chuyển qua lại giữa email, Slack, Drive, docs, spreadsheet, web, calendar, project tracker và nhiều đồng nghiệp; sau đó tự tổng hợp thành report/deck/document. |
| **Điều họ chấp nhận đánh đổi** | Chấp nhận hallucination và trải nghiệm chưa ổn định vì lợi ích về tốc độ đủ lớn. | Yêu cầu cao hơn nhiều về reliability, provenance, permissions, privacy, governance và khả năng kiểm soát hành động của agent. |
| **Cột mốc thúc đẩy dịch chuyển** | Launch 2022 và GPT-4 2023 tạo giá trị ban đầu cho hỏi–đáp, code, học tập và drafting. | Search → Deep Research → Agent → Company Knowledge/Workspace Agents → Work biến ChatGPT thành công cụ xử lý workflow thay vì chỉ là chatbot. |

## 2.2. Early adopters cụ thể là ai?

Tôi chọn một persona cụ thể để tránh mô tả chung chung:

> **Một developer junior tại startup nhỏ, đã sử dụng VS Code, Google, Stack Overflow và documentation hằng ngày; theo dõi xu hướng AI và sẵn sàng kiểm tra lại output của model.**

### JTBD của persona này

**Khi** gặp code lỗi hoặc một khái niệm kỹ thuật chưa hiểu,  
**tôi muốn** có một công cụ giải thích vấn đề và đề xuất hướng xử lý ngay trong cùng cuộc hội thoại,  
**để** tôi tiếp tục công việc mà không cần mở và đọc hàng loạt kết quả tìm kiếm.

ChatGPT phù hợp với early adopter này vì giá trị ban đầu rất rõ: tốc độ feedback cao và chi phí thử gần như bằng không trong research preview. OpenAI ngay từ launch cũng sử dụng các ví dụ liên quan đến sửa code, giải thích kiến thức và hỏi tiếp trong hội thoại.

## 2.3. Tệp user hiện tại cụ thể

Persona tôi chọn cho giai đoạn hiện tại là:

> **Một marketing/operations executive trong công ty nhỏ hoặc vừa, phải research thị trường, đọc tài liệu, tổng hợp dữ liệu, viết brief/report/deck và phối hợp thông tin từ nhiều công cụ nhưng không có một analyst riêng cho từng nhiệm vụ.**

### JTBD của persona này

**Khi** tôi có một nhiệm vụ cần thu thập dữ liệu từ nhiều nguồn và tạo thành một tài liệu có thể sử dụng,  
**tôi muốn** giao phần tìm kiếm, tổng hợp và tạo first draft cho AI,  
**để** tôi dành thời gian cho việc kiểm chứng, judgement và ra quyết định thay vì xử lý thủ công từng bước.

OpenAI hiện định vị ChatGPT Work đúng theo hướng này: lấy context từ tool/file, lập kế hoạch và tạo thành phẩm như docs, slides, spreadsheets và analyses.

## 2.4. Dịch chuyển tệp user

Theo tôi, không có một milestone duy nhất gây ra sự dịch chuyển này. Đó là một chuỗi:

**Search (2024) → Deep Research (2025) → Agent (2025) → Work (2026).**

- **Search** giảm nhu cầu rời ChatGPT để lấy thông tin mới.
- **Deep Research** cho phép giao một nhiệm vụ nghiên cứu nhiều bước.
- **Agent** cho phép AI không chỉ đọc mà còn hành động bằng browser/tool.
- **Work** nâng đơn vị output từ “answer” lên “finished work”.

Điều này làm tệp khách hàng tiềm năng thay đổi từ **người muốn AI hỗ trợ một task nhỏ** sang **người/team muốn delegate một phần workflow**.

Đây cũng là lý do OpenAI ngày càng đầu tư vào company knowledge, app connections và workspace agents. Company knowledge được thiết kế để lấy context phân tán trong Slack, SharePoint, Google Drive, GitHub và các công cụ khác để trả lời theo đúng bối cảnh doanh nghiệp.

---

## 2.5. Switching Cost — phân tích theo 4 Forces

### Force 1 — Push: điều gì đẩy user khỏi cách làm cũ?

Cách làm cũ của knowledge worker thường bị phân mảnh:

**Search → Docs → Email → Spreadsheet → Slack → Browser → Report.**

User phải tự làm nhiều việc có giá trị thấp:

- tìm tài liệu;
- copy dữ liệu;
- chuyển giữa nhiều app;
- đọc nhiều nguồn;
- tổng hợp lại;
- định dạng thành báo cáo hoặc slide.

Đây là “push” khiến user muốn thử một sản phẩm có thể gom các bước này thành một workflow.

---

### Force 2 — Pull: điều gì kéo user sang ChatGPT?

Pull của ChatGPT ngày càng không chỉ là “model thông minh”.

Nó gồm:

- giao tiếp bằng natural language;
- web search;
- deep research;
- file/context;
- connected apps;
- browser/tool execution;
- workspace agents;
- tạo document, spreadsheet, presentation;
- scheduled/long-running work.

ChatGPT Work hiện được thiết kế để thu thập context, lập kế hoạch và thực hiện hành động trên nhiều nguồn nhằm tạo output hoàn chỉnh.

Điều này làm **product-level pull** mạnh hơn **model-level pull**.

---

### Force 3 — Habit: điều gì khiến user vẫn ở lại cách cũ?

Đây là lực rất mạnh.

Người dùng đã quen:

- Google để search;
- Microsoft Office/Google Workspace để tạo tài liệu;
- Slack/Teams để trao đổi;
- spreadsheet để phân tích;
- browser để thực hiện các thao tác;
- workflow nội bộ của công ty.

Một AI tốt hơn chưa đủ để buộc họ bỏ các thói quen này.

Vì vậy, thay vì yêu cầu user bỏ toàn bộ tool cũ, hướng đi của ChatGPT là **kết nối vào các tool đó**.

Tôi cho rằng đây là một quyết định product quan trọng: ChatGPT không nhất thiết phải thay thế Google Drive, Slack hay GitHub; nó có thể trở thành **orchestration layer nằm phía trên chúng**.

---

### Force 4 — Anxiety: điều gì khiến user ngại chuyển?

Khi ChatGPT chỉ viết text, một câu sai thường dễ sửa.

Khi AI có quyền:

- truy cập dữ liệu công ty;
- gửi thông tin;
- sửa spreadsheet;
- thao tác website;
- thực hiện workflow;

thì hậu quả của lỗi lớn hơn nhiều.

Các anxiety chính gồm:

- hallucination;
- sử dụng sai nguồn;
- privacy;
- quyền truy cập dữ liệu;
- agent thực hiện nhầm action;
- khó biết AI đã làm gì;
- governance trong doanh nghiệp.

Việc OpenAI nhấn mạnh quyền kiểm soát, approvals và security khi triển khai agent cho thấy chính sản phẩm cũng phải giải quyết lực cản này.

---

## 2.6. Lực nào đang giữ user mạnh nhất?

Theo tôi, lực giữ user ngày càng mạnh nhất không phải chỉ là **habit với giao diện ChatGPT**, mà là **workflow + context tích lũy**.

Một user có thể dễ chuyển giữa hai chatbot nếu cả hai chỉ nhận một prompt và trả lại text.

Nhưng switching cost tăng khi trong ChatGPT đã có:

- project context;
- file;
- conversation history;
- instructions;
- company knowledge;
- connected apps;
- workspace agents;
- scheduled workflows.

Khi đó việc chuyển sản phẩm đồng nghĩa với việc phải **rebuild context và workflow**, không chỉ đổi model.

Nếu layer context/workflow này biến mất và các đối thủ có model tương đương, moat của ChatGPT sẽ yếu đi đáng kể. Đây là lý do tôi cho rằng moat dài hạn phải nằm trên model.

---

# §3. Ba dự đoán hướng đi trong 6–12 tháng tới

**Khung thời gian dự đoán: khoảng tháng 04/2027 đến tháng 10/2027.**

Các phần dưới đây là **phán đoán của tôi từ dữ liệu**, không phải thông tin OpenAI đã công bố chắc chắn.

## Dự đoán 1 — ChatGPT Work sẽ chuyển mạnh từ “agent theo yêu cầu” sang “agent chủ động vận hành workflow”

**Loại:** Mở rộng tính năng

- **Dự đoán:** Trong 6–12 tháng tới, ChatGPT sẽ tăng khả năng cho Work/workspace agents chạy các workflow dài, lặp lại hoặc theo trigger; theo dõi thay đổi và chỉ yêu cầu user can thiệp tại các checkpoint quan trọng. User sẽ ngày càng giao một **outcome** thay vì một prompt.
- **Lập luận:** §1 cho thấy progression nhất quán từ Search → Deep Research → Agent → Work. Mỗi bước giảm thêm lượng thao tác mà user phải tự thực hiện. Work hiện đã hỗ trợ scheduled tasks và các nhiệm vụ dài, còn workspace agents có thể dùng app, skill và lịch chạy cho workflow lặp lại. Vì JTBD của user hiện tại trong §2 là “hoàn thành một công việc nhiều bước”, bước hợp lý tiếp theo là AI duy trì workflow lâu hơn và chủ động hơn thay vì chỉ phản ứng theo từng request.

**Giả định quan trọng:** OpenAI phải giữ được mức reliability và cơ chế approval đủ tốt. Nếu agent vẫn cần user kiểm tra gần như từng bước, progression này sẽ chậm lại.

---

## Dự đoán 2 — ChatGPT sẽ “verticalize” ở cấp doanh nghiệp thông qua company context, skills và workspace agents

**Loại:** Mở rộng segment / Vertical AI

- **Dự đoán:** ChatGPT sẽ không cần biến thành hàng chục sản phẩm AI ngành dọc riêng biệt; thay vào đó OpenAI sẽ đẩy mạnh khả năng để doanh nghiệp tự tạo các agent chuyên biệt cho từng phòng ban hoặc nghiệp vụ, ví dụ sales operations, financial reporting, recruiting, customer support hoặc internal research.
- **Lập luận:** GPTs năm 2023 đã thử nghiệm việc cho user đóng gói instructions và knowledge. Đến 2025–2026, company knowledge và workspace agents nâng pattern này lên cấp tổ chức: agent có thể dùng kiến thức công ty, connected apps, skill và workflow lặp lại. Điều này gần với nguyên lý **Vertical AI = AI Expert + Domain Expert**, nhưng domain expertise được doanh nghiệp nạp vào hệ thống thay vì OpenAI tự xây từng vertical. §2 cũng cho thấy tệp hiện tại cần AI hiểu context riêng của tổ chức chứ không chỉ kiến thức chung.

**Giả định quan trọng:** Doanh nghiệp phải sẵn sàng cấp quyền cho AI truy cập dữ liệu và quy trình nội bộ. Nếu privacy/governance trở thành blocker lớn, adoption sẽ chậm hơn.

---

## Dự đoán 3 — Mô hình kiếm tiền sẽ ngày càng dựa vào “agent capacity / mức công việc được thực hiện” thay vì chỉ quyền truy cập model

**Loại:** Thay đổi mô hình kiếm tiền

- **Dự đoán:** Trong 6–12 tháng tới, OpenAI sẽ tiếp tục phân tầng các gói Business/Enterprise theo lượng agentic work, compute và mức automation mà mỗi user/team sử dụng; pricing sẽ ngày càng phản ánh **khối lượng công việc AI thực hiện** thay vì chỉ “được dùng model nào”.
- **Lập luận:** Đây đã là tín hiệu có thể nhìn thấy trong pricing hiện tại. ChatGPT Business có Standard và Premium seat khác nhau về mức usage, đồng thời các tính năng nâng cao và agent/workflow có thể dùng credit hoặc flexible pricing. Khi product chuyển từ tạo câu trả lời sang chạy workflow dài hàng phút/giờ, chi phí compute và giá trị kinh tế của từng task chênh lệch rất lớn. Vì vậy pricing dựa đơn thuần trên “subscription có model X” sẽ ngày càng không phản ánh đúng cost/value.

**Giả định quan trọng:** User doanh nghiệp phải nhìn thấy ROI đủ rõ từ agentic workflow. Nếu giá trị đầu ra không ổn định, khách hàng sẽ khó chấp nhận pricing dựa trên usage/work performed.

---

## Dự đoán tôi tự tin nhất

Tôi tự tin nhất với **Dự đoán 1 — ChatGPT tiếp tục đi từ phản hồi sang thực thi workflow chủ động hơn**.

Lý do là đây không phải một thay đổi hướng hoàn toàn mới mà là continuation của một pattern đã xuất hiện liên tục:

**Answer → Search → Research → Action → Work.**

Từ timeline, mỗi product generation đều lấy thêm một phần công việc mà trước đó user phải tự thực hiện.

Giả định có thể làm dự đoán này gãy là **reliability**. Nếu AI vẫn mắc lỗi quá thường xuyên khi chạy autonomous workflow, user sẽ tiếp tục chỉ sử dụng agent như một copilot có supervision cao thay vì giao toàn bộ outcome.

---

# §4. AI Log

| Việc | AI làm hay bạn làm? | Bạn kiểm chứng/phán đoán lại thế nào? |
|---|---|---|
| Giải thích đề bài và rubric | **AI hỗ trợ** | Tôi đọc lại yêu cầu gốc và đối chiếu rằng memo phải có đủ Timeline, User/JTBD, 3 Predictions và AI Log. |
| Đề xuất sản phẩm để teardown | **AI gợi ý, tôi quyết định** | AI so sánh một số lựa chọn như ChatGPT, Cursor và Canva. Tôi chọn ChatGPT vì thỏa 3 tiêu chí của đề: AI là core product, có đủ dữ liệu công khai cho ≥6 milestone và JTBD xác định được. |
| Thu thập danh sách milestone ứng viên | **AI hỗ trợ research** | Tôi yêu cầu ưu tiên nguồn gốc từ OpenAI và kiểm tra lại ngày công bố, tên feature và mô tả trên trang chính thức. |
| Chọn 8 milestone cuối cùng | **AI hỗ trợ, tôi phán đoán** | Tôi chỉ giữ các mốc làm thay đổi capability, interaction hoặc phạm vi workflow. Tôi loại Operator khỏi bảng riêng vì sau đó capability này được hợp nhất vào ChatGPT Agent. |
| Viết context cho từng milestone | **AI hỗ trợ tổng hợp** | Tôi kiểm tra context có thực sự giải thích “vì sao nước đi xảy ra lúc đó” thay vì chỉ lặp lại changelog. |
| Revert milestone về nguyên lý | **AI hỗ trợ brainstorm, tôi chọn framework** | Tôi map lại từng mốc vào các khái niệm đã học: x10, learning loop, wrapper/moat, definition of good và Vertical AI. Tôi tránh các nhãn chung chung như “để tăng trưởng”. |
| Xác định early adopter và user hiện tại | **AI hỗ trợ brainstorm, tôi phán đoán** | Tôi cụ thể hóa thành persona có hành vi và workflow rõ ràng thay vì các nhóm chung như “người trẻ” hoặc “dân văn phòng”. |
| Viết JTBD | **AI hỗ trợ cấu trúc** | Tôi kiểm tra từng JTBD phải mô tả “việc cần làm” và outcome, không viết dưới dạng feature như “user cần chatbot”. |
| Phân tích switching cost | **AI hỗ trợ framework** | Tôi tự map Push, Pull, Habit và Anxiety vào workflow ChatGPT và kiểm tra xem từng lực có phù hợp với persona ở trên hay không. |
| Đưa ra 3 dự đoán | **AI brainstorm + tôi phán đoán** | Tôi chỉ giữ các dự đoán có thể dẫn ngược về ít nhất một pattern trong §1 và một JTBD/segment trong §2; bỏ các câu chung chung như “ChatGPT sẽ thông minh hơn”. |
| Kiểm tra thông tin hiện tại đến 10/2026 | **AI hỗ trợ research web** | Tôi ưu tiên nguồn OpenAI chính thức và phân biệt rõ dữ kiện đã xảy ra với dự đoán 6–12 tháng phía trước. |
| Hoàn thiện memo | **AI hỗ trợ biên tập** | Tôi đọc lại toàn bộ memo và kiểm tra chuỗi logic Timeline → User/JTBD → Prediction trước khi nộp. |

---

# Kết luận

Qua teardown này, điều tôi học được không phải là ChatGPT đã có bao nhiêu tính năng mà là **chuỗi logic trong các quyết định sản phẩm**.

ChatGPT bắt đầu bằng việc giảm rào cản để người bình thường có thể sử dụng LLM qua giao diện hội thoại. Sau đó sản phẩm liên tục di chuyển lên một tầng giá trị cao hơn:

**trả lời tốt hơn → tương tác tự nhiên hơn → truy cập thông tin mới → tự nghiên cứu → hành động → hoàn thành workflow.**

Điều này cũng làm moat thay đổi. Ở giai đoạn đầu, lợi thế phần lớn nằm ở model. Khi model giữa các nhà cung cấp ngày càng tiến gần nhau, moat cần dịch sang những thứ khó bị model khác hấp thụ hơn: **user context, company data, integrations, workflow, ecosystem và khả năng thực thi đáng tin cậy**.

Từ góc nhìn JTBD, ChatGPT cũng đang chuyển từ một sản phẩm mà user “thuê để giúp mình nghĩ hoặc viết” sang một sản phẩm mà user có thể “thuê để thực hiện một phần công việc”. Theo tôi, khả năng ChatGPT tiếp tục mở rộng phụ thuộc rất lớn vào việc OpenAI có giải quyết được tension giữa **autonomy** và **trust** hay không: agent càng có khả năng hành động nhiều thì giá trị càng lớn, nhưng yêu cầu về reliability, permissions và user control cũng tăng tương ứng.

---

## Checklist trước khi nộp

- [x] Có 8 milestone, nằm trong yêu cầu 6–8 mốc.
- [x] Mỗi milestone là một quyết định sản phẩm lớn, không phải bug fix/changelog nhỏ.
- [x] Mỗi milestone có nguồn kiểm chứng.
- [x] Mỗi milestone được revert về nguyên lý có tên.
- [x] Có giải thích milestone bị loại và lý do loại.
- [x] Early adopter được mô tả cụ thể.
- [x] User hiện tại được mô tả cụ thể.
- [x] JTBD viết theo việc cần làm, không theo feature.
- [x] Segment shift được nối ngược về §1.
- [x] Switching cost được map đủ Push / Pull / Habit / Anxiety.
- [x] Có đúng 3 dự đoán cho 6–12 tháng tới.
- [x] Mỗi prediction đều dẫn ngược về §1–§2.
- [x] Phân biệt dữ kiện và phán đoán.
- [x] AI Log có trên 3 hàng và khai rõ AI hỗ trợ phần nào.
- [x] Memo đủ 4 phần theo template.
