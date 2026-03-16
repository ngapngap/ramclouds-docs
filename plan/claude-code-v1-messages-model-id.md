# Plan: Claude Code + `v1/messages` model ID normalization

## Tóm tắt mục tiêu
Chuẩn bị đặc tả thay đổi tài liệu để chuẩn hóa lưu ý sử dụng model Claude khi gọi endpoint `v1/messages`: **không dùng hậu tố `-CL` trong model ID**. Mục tiêu là thống nhất hướng dẫn xuyên suốt docs để giảm lỗi tích hợp do cấu hình sai endpoint/model.

## Checklist subtask (planning/spec only)

- [x] Subtask 1 — Chuẩn hóa thông điệp gốc ở tài liệu tổng quan chính
  - Mục tiêu: cập nhật mô tả trung tâm về mapping endpoint/model cho Claude Code với rule `v1/messages` => model Claude không có `-CL`.
  - File dự kiến tác động (2):
    - `README.md`
    - `docs/README.md`
  - Ghi chú hoàn tất: đã bổ sung quy tắc theo endpoint `v1/messages`, ví dụ đúng/sai, phạm vi áp dụng, và cảnh báo validation đầu vào theo endpoint.

- [x] Subtask 2 — Chuẩn hóa quickstart cho đường đi triển khai nhanh
  - Mục tiêu: bổ sung lưu ý ngắn, rõ, dễ scan cho luồng bắt đầu nhanh; nhấn mạnh model ID đúng/sai khi dùng `v1/messages`.
  - File dự kiến tác động (1):
    - `docs/guide/quickstart.md`
  - Ghi chú hoàn tất: đã thêm lưu ý nổi bật cho `v1/messages` với ví dụ model đúng/sai và cảnh báo rủi ro cấu hình endpoint/model.

- [x] Subtask 3 — Chuẩn hóa phần API model catalog và API overview
  - Mục tiêu: đồng bộ quy tắc đặt model ID trong phần API, tránh mâu thuẫn giữa tài liệu model list và hướng dẫn endpoint.
  - File dự kiến tác động (2):
    - `docs/api/models.md`
    - `docs/api/overview.md`
  - Ghi chú hoàn tất (adjusted): đã thêm rule `v1/messages` dùng model Claude không `-CL`, ví dụ đúng/sai, phạm vi áp dụng theo endpoint, và cảnh báo mismatch endpoint/model + khuyến nghị validation theo endpoint; đã điều chỉnh model ID ví dụ sang `claude-sonnet-4-5` / `claude-sonnet-4-5-CL` để đồng bộ với quyết định chuẩn hóa mới.

- [x] Subtask 4 — Chuẩn hóa hướng dẫn tích hợp IDE
  - Mục tiêu: cập nhật lưu ý cấu hình trong tích hợp IDE để tránh người dùng giữ thói quen thêm `-CL` khi chuyển sang `v1/messages`.
  - File dự kiến tác động (1):
    - `docs/integrations/ide.md`
  - Ghi chú hoàn tất (adjusted): đã thêm mục lưu ý cho `v1/messages`, ví dụ đúng/sai, thao tác cấu hình tránh nhập nhầm `-CL`, và security note mức tài liệu; đã điều chỉnh model ID ví dụ sang `claude-sonnet-4-5` / `claude-sonnet-4-5-CL` để đồng bộ chuẩn.

- [x] Subtask 5 — Rà soát nhất quán và liên kết chéo cảnh báo
  - Mục tiêu: đảm bảo thông điệp nhất quán toàn bộ nhóm file ưu tiên, không còn hướng dẫn xung đột về hậu tố model.
  - File dự kiến tác động (3):
    - `docs/api/models.md`
    - `docs/api/overview.md`
    - `docs/guide/quickstart.md`
  - Ghi chú hoàn tất (adjusted): thông điệp đã đồng bộ theo endpoint `v1/messages` trên nhóm file ưu tiên, thống nhất ví dụ đúng/sai và cảnh báo validation cấu hình; sau rà soát phát hiện lệch model ID ví dụ và đã đồng bộ lại theo model chuẩn `claude-sonnet-4-5`.

