# Day 16 — Track 1 Product Teardown
# Memo Teardown — ChatGPT

**Họ tên:** Nguyễn Thùy Linh  
**MSV:** 2A202602497  
**Track:** Track 1 — Product Teardown  
**Sản phẩm phân tích:** ChatGPT  
**Thời điểm phân tích:** Tháng 10/2026  

## Vì sao chọn sản phẩm này

Tôi chọn ChatGPT vì đây là một sản phẩm AI-native, trong đó AI không chỉ là một tính năng bổ sung mà là phần cốt lõi của trải nghiệm. Từ khi ra mắt dưới dạng research preview năm 2022, ChatGPT đã thay đổi từ một chatbot hỏi–đáp thành một hệ thống có thể tìm kiếm web, nghiên cứu nhiều bước, sử dụng công cụ, truy cập dữ liệu doanh nghiệp và thực hiện các workflow dài.

Quá trình phát triển này tạo ra một chuỗi quyết định sản phẩm đủ rõ để phân tích theo các nguyên lý đã học như **x10, learning loop, wrapper/moat, Vertical AI và định nghĩa lại “tốt”**.

---

# §1. Timeline các cập nhật lớn

| Thời điểm | Cập nhật | Context lúc đó | Nguyên lý |
|---|---|---|---|
| **30/11/2022** | **ChatGPT ra mắt dưới dạng research preview.** OpenAI đưa mô hình hội thoại tới người dùng phổ thông và chủ động thu thập feedback về điểm mạnh, điểm yếu của hệ thống. [Nguồn](https://openai.com/index/chatgpt/) | Trước ChatGPT, các mô hình ngôn ngữ lớn chủ yếu được tiếp cận qua API, demo hoặc sản phẩm dành cho nhóm kỹ thuật. ChatGPT giảm mạnh rào cản sử dụng bằng giao diện hội thoại đơn giản. | **Learning loop.** Cho nhiều người dùng thật tiếp xúc với AI → thu feedback thực tế → phát hiện failure mode → cải thiện model và product. Giá trị của launch không chỉ là tăng user mà còn là tạo vòng lặp học ở quy mô lớn. |
| **14/03/2023** | **GPT-4 được công bố và đưa vào ChatGPT Plus.** GPT-4 cải thiện khả năng xử lý tác vụ phức tạp, hỗ trợ đầu vào văn bản + hình ảnh và OpenAI cho biết feedback từ người dùng ChatGPT được sử dụng để cải thiện hành vi của GPT-4. [Nguồn](https://openai.com/index/gpt-4/) | Sau giai đoạn đầu, câu hỏi không còn chỉ là “AI có thể trò chuyện không?” mà chuyển thành “AI có đủ tốt để xử lý công việc nghiêm túc không?”. Người dùng bắt đầu thử ChatGPT với code, học tập và công việc chuyên môn. | **Định nghĩa lại “tốt”.** Chất lượng sản phẩm dịch từ khả năng tạo hội thoại sang độ chính xác, reasoning, khả năng xử lý task khó và độ tin cậy. |
| **06/11/2023** | **Ra mắt GPTs — cho phép người dùng tạo phiên bản ChatGPT riêng bằng instructions, extra knowledge và skills.** [Nguồn](https://openai.com/index/introducing-gpts/) | Một ChatGPT chung không thể được OpenAI tối ưu thủ công cho mọi use case. Nhu cầu của giáo viên, developer, doanh nghiệp và người dùng cá nhân khác nhau đáng kể. | **Wrapper → Moat thông qua ecosystem.** Thay vì OpenAI phải tự xây từng use case, cộng đồng và doanh nghiệp có thể đóng gói knowledge/workflow riêng vào sản phẩm. Giá trị bắt đầu nằm ở hệ sinh thái, cấu hình và dữ liệu xung quanh model, không chỉ ở model nền. |
| **13/05/2024** | **GPT-4o đưa text, vision và audio vào trải nghiệm thời gian thực tự nhiên hơn.** OpenAI công bố thời gian phản hồi audio trung bình khoảng 320 ms. [Nguồn](https://openai.com/index/hello-gpt-4o/) | ChatGPT đã hữu ích nhưng interaction vẫn chủ yếu xoay quanh gõ và đọc. Voice và vision trước đó tạo cảm giác tách rời hơn so với hội thoại tự nhiên. | **x10 về trải nghiệm.** x10 không nhất thiết chỉ là benchmark cao hơn; nó có thể đến từ việc giảm mạnh friction. Khi interaction chuyển từ “gõ → chờ → đọc” sang nói, nhìn và phản hồi gần thời gian thực, AI đi vào nhiều tình huống mới. |
| **31/10/2024** | **ChatGPT Search được tích hợp trực tiếp vào hội thoại và cung cấp thông tin thời sự kèm link nguồn web.** [Nguồn](https://openai.com/index/introducing-chatgpt-search/) | Một điểm yếu lớn của chatbot là kiến thức có cutoff và user thường phải rời ChatGPT sang search engine để lấy hoặc kiểm tra thông tin mới. | **Workflow moat / giảm context switching.** Thay vì ChatGPT chỉ sinh câu trả lời rồi buộc user sang Google, search trở thành một bước bên trong workflow ChatGPT. Sản phẩm giữ được nhiều hơn chuỗi công việc của người dùng. |
| **02/02/2025** | **Deep Research ra mắt như một capability agentic có thể thực hiện multi-step research, tìm kiếm, phân tích và tổng hợp nhiều nguồn.** [Nguồn](https://openai.com/index/introducing-deep-research/) | Search giải quyết việc lấy thông tin mới, nhưng user vẫn phải tự quyết định tìm gì tiếp, đọc nguồn nào và kết nối bằng chứng ra sao. | **x10 productivity + chuyển từ answer sang outcome.** User không còn chỉ thuê AI “trả lời câu hỏi” mà bắt đầu thuê AI “thực hiện phần research”. Đơn vị giá trị chuyển từ một response sang một công việc nhiều bước. |
| **17/07/2025** | **ChatGPT Agent kết hợp reasoning, research và khả năng sử dụng computer/tools để thực hiện task cho người dùng.** OpenAI mô tả đây là sự phát triển từ Operator và Deep Research. [Nguồn](https://openai.com/index/introducing-chatgpt-agent/) | Deep Research đã chứng minh AI có thể tự chạy một chuỗi nghiên cứu. Bước tiếp theo là không chỉ đọc và báo cáo mà còn thao tác với website, file và các nguồn dữ liệu khác. | **Moat từ workflow và tool use.** Nếu sản phẩm chỉ là wrapper quanh model, model thế hệ sau có thể hấp thụ feature đó. Khi AI có browser, file, app, context và khả năng hành động, giá trị nằm ở cả hệ thống thực thi chứ không chỉ ở text generation. |
| **09/07/2026** | **ChatGPT Work được giới thiệu như một agent có thể thao tác trên apps/files, ở lại với project trong nhiều giờ và biến một goal thành finished work như spreadsheet, slide, document hoặc web app.** [Nguồn](https://openai.com/index/chatgpt-for-your-most-ambitious-work/) | Đến 2026, OpenAI đã có Search, Deep Research và Agent. Rào cản tiếp theo không còn là “AI có biết làm không?” mà là liệu AI có thể lấy đúng context, thực hiện nhiều bước ổn định và tạo ra output có thể sử dụng được hay không. | **Wrapper → workflow moat + logic Vertical AI.** ChatGPT vẫn là horizontal product, nhưng ngày càng đi theo công thức AI Expert + Domain/Company Context. Moat chuyển dần sang context + workflow + execution. |

## Chuỗi quyết định tôi đọc được từ timeline

Nhìn toàn bộ timeline, tôi không cho rằng ChatGPT phát triển theo kiểu thêm ngày càng nhiều feature độc lập. Có một chuỗi khá nhất quán:

**Chat → Model tốt hơn → Customization → Multimodal → Search → Research → Action → Finished Work**

Đơn vị giá trị của sản phẩm liên tục tăng lên.

- Năm 2022, giá trị chủ yếu là **một câu trả lời hữu ích**.
- Đến 2024, giá trị trở thành **một cuộc tương tác tự nhiên hơn và có thông tin thời sự**.
- Đến 2025, ChatGPT bắt đầu chịu trách nhiệm cho **một chuỗi công việc nhiều bước**.
- Đến 2026, ChatGPT Work được định vị theo hướng biến một goal thành **finished work** thay vì chỉ tạo response. [Nguồn](https://openai.com/index/chatgpt-for-your-most-ambitious-work/)

Theo tôi, đây là quyết định chiến lược quan trọng nhất xuyên suốt sản phẩm: **ChatGPT đang di chuyển lên cao dần trong value chain của người dùng.**

## Vì sao tôi chọn những mốc này?

Tôi chọn 8 mốc trên vì mỗi mốc làm thay đổi ít nhất một trong ba yếu tố:

1. **Khả năng cốt lõi** mà ChatGPT có thể đảm nhận.
2. **Cách người dùng tương tác** với sản phẩm.
3. **Phạm vi workflow** mà user có thể giao cho AI.

Tôi đã cân nhắc đưa **Operator — 23/01/2025** thành một milestone riêng. Operator là research preview của một agent có thể sử dụng browser để click, type và scroll trên web. Tuy nhiên, đến 17/07/2025 OpenAI đã tích hợp Operator vào ChatGPT Agent. Vì vậy, tôi loại Operator khỏi bảng cuối để tránh hai hàng phản ánh gần cùng một hướng quyết định sản phẩm. [Nguồn](https://openai.com/index/introducing-operator/)

Tôi cũng không chọn các lần đổi UI, tăng rate limit hoặc các update nhỏ về model làm milestone vì đó chủ yếu là **optimization**, chưa đủ làm thay đổi đáng kể JTBD hoặc vị trí của ChatGPT trong workflow người dùng.

---

# §2. Tệp user & JTBD

## 2.1. So sánh Early Adopters và tệp hiện tại

| | Early adopters | Tệp hiện tại |
|---|---|---|
| **Đặc điểm** | Developer junior, sinh viên kỹ thuật và knowledge worker thích thử công nghệ mới; đã quen với Google, Stack Overflow, documentation và các công cụ số; sẵn sàng kiểm tra lại output của AI. | Knowledge worker và team làm việc thực tế như marketing, operations, finance, sales, analyst và engineering; cần AI làm việc với file, app, tài liệu, dữ liệu công ty và các workflow nhiều bước. |
| **JTBD chính** | “Khi tôi gặp một vấn đề chưa biết cách xử lý, tôi muốn AI giải thích, brainstorm hoặc tạo bản nháp ngay để tôi không phải mất nhiều thời gian tìm kiếm và ghép thông tin thủ công.” | “Khi tôi có một nhiệm vụ dài gồm nhiều nguồn và nhiều bước, tôi muốn giao cho AI thu thập context, phân tích và tạo đầu ra có thể review để tôi tập trung vào judgement và quyết định.” |
| **Trước đó họ làm bằng cách nào** | Google → mở nhiều link → Stack Overflow/documentation → copy/paste → tự tổng hợp → viết bản nháp. | Chuyển qua lại giữa email, Slack, Drive, docs, spreadsheet, browser và project tracker rồi tự tổng hợp thành report/deck/document. |
| **Điều họ chấp nhận đánh đổi** | Chấp nhận hallucination và trải nghiệm chưa ổn định vì lợi ích về tốc độ đủ lớn. | Yêu cầu cao hơn về reliability, provenance, permissions, privacy, governance và khả năng kiểm soát hành động của agent. |
| **Cột mốc thúc đẩy dịch chuyển** | Launch 2022 và GPT-4 2023 tạo giá trị ban đầu cho hỏi–đáp, code, học tập và drafting. | Search → Deep Research → Agent → Company Knowledge → Work biến ChatGPT từ chatbot thành công cụ xử lý workflow. |

## 2.2. Early adopters cụ thể là ai?

Tôi chọn một persona cụ thể:

> **Một developer junior tại startup nhỏ, đã sử dụng VS Code, Google, Stack Overflow và documentation hằng ngày; theo dõi xu hướng AI và sẵn sàng kiểm tra lại output của model.**

### JTBD của persona này

**Khi** gặp code lỗi hoặc một khái niệm kỹ thuật chưa hiểu,  
**tôi muốn** có một công cụ giải thích vấn đề và đề xuất hướng xử lý ngay trong cùng cuộc hội thoại,  
**để** tôi tiếp tục công việc mà không cần mở và đọc hàng loạt kết quả tìm kiếm.

ChatGPT phù hợp với early adopter này vì giá trị ban đầu rất rõ: giao diện hội thoại đơn giản, có thể hỏi tiếp, sửa code và giải thích kiến thức; đồng thời research preview ban đầu được mở miễn phí để thu feedback. [Nguồn](https://openai.com/index/chatgpt/)

---

## 2.3. Tệp user hiện tại cụ thể

Persona tôi chọn cho giai đoạn hiện tại là:

> **Một marketing hoặc operations executive trong công ty nhỏ hoặc vừa, phải research thị trường, đọc tài liệu, tổng hợp dữ liệu, viết brief/report/deck và phối hợp thông tin từ nhiều công cụ nhưng không có một analyst riêng cho từng nhiệm vụ.**

### JTBD của persona này

**Khi** tôi có một nhiệm vụ cần thu thập dữ liệu từ nhiều nguồn và tạo thành một tài liệu có thể sử dụng,  
**tôi muốn** giao phần tìm kiếm, tổng hợp và tạo first draft cho AI,  
**để** tôi dành thời gian cho việc kiểm chứng, judgement và ra quyết định thay vì xử lý thủ công từng bước.

ChatGPT Work hiện được thiết kế để lấy thông tin từ apps và workflow, sau đó tạo ra finished materials như sheets, slides, docs và web apps. [Nguồn](https://openai.com/index/chatgpt-for-your-most-ambitious-work/)

---

## 2.4. Dịch chuyển tệp user

Theo tôi, không có một milestone duy nhất gây ra sự dịch chuyển này. Đây là một chuỗi:

**Search (2024) → Deep Research (2025) → Agent (2025) → Company Knowledge (2025) → Work (2026)**

- **Search** giảm nhu cầu rời ChatGPT để lấy thông tin mới. [Nguồn](https://openai.com/index/introducing-chatgpt-search/)
- **Deep Research** cho phép user giao một nhiệm vụ nghiên cứu nhiều bước. [Nguồn](https://openai.com/index/introducing-deep-research/)
- **Agent** cho phép AI không chỉ đọc mà còn hành động bằng computer và tool. [Nguồn](https://openai.com/index/introducing-chatgpt-agent/)
- **Company Knowledge** đưa context từ các connected tools như Slack, SharePoint, Google Drive và GitHub vào ChatGPT. [Nguồn](https://openai.com/index/introducing-company-knowledge/)
- **Work** nâng đơn vị đầu ra từ answer sang finished work. [Nguồn](https://openai.com/index/chatgpt-for-your-most-ambitious-work/)

Điều này làm tệp khách hàng tiềm năng dịch từ **người muốn AI hỗ trợ một task nhỏ** sang **người hoặc team muốn delegate một phần workflow**.

---

## 2.5. Switching Cost — phân tích theo 4 Forces

### Force 1 — Push: điều gì đẩy user khỏi cách làm cũ?

Cách làm cũ của knowledge worker thường bị phân mảnh:

**Search → Docs → Email → Spreadsheet → Slack → Browser → Report**

User phải tự làm nhiều việc có giá trị thấp:

- tìm tài liệu;
- copy dữ liệu;
- chuyển giữa nhiều app;
- đọc nhiều nguồn;
- tổng hợp lại;
- định dạng thành báo cáo hoặc slide.

Đây là “push” khiến user muốn thử một sản phẩm có thể gom nhiều bước thành một workflow.

---

### Force 2 — Pull: điều gì kéo user sang ChatGPT?

Pull của ChatGPT ngày càng không chỉ là “model thông minh”.

Nó gồm:

- natural-language interaction;
- web search;
- deep research;
- file/context;
- connected apps;
- tool/browser execution;
- company knowledge;
- workspace workflow;
- khả năng tạo finished materials.

ChatGPT Work được định vị để thu thập thông tin từ apps và workflow, thực hiện project trong nhiều giờ và tạo output hoàn chỉnh. [Nguồn](https://openai.com/index/chatgpt-for-your-most-ambitious-work/)

Điều này làm **product-level pull** mạnh hơn **model-level pull**.

---

### Force 3 — Habit: điều gì khiến user vẫn ở lại cách cũ?

Đây là lực mạnh vì người dùng đã quen:

- Google để search;
- Microsoft Office hoặc Google Workspace để tạo tài liệu;
- Slack hoặc Teams để giao tiếp;
- spreadsheet để phân tích;
- browser để thao tác;
- workflow nội bộ của công ty.

Một AI tốt hơn chưa chắc đủ để user bỏ toàn bộ thói quen này.

Vì vậy, thay vì yêu cầu user bỏ các tool cũ, hướng đi của ChatGPT là **kết nối vào chúng**.

Company Knowledge là một ví dụ: OpenAI gom context từ các connected apps như Slack, SharePoint, Google Drive và GitHub vào cùng một lớp hội thoại. [Nguồn](https://openai.com/index/introducing-company-knowledge/)

Theo tôi, đây là một quyết định product quan trọng: ChatGPT không nhất thiết phải thay thế toàn bộ Google Drive, Slack hay GitHub; nó có thể trở thành **orchestration layer nằm phía trên chúng**.

---

### Force 4 — Anxiety: điều gì khiến user ngại chuyển?

Khi ChatGPT chỉ viết text, một câu sai thường dễ sửa.

Khi AI có quyền:

- truy cập dữ liệu công ty;
- dùng browser;
- thao tác website;
- chạy code;
- tạo spreadsheet hoặc slide;
- thực hiện workflow;

thì hậu quả của lỗi có thể lớn hơn.

Các anxiety chính gồm:

- hallucination;
- dùng sai nguồn;
- privacy;
- quyền truy cập dữ liệu;
- agent thực hiện nhầm hành động;
- governance trong doanh nghiệp;
- khó biết AI đã làm gì.

ChatGPT Agent System Card cho thấy agent kết hợp Deep Research, Operator, terminal và external applications, đồng thời OpenAI phải bổ sung thêm safeguards vì quyền hành động cao hơn cũng kéo theo rủi ro mới. [Nguồn](https://openai.com/index/chatgpt-agent-system-card/)

---

## 2.6. Lực nào đang giữ user mạnh nhất?

Theo tôi, lực giữ user ngày càng mạnh nhất không phải chỉ là **habit với giao diện ChatGPT**, mà là **workflow + context tích lũy**.

Một user có thể dễ chuyển giữa hai chatbot nếu cả hai chỉ nhận một prompt và trả text.

Nhưng switching cost tăng khi trong hệ thống đã có:

- conversation history;
- file;
- company context;
- connected apps;
- workflow;
- agent;
- scheduled tasks.

Khi đó, chuyển sản phẩm không chỉ là đổi model mà còn có thể đồng nghĩa với việc **rebuild context và workflow**.

Nếu layer context/workflow này biến mất và đối thủ có model tương đương, moat của ChatGPT sẽ yếu đi đáng kể. Vì vậy tôi cho rằng moat dài hạn phải nằm trên model.

---

# §3. Ba dự đoán hướng đi trong 6–12 tháng tới

**Khung thời gian dự đoán:** khoảng **04/2027 đến 10/2027**.

Các nội dung dưới đây là **phán đoán của tôi dựa trên dữ liệu đã phân tích**, không phải thông tin OpenAI đã công bố chắc chắn.

---

## Dự đoán 1 — Workflow agent sẽ trở nên chủ động và dài hơn, không chỉ dừng ở scheduled/webhook tasks

**Loại:** Mở rộng tính năng

- **Dự đoán:** Trong 6–12 tháng tới, ChatGPT Work và workspace agents sẽ mở rộng từ các scheduled/webhook-triggered workflow hiện tại sang các workflow dài hơn có khả năng tự theo dõi trạng thái, phối hợp nhiều nguồn và chỉ yêu cầu con người can thiệp tại các checkpoint quan trọng.
- **Lập luận:** §1 cho thấy progression nhất quán từ Search → Deep Research → Agent → Work. Mỗi bước giảm thêm lượng thao tác user phải tự thực hiện. Đến tháng 08/2026, ChatGPT Business đã có scheduled tasks và webhook-triggered tasks từ các sự kiện như Gmail message, Slack message và GitHub pull request. [Nguồn](https://help.openai.com/en/articles/11391654-chatgpt-business-release-notes) Vì vậy bước tiếp theo hợp lý không phải là “có scheduling”, vì scheduling đã tồn tại, mà là **tăng mức tự chủ và độ dài của workflow**.

**Giả định có thể làm dự đoán này sai:** reliability không cải thiện đủ nhanh. Nếu agent vẫn cần user kiểm tra gần như từng bước, mức autonomy sẽ tăng chậm hơn.

---

## Dự đoán 2 — ChatGPT sẽ “verticalize” ở cấp doanh nghiệp bằng company context, skills và workspace agents

**Loại:** Mở rộng segment / Vertical AI

- **Dự đoán:** ChatGPT có khả năng tiếp tục cho doanh nghiệp tạo các agent chuyên biệt theo từng phòng ban hoặc nghiệp vụ như financial reporting, sales operations, internal research, recruiting hoặc customer support, thay vì OpenAI tự xây một sản phẩm riêng cho mọi ngành.
- **Lập luận:** GPTs năm 2023 đã thử nghiệm việc để user đóng gói instructions và knowledge. [Nguồn](https://openai.com/index/introducing-gpts/) Company Knowledge sau đó đưa context doanh nghiệp từ các connected apps vào ChatGPT. [Nguồn](https://openai.com/index/introducing-company-knowledge/) Đến 2026, ChatGPT Business đã có workspace agents cho customized workflows. [Nguồn](https://openai.com/business/pricing/) Pattern này gần với nguyên lý **Vertical AI = AI Expert + Domain Expert**, nhưng domain expertise có thể được tổ chức đưa vào hệ thống thay vì OpenAI tự xây từng vertical.

**Giả định có thể làm dự đoán này sai:** privacy, compliance hoặc governance khiến doanh nghiệp không sẵn sàng đưa đủ context vào hệ thống.

---

## Dự đoán 3 — Usage/credits sẽ đóng vai trò lớn hơn trong pricing của workload agentic và compute-intensive

**Loại:** Thay đổi mô hình kiếm tiền

- **Dự đoán:** Trong 6–12 tháng tới, OpenAI có khả năng tiếp tục tăng vai trò của usage limits và credits trong pricing cho các workload agentic hoặc compute-intensive, thay vì để toàn bộ giá trị nằm trong một mức subscription cố định.
- **Lập luận:** Pricing hiện tại của ChatGPT Business đã chia Standard và Premium seat với mức usage khác nhau. [Nguồn](https://openai.com/business/pricing/) Ngoài ra, OpenAI đã có flexible pricing trong đó credits cho phép user tiếp tục sử dụng các advanced features khi vượt usage được bao gồm trong seat. [Nguồn](https://help.openai.com/en/articles/11487671-flexible-pricing-for-the-enterprise-edu-and-business-plans) Khi sản phẩm chuyển từ tạo response ngắn sang Deep Research, Codex, Work và agentic workflow kéo dài, chi phí compute và giá trị kinh tế của từng task khác nhau đáng kể. Do đó, mô hình pricing có khả năng tiếp tục phản ánh mức sử dụng thực tế nhiều hơn.

**Giả định có thể làm dự đoán này sai:** khách hàng doanh nghiệp thích pricing cố định và predictable đến mức OpenAI ưu tiên giữ mô hình seat-based đơn giản hơn.

---

## Dự đoán tôi tự tin nhất

Tôi tự tin nhất với **Dự đoán 1 — workflow agent sẽ trở nên chủ động và dài hơn**.

Lý do là đây không phải một thay đổi hướng hoàn toàn mới mà là continuation của pattern đã xuất hiện liên tục:

**Answer → Search → Research → Action → Work**

Từ timeline, mỗi generation đều lấy thêm một phần công việc mà trước đó user phải tự thực hiện.

Đến 2026, scheduled và webhook-triggered tasks đã tồn tại, nên câu hỏi tiếp theo không còn là “AI có thể bắt đầu task tự động không?” mà là:

> “AI có thể giữ được context, theo dõi trạng thái và tự xử lý bao nhiêu phần của workflow trước khi phải gọi người dùng quay lại?”

Giả định có thể làm dự đoán này gãy là **reliability**. Nếu AI vẫn mắc lỗi quá thường xuyên trong workflow dài, user sẽ tiếp tục dùng agent như copilot có supervision cao thay vì giao outcome.

---

# §4. AI Log

| Việc | AI làm hay bạn làm? | Bạn kiểm chứng/phán đoán lại thế nào? |
|---|---|---|
| Giải thích đề bài và rubric | **AI hỗ trợ** | Tôi đọc lại yêu cầu gốc và xác nhận memo phải có đủ Timeline, User/JTBD, 3 Predictions và AI Log. |
| Đề xuất sản phẩm để teardown | **AI gợi ý, tôi quyết định** | AI so sánh một số lựa chọn. Tôi chọn ChatGPT vì thỏa 3 tiêu chí của đề: AI là core product, có đủ dữ liệu công khai cho ≥6 milestone và JTBD xác định được. |
| Thu thập milestone ứng viên | **AI hỗ trợ research** | Tôi kiểm tra lại ngày, tên feature và mô tả trên nguồn OpenAI chính thức. |
| Chọn 8 milestone cuối cùng | **AI hỗ trợ, tôi phán đoán** | Tôi chỉ giữ các mốc làm thay đổi capability, interaction hoặc phạm vi workflow; loại các update nhỏ. |
| Loại Operator khỏi timeline cuối | **AI hỗ trợ kiểm tra** | Tôi mở nguồn Operator và ChatGPT Agent, xác nhận Operator sau đó được tích hợp vào ChatGPT Agent nên không cần giữ thành hai milestone riêng. |
| Viết context từng milestone | **AI hỗ trợ tổng hợp** | Tôi kiểm tra context phải trả lời “vì sao nước đi này có ý nghĩa ở thời điểm đó”, không chỉ kể lại changelog. |
| Revert milestone về nguyên lý | **AI hỗ trợ brainstorm, tôi chọn framework** | Tôi map lại từng mốc vào x10, learning loop, wrapper/moat, Vertical AI hoặc definition of good; tránh các nhãn chung chung như “để tăng trưởng”. |
| Xác định early adopter và user hiện tại | **AI hỗ trợ brainstorm, tôi phán đoán** | Tôi cụ thể hóa thành persona có hành vi và workflow rõ thay vì các nhóm chung như “giới trẻ” hoặc “dân văn phòng”. |
| Viết JTBD | **AI hỗ trợ cấu trúc** | Tôi kiểm tra từng JTBD phải mô tả việc cần làm và outcome, không viết thành feature như “user cần chatbot AI”. |
| Phân tích 4 Forces | **AI hỗ trợ framework** | Tôi tự map Push, Pull, Habit và Anxiety vào workflow của persona đã chọn. |
| Tạo 3 prediction | **AI brainstorm + tôi phán đoán** | Tôi chỉ giữ prediction dẫn ngược được về §1 và §2. Tôi sửa prediction về scheduled tasks sau khi kiểm tra và phát hiện tính năng này đã tồn tại trong 2026. |
| Kiểm tra pricing prediction | **AI hỗ trợ research** | Tôi kiểm tra pricing hiện tại và flexible credits, sau đó giảm mức khẳng định để phân biệt fact hiện tại với phán đoán tương lai. |
| Kiểm chứng citation | **AI hỗ trợ tìm nguồn** | Tôi mở lại các nguồn OpenAI gốc và kiểm tra link có thực sự chứng minh claim được đặt cạnh nó. |
| Hoàn thiện memo | **AI hỗ trợ biên tập** | Tôi đọc lại chuỗi logic Timeline → User/JTBD → Prediction và kiểm tra checklist trước khi nộp. |

---

# Kết luận

Qua teardown này, điều tôi học được không phải là ChatGPT đã có bao nhiêu tính năng mà là **chuỗi logic trong các quyết định sản phẩm**.

ChatGPT bắt đầu bằng việc giảm rào cản để người bình thường có thể sử dụng LLM qua giao diện hội thoại. Sau đó sản phẩm liên tục di chuyển lên một tầng giá trị cao hơn:

**trả lời tốt hơn → tương tác tự nhiên hơn → truy cập thông tin mới → tự nghiên cứu → hành động → hoàn thành workflow**

Điều này cũng làm moat thay đổi.

Ở giai đoạn đầu, lợi thế phần lớn nằm ở model. Khi các model trên thị trường ngày càng mạnh, moat cần dịch sang những thứ khó bị hấp thụ hơn:

- user context;
- company data;
- integrations;
- workflow;
- ecosystem;
- khả năng thực thi đáng tin cậy.

Từ góc nhìn JTBD, ChatGPT cũng đang chuyển từ một sản phẩm mà user **“thuê để giúp mình nghĩ hoặc viết”** sang một sản phẩm mà user có thể **“thuê để thực hiện một phần công việc”**.

Theo tôi, khả năng ChatGPT tiếp tục mở rộng phụ thuộc lớn vào việc OpenAI giải quyết được tension giữa **autonomy** và **trust**:

> Agent càng có khả năng hành động nhiều thì giá trị càng lớn, nhưng yêu cầu về reliability, permissions, provenance và user control cũng tăng tương ứng.

---

# Checklist trước khi nộp

- [x] Có 8 milestone, nằm trong yêu cầu 6–8 mốc.
- [x] Mỗi milestone là một quyết định sản phẩm lớn.
- [x] Mỗi milestone có link nguồn gốc.
- [x] Mỗi milestone được revert về nguyên lý có tên.
- [x] Có giải thích milestone đã cân nhắc nhưng loại.
- [x] Early adopter được mô tả cụ thể.
- [x] User hiện tại được mô tả cụ thể.
- [x] JTBD viết theo việc cần làm, không theo feature.
- [x] Segment shift nối ngược về §1.
- [x] Switching cost map đủ Push / Pull / Habit / Anxiety.
- [x] Có đúng 3 dự đoán 6–12 tháng tới.
- [x] Mỗi prediction dẫn ngược về timeline hoặc user/JTBD.
- [x] Prediction không nhầm một feature đã tồn tại thành tương lai.
- [x] Fact và phán đoán được phân biệt rõ.
- [x] AI Log có ít nhất 3 hàng và khai rõ AI hỗ trợ phần nào.
- [x] Memo đủ 4 phần theo template.
