# Skills

Public AI agent skills by [zubair2005](https://github.com/zubair2005).

## Available skills

- [`qiyas`](./qiyas/): reuses your earlier decisions by careful analogy, so your agent asks you fewer repeated questions and makes better calls when it acts alone. Built on qiyas (قياس) from usul al-fiqh.

## Install

In Codex, ask the built-in installer:

```text
$skill-installer install https://github.com/zubair2005/skills/tree/main/qiyas
```

Any other agent that supports skills can install it from the link:

```text
Install the AI agent skill at https://github.com/zubair2005/skills/tree/main/qiyas
```

Or clone this repo and copy the skill folder into your agent's skills folder:

```bash
git clone https://github.com/zubair2005/skills.git
cp -R skills/qiyas ~/.codex/skills/
```

For Claude Code, copy it to `~/.claude/skills/` instead. The [qiyas README](./qiyas/) covers recommended usage.

## License

MIT