- [x] Subtask 6 — Đồng bộ model ID ví dụ sau vòng review (follow-up adjustment)
  - Mục tiêu: xử lý lệch model ID ví dụ phát hiện sau khi các mục review đã đánh dấu xong, bảo đảm tài liệu cùng dùng một model chuẩn cho rule `v1/messages`.
  - File đã tác động (4):
    - `docs/api/models.md`
    - `docs/api/overview.md`
    - `docs/integrations/ide.md`
    - `plan/claude-code-v1-messages-model-id.md`
  - Ghi chú hoàn tất: đã chuẩn hóa ví dụ `v1/messages` theo một cặp duy nhất — đúng: `claude-sonnet-4-5`, sai: `claude-sonnet-4-5-CL`; giữ nguyên thông điệp phạm vi endpoint và security note.

## Security Assessment (Docs-level)

### Rủi ro chính
- Cấu hình sai cặp endpoint/model (ví dụ dùng `v1/messages` nhưng model vẫn có hậu tố `-CL`) có thể gây lỗi tích hợp, request fail, hoặc hành vi khó chẩn đoán trong môi trường production.
- Tài liệu không nhất quán giữa các trang có thể làm đội vận hành copy cấu hình sai sang nhiều hệ thống, tăng rủi ro incident do cấu hình lặp lại.

### Hardening khuyến nghị ở mức tài liệu
- Thêm quy tắc validation rõ ràng theo ngữ cảnh endpoint:
  - Nếu endpoint là `v1/messages` => model Claude **không** có hậu tố `-CL`.
- Bổ sung ví dụ đúng/sai (good/bad examples) sát ngữ cảnh cấu hình thực tế.
- Đặt cảnh báo nổi bật tại các điểm dễ copy-paste (quickstart, API overview, integration guide).
- Dùng ngôn ngữ cảnh báo nhất quán và liên kết chéo tới một nguồn giải thích chuẩn để giảm drift tài liệu.

## Phase 2026-03 — Đồng bộ Claude 4-6 + OpenCode/AmpCode

> Mục tiêu phase mới: mở rộng plan hiện có để phản ánh yêu cầu cập nhật model thế hệ mới và bổ sung hướng dẫn cấu hình OpenCode/AmpCode, **không rewrite lịch sử phase cũ**.

### Quyết định bổ sung cho phase này
- Đồng bộ toàn bộ docs: mọi tham chiếu model Claude `4-5` chuyển sang `4-6` theo ngữ cảnh tương ứng.
- OpenCode:
  - Nếu dùng chuẩn Claude thì dùng `@ai-sdk/anthropic` + model `claude-opus-4.6` (không dùng hậu tố `-CL`).
  - Nếu dùng `@ai-sdk/openai-compatible` thì dùng model có hậu tố `-CL`.
- AmpCode:
  - **Correction bắt buộc**: AmpCode chỉ hỗ trợ cấu hình qua proxy server; không hỗ trợ gọi thẳng provider.
  - Bổ sung cấu hình có nhắc repo tham chiếu: `https://github.com/fdkgenie/9router`.
  - Nhấn mạnh ưu điểm cấu hình nhanh qua một endpoint proxy `http://localhost:20128/v1`.
  - Loại bỏ mọi mô tả/suy diễn về phương án gọi thẳng provider trong docs.
  - Nêu rõ lợi điểm: đã thêm RamClouds làm provider thông qua lớp proxy.

### Checklist subtask triển khai (new wave)

