# agent-skills-fa 🇮🇷

A collection of **Persian (Farsi) agent skills** for AI assistants — written in the
[Anthropic Skills](https://github.com/anthropics/skills) authoring format: every skill is a
folder with a `SKILL.md` file (YAML frontmatter + instructions) that an agent loads on demand.

> Pattern inspired by anthropics/skills (180k+ ⭐). All content here is original and written
> for Persian-speaking businesses: Instagram pages, local shops, and sales follow-up.

## What is a skill?

A skill is a small, self-contained instruction pack. Instead of pasting a long prompt every
time, you drop the skill folder into your agent's skills directory once — and the agent picks
it up automatically whenever your request matches the skill's `description`.

Each `SKILL.md` contains:
- **Frontmatter** — `name` and `description` (when the agent should use this skill)
- **Instructions** — the exact steps, rules and output format, in Persian

## Catalog

| Skill | What it does | Use it when… |
|---|---|---|
| [instagram-caption-fa](skills/instagram-caption-fa/SKILL.md) | News-first Persian caption: hook, number bullets, follow CTA | You have a reel/post topic and need a caption |
| [shop-audit-fa](skills/shop-audit-fa/SKILL.md) | One-page audit of an Instagram page or a shop | Preparing a free audit before pitching an AI agent |
| [lead-followup-fa](skills/lead-followup-fa/SKILL.md) | 3-step Persian lead follow-up messages | A lead went silent after the first contact |
| [content-calendar-fa](skills/content-calendar-fa/SKILL.md) | 7-day content calendar for a page | Planning a week of reels + stories |
| [price-quote-fa](skills/price-quote-fa/SKILL.md) | Price answer + proforma invoice text for a customer | A customer asks "how much?" in DM/chat |

## Install / use

**Claude / Claude Code style agents**
1. Copy the skill folder(s) you want into your skills directory (e.g. `~/.claude/skills/` or your project's `skills/`).
2. Ask in Persian, e.g. «برای این موضوع کپشن بنویس: …» — the matching skill loads automatically.

**Any other LLM (ChatGPT, etc.)**
1. Open the skill's `SKILL.md`, copy everything below the frontmatter.
2. Paste it as the system/custom instruction, then send your request.

**Validate the collection**
```bash
python3 - <<'PY'
import pathlib, re
for p in sorted(pathlib.Path("skills").glob("*/SKILL.md")):
    fm = re.match(r"^---\n(.*?)\n---\n", p.read_text(encoding="utf-8"), re.S).group(1)
    assert "name:" in fm and "description:" in fm, p
    print("OK", p)
PY
```

## License
MIT — use, adapt and sell services with these skills; keep the credit line.

---
## فارسی

مجموعه اسکیل‌های فارسی برای ایجنت‌های هوش مصنوعی، با فرمت استاندارد Skills: هر اسکیل یه پوشه‌ست
با یه فایل `SKILL.md` که ایجنت موقع نیاز خودش لودش می‌کنه.

| اسکیل | کارش چیه |
|---|---|
| instagram-caption-fa | کپشن خبری فارسی: هوک + بولت عددی + CTA فالو |
| shop-audit-fa | آدیت یک‌صفحه‌ای پیج یا مغازه برای فروش ایجنت |
| lead-followup-fa | پیام پیگیری لید در ۳ مرحله |
| content-calendar-fa | تقویم محتوای ۷ روزه پیج |
| price-quote-fa | پاسخ قیمت + متن پیش‌فاکتور برای مشتری |

**نصب:** پوشه اسکیل رو کپی کن تو پوشه skills ایجنتت؛ بعد فقط فارسی درخواست بده، خودش پیداش می‌کنه.
ساخته‌شده در «خدمات کامپیوتری سینا» — اراک، برای کسب‌وکارهای فارسی‌زبان.
