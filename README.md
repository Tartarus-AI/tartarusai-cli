<p align="center">
  <img src="https://tartarusai.dev/logo.svg" width="120" alt="TartarusAI">
</p>

<h1 align="center">tartarusai-cli</h1>

<p align="center"><i>The coding agent that doesn't refuse your own work.</i></p>

<p align="center">
  <a href="https://tartarusai.dev"><img alt="site" src="https://img.shields.io/badge/site-tartarusai.dev-b82400?style=flat-square"></a>
  <a href="https://github.com/Tartarus-AI/tartarusai-cli/releases"><img alt="release" src="https://img.shields.io/github/v/release/Tartarus-AI/tartarusai-cli?style=flat-square&color=d4914f&display_name=tag&include_prereleases"></a>
  <a href="https://discord.gg/GfzePawBBd"><img alt="discord" src="https://img.shields.io/badge/discord-join-5865F2?style=flat-square&logo=discord&logoColor=white"></a>
  <a href="https://x.com/TartarusAIDev"><img alt="x" src="https://img.shields.io/badge/x-@TartarusAIDev-000?style=flat-square&logo=x&logoColor=white"></a>
  <a href="./LICENSE"><img alt="license" src="https://img.shields.io/badge/license-MIT-d4914f?style=flat-square"></a>
</p>

---

> *"I can't help with that."* — every other coding agent, on routine work.
>
> Tartarus Coder ships the code. No lecture, no asterisks, no "as an AI…".

`tartarusai-cli` is the official terminal client for **TartarusAI** — an
uncensored coding agent built for the work mainstream models punt on.

It's not a jailbreak. It's not a wrapper. It's a CLI talking to a model
that wasn't trained to refuse you in the first place.

## Why this exists

Every senior dev has the same story:

- *"Write a port scanner for **my own** lab."* → refused.
- *"Help me deobfuscate this script I found in our incident response."* → refused.
- *"Write a credential-rotation tool that **revokes** leaked tokens."* → refused.

The models can do the work. They're just trained to refuse, "for safety."
That refusal isn't safety. It's liability theater that shifts risk onto you.

So we built one that does the work.

## What it is

- **Uncensored coding agent.** No policy filter wedged between you and your editor.
- **256K context.** Drop the whole repo in; the agent reasons over all of it.
- **Crypto-only billing.** No card on file, no recurring charge, no chargeback risk.
- **~30 seconds to live.** Pay, network confirms, the CLI activates.
- **14-day refund.** It earns its keep or you get it back.

## What it isn't

Read this once.

- **Not a malware factory.** No weaponized payloads, no stealers, no spyware,
  no actual exploit kits. Writing lab PoCs for *patched, public* CVEs is
  standard pentest material; we do that. Attacking systems you don't own —
  we don't help with that.
- **Not a piracy tool.** No DRM bypass, no keygens for someone else's
  software, no license cracking.
- **Not a politics bot.** It's a coding agent. We optimize for shipping code.

The line is the same line a professional pentest course or CTF runs on
every day. The difference is we just *do the work* instead of writing
you an essay about whether we should.

## Install

Grab a binary from [Releases](https://github.com/Tartarus-AI/tartarusai-cli/releases/latest):

### Linux (x86_64)

```bash
curl -L -o tartarusai-cli \
  https://github.com/Tartarus-AI/tartarusai-cli/releases/latest/download/tartarusai-cli-linux-x64
chmod +x tartarusai-cli
sudo mv tartarusai-cli /usr/local/bin/
```

### Windows (x86_64)

```powershell
iwr https://github.com/Tartarus-AI/tartarusai-cli/releases/latest/download/tartarusai-cli-windows-x64.exe `
    -OutFile $env:USERPROFILE\bin\tartarusai-cli.exe
```

> macOS, Linux ARM, Windows ARM — coming. Email `team@tartarusai.dev` if you
> need one early; we'll cut a build.

## Quickstart

```bash
# 1. Sign up + generate a CLI token
#    https://dash.tartarusai.dev/account

# 2. Save the token (Unix)
mkdir -p ~/.tartarus
cat > ~/.tartarus/cli-token.json <<EOF
{
  "endpoint":   "https://api.tartarusai.dev",
  "token":      "<paste-the-token-here>",
  "user_email": "you@example.com",
  "issued_at":  "$(date -Iseconds)"
}
EOF

# 3. Run
tartarusai-cli
```

On Windows the token file goes to `%USERPROFILE%\.tartarus\cli-token.json`
with the same shape.

That's it. The CLI reads the token, points itself at `api.tartarusai.dev`,
and you're in the TUI.

## Pricing

Crypto only (USDT TRC20/ERC20, BTC, ETH). Prepay 1 / 3 / 12 months.
The 12-month plan is ~20% cheaper per month than 1-month. Stacks on
remaining time when you renew early. No card, ever.

See https://tartarusai.dev/#pricing for current tiers.

## Architecture

```
your terminal  →  tartarusai-cli (this repo)
                       ↓
              dash.tartarusai.dev  (account, billing, token mgmt)
                       ↓
              api.tartarusai.dev   (Sanctum auth + quota + proxy)
                       ↓
              inference.tartarusai.dev  (uncensored model · 256K ctx)
```

Three independent defense layers stand between the public model and abuse:
account auth, per-user weekly quota, and a model-side bearer token. The CLI
itself is dumb — auth + endpoint live in `~/.tartarus/cli-token.json` and
nothing else.

## Built on

`tartarusai-cli` is a hard fork of the excellent
[**opencode**](https://github.com/sst/opencode) project (MIT). We rebranded
the user-facing surface, removed the upstream hosted-cloud integrations,
pointed the model layer at our own inference, and shipped it under our name.

The original `LICENSE` is preserved unchanged; modifications are summarized
in [`NOTICE`](./NOTICE), as MIT requires. If you fork this further, do the
same.

## Community

| | |
|---|---|
| 💬 Discord  | https://discord.gg/GfzePawBBd |
| 🐦 X        | https://x.com/TartarusAIDev |
| 👥 Reddit   | https://reddit.com/r/TartarusAI |
| 📰 Blog     | https://tartarusai.dev/blog |
| 📧 Email    | team@tartarusai.dev |

Discord is the fastest channel for live help. Bugs and feature requests
go in [Issues](https://github.com/Tartarus-AI/tartarusai-cli/issues).

## License

MIT — see [`LICENSE`](./LICENSE).

Includes substantial code from the [opencode](https://github.com/sst/opencode)
project, also MIT. Original copyright preserved in `LICENSE`; modifications
summarized in [`NOTICE`](./NOTICE).