- [x] Subtask 7 — Đồng bộ model Claude 4-6 trên nhóm tài liệu ưu tiên
  - Mục tiêu: thay thế mọi ví dụ/diễn giải model Claude `4-5` sang `4-6` để tránh lệch version trong docs.
  - File dự kiến tác động (3):
    - `README.md`
    - `docs/README.md`
    - `docs/api/models.md`
  - Acceptance criteria:
    - Không còn chuỗi model Claude `4-5` trong 3 file trên (trừ phần lịch sử/changelog nếu có ghi chú cố ý).
    - Ví dụ model chính dùng nhất quán theo chuẩn `4-6`.
    - Quy tắc endpoint/model đang có (bao gồm rule `-CL`) không bị mâu thuẫn sau khi đổi version.
  - Ghi chú hoàn tất (adjusted): trong wave này chỉ chỉnh trong phạm vi 4 file được yêu cầu; đã chuẩn hóa `docs/api/models.md` sang `4.6` và giữ lịch sử các file ngoài phạm vi.

- [x] Subtask 8 — Bổ sung phần cấu hình OpenCode theo 2 nhánh SDK
  - Mục tiêu: thêm hướng dẫn rõ ràng cho OpenCode theo hai lựa chọn triển khai để tránh nhầm model suffix.
  - File dự kiến tác động (2):
    - `docs/guide/quickstart.md`
    - `docs/api/overview.md`
  - Acceptance criteria:
    - Có mục riêng cho `@ai-sdk/anthropic` với ví dụ model `claude-opus-4.6` (không `-CL`).
    - Có mục riêng cho `@ai-sdk/openai-compatible` với ví dụ model có hậu tố `-CL`.
    - Có ghi chú “khi nào dùng nhánh nào” và ví dụ đúng/sai để giảm copy-paste sai.
  - Ghi chú hoàn tất (adjusted): theo ràng buộc subtask hiện tại, nội dung OpenCode được bổ sung tại `docs/integrations/ide.md`; `docs/api/overview.md` đã đồng bộ rule suffix và ví dụ đúng/sai theo `claude-opus-4.6`.

- [x] Subtask 9 — Bổ sung phần AmpCode + tham chiếu 9Router + bảng so sánh trực tiếp
  - Mục tiêu: mô tả cách cấu hình AmpCode nhanh qua 9Router và đối chiếu rõ với cấu hình gọi thẳng.
  - File dự kiến tác động (2):
    - `docs/integrations/ide.md`
    - `docs/api/overview.md`
  - Acceptance criteria:
    - Có nhắc rõ repo `https://github.com/fdkgenie/9router` trong phần AmpCode.
    - Có mô tả ưu điểm cấu hình nhanh qua `http://localhost:20128/v1` (set một lần).
    - Có bảng so sánh trực tiếp “cấu hình thẳng” vs “qua 9Router” với tiêu chí tối thiểu: endpoint, model suffix, độ phức tạp cấu hình, khả năng mở rộng provider.
    - Có ghi chú lợi điểm “RamClouds đã được thêm làm provider”.
  - Ghi chú hoàn tất (adjusted): đã triển khai đầy đủ ở `docs/integrations/ide.md`; giữ nguyên lịch sử kế hoạch cũ và không mở rộng sang file ngoài phạm vi.

- [x] Subtask 10 — Rà soát nhất quán liên trang + liên kết chéo cho nhánh OpenCode/AmpCode
  - Mục tiêu: đảm bảo thông điệp không xung đột giữa quickstart, API overview, integrations.
  - File dự kiến tác động (3):
    - `docs/guide/quickstart.md`
    - `docs/api/overview.md`
    - `docs/integrations/ide.md`
  - Acceptance criteria:
    - Mapping SDK/endpoint/model suffix giống nhau trên cả 3 file.
    - Các section mới có liên kết chéo về nguồn giải thích chuẩn để giảm drift.
    - Không còn ví dụ vừa dùng endpoint chuẩn Claude vừa gắn model `-CL` sai ngữ cảnh.
  - Ghi chú hoàn tất (adjusted): trong phạm vi được phép, mapping Claude-native/OpenAI-compatible và rule `-CL` đã đồng bộ trên `docs/api/overview.md` + `docs/integrations/ide.md`; không chỉnh `docs/guide/quickstart.md` theo ràng buộc phạm vi.

