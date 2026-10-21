# Bang_Skill

Skill `bang-skill` giúp mọi repo luôn tự mô tả được cho bất kỳ coding agent nào:

| File | Nội dung |
|------|----------|
| `Project_proposal.md` | Dự án làm gì: topic, scope, data, pipeline, stack, open questions, changelog |
| `task_board.md` | Toàn bộ task giao cho AI: ID, status, priority, owner, phase, done-when |
| `Process_phases/` | `README.md` (index) + mỗi phase lớn một file `NN_<phase>.md`: goal, work log, decisions, outputs, risks, exit criteria |

Quy tắc bắt buộc: **không xóa database, code, project nếu người dùng chưa chốt.**

## Yêu cầu
Cài [ponytail](https://github.com/DietrichGebert/ponytail) trước (skill sẽ chạy ở chế độ `/ponytail:ponytail ultra`):
```
/plugin marketplace add DietrichGebert/ponytail
/plugin install ponytail@ponytail
```

## Cài đặt (Claude Code)
Gửi hai prompt riêng:
```
/plugin marketplace add Lilkremxxxx/Bang_Skill
/plugin install bang-skill@bang-skill
```
Sau đó trong repo bất kỳ:
```
/bang-skill:bang-skill
```
Lần đầu: quét repo, tạo 3 artifact và chèn khối rules vào `CLAUDE.md` + `AGENTS.md` của repo để các phiên sau luôn cập nhật.

## Agent khác (Codex, Cursor, Copilot, ...)
Copy [`AGENTS.md`](AGENTS.md) vào thư mục gốc project, hoặc bảo agent đọc `skills/bang-skill/SKILL.md`.

## Cấu trúc
```
.claude-plugin/        plugin.json, marketplace.json
skills/bang-skill/     SKILL.md + templates/
AGENTS.md              bản cho agent không phải Claude
```
