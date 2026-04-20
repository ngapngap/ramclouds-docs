# IDE Integrations

Trang này là overview cho toàn bộ tài liệu tích hợp IDE/tool với Ramclouds API.

## Tổng quan nhanh về model và endpoint

Quy tắc quan trọng nhất là không trộn model suffix giữa hai luồng:

- **Claude-native (`v1/messages`)**: model Claude **không có `-CL`**.
  - Ví dụ đúng: `claude-opus-4.6`
- **OpenAI-compatible (`/v1`)**: model Claude **có `-CL`**.
  - Ví dụ đúng: `claude-opus-4.6-CL`

> Security note: không commit API key vào repo; ưu tiên biến môi trường. Khi dùng localhost/proxy, luôn xác minh đúng tiến trình đang lắng nghe trước khi nhập credential.

## Danh sách integrations

### IDE & Coding Assistants

- [Claude Code](claude-code.md)
- [Roo Code](roo-code.md)
- [OpenCode](opencode.md)
- [AmpCode](ampcode.md)
- [Continue](continue.md)
- [Cursor](cursor.md)
- [Cline](cline.md)
- [Aider](aider.md)
- [OpenClaw / ClawdBot](openclaw.md)
- [n8n](n8n.md)

### Ứng dụng khác

- [Cherry Studio](cherry-studio.md)
- [Lobe Chat](lobe-chat.md)

## Gợi ý chọn trang nhanh

- Bạn dùng CLI Anthropic-native: vào [Claude Code](claude-code.md).
- Bạn dùng tool theo chuẩn OpenAI-compatible: bắt đầu từ [Roo Code](roo-code.md), [Continue](continue.md), [Cursor](cursor.md), [Cline](cline.md), [Aider](aider.md).
- Bạn chạy automation workflow: xem [n8n](n8n.md).