- [x] Subtask 11 — Cập nhật lại plan nguồn sự thật sau vòng chỉnh docs
  - Mục tiêu: phản ánh trạng thái thực thi thật vào plan để orchestrator có thể bám theo.
  - File dự kiến tác động (1):
    - `plan/claude-code-v1-messages-model-id.md`
  - Acceptance criteria:
    - Từng subtask 7-10 được đánh dấu trạng thái đúng với kết quả thực tế.
    - Mọi thay đổi phạm vi/decision phát sinh được ghi bổ sung thay vì ghi đè lịch sử.
  - Ghi chú hoàn tất: đã cập nhật trạng thái DONE/adjusted cho subtask 7-10 và lưu rõ giới hạn phạm vi 4 file của wave hiện tại.

## Security Assessment bổ sung cho phase mới (Docs-level)

### Rủi ro trọng yếu cần nêu trong tài liệu cấu hình mới
- Rủi ro lộ API key:
  - Copy key trực tiếp vào ví dụ docs, commit vào repo, hoặc dán vào config chia sẻ nội bộ.
- Rủi ro endpoint giả mạo/sai nguồn:
  - Người dùng cấu hình endpoint không tin cậy (đặc biệt khi dùng OpenAI-compatible/Router), dẫn đến gửi request + credential tới đích không mong muốn.
- Rủi ro nhầm lẫn model suffix:
  - Dùng model `-CL` cho nhánh chuẩn Claude hoặc ngược lại, gây lỗi request, fallback sai, hoặc khó điều tra sự cố.

### Checklist security follow-up trong phạm vi docs
- [x] Thêm cảnh báo “không hardcode key” + khuyến nghị dùng biến môi trường tại các section cấu hình mới.
- [x] Thêm lưu ý xác thực endpoint tin cậy trước khi cấu hình (hostname/port/protocol expected).
- [x] Thêm bảng quy tắc model suffix theo từng nhánh SDK để giảm nhầm lẫn vận hành.
- [x] Thêm mục “Security follow-up: review/approve” cho các thay đổi security-sensitive nếu cần điều chỉnh lớn ngoài phạm vi docs.
  - Trạng thái review/approve: docs-only change, không thay đổi kiến trúc hay luồng bảo mật runtime.

## Correction / Errata khẩn — AmpCode proxy-only

### Sai sót đã xác nhận
- Sai sót trước đó: tài liệu có nội dung gợi ý AmpCode có thể cấu hình gọi thẳng provider.
- Correction chính thức: **AmpCode bắt buộc đi qua proxy server**; không có luồng cấu hình direct-provider hợp lệ.

### Checklist subtask docs follow-up (phạm vi 1-2 file)
- [x] Subtask 12 — Sửa mô tả AmpCode về proxy-only trong integration guide
  - Mục tiêu: chỉnh mô tả AmpCode để khẳng định bắt buộc proxy-only, loại bỏ mọi câu chữ gợi ý direct-provider.
  - File dự kiến tác động (ưu tiên 1, tối đa 2):
    - `docs/integrations/ide.md`
    - `README.md` (chỉ note ngắn nếu cần liên kết chéo)
  - Acceptance criteria:
    - Mọi mô tả AmpCode khẳng định proxy-only, có ví dụ endpoint qua proxy (ví dụ `http://localhost:20128/v1`).
    - Không còn hướng dẫn hoặc ví dụ cấu hình gọi thẳng provider cho AmpCode.
    - Nếu có cập nhật `README.md`, chỉ thêm note ngắn điều hướng, không mở rộng nội dung ngoài correction.
  - Ghi chú hoàn tất (adjusted): đã cập nhật `docs/integrations/ide.md` theo proxy-only, thay bảng so sánh để loại bỏ nhánh direct-provider, giữ endpoint `http://localhost:20128/v1`, giữ lợi điểm RamClouds qua proxy layer, và bổ sung security note; không chỉnh `README.md` theo ràng buộc phạm vi subtask hiện tại.

### Security note (docs-level, ngắn)
- Chỉ dùng endpoint proxy tin cậy nội bộ cho cấu hình AmpCode.
- API key/provider secret phải được bảo vệ tại proxy layer; không mô tả phương án đưa key provider trực tiếp vào AmpCode client.
