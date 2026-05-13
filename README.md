# Agentry — Distribution

Öffentlicher Distributions-Spiegel für
[Agentry](https://github.com/torben-erz/Agentry) — ein plattform-
agnostisches Agenten-Framework, das Tickets autonom in Pull Requests
verwandelt.

Dieses Repository enthält **nur** signierte/notarisierte Release-
Binaries für macOS und Linux. Der Source-Code liegt während der
Closed-Beta-Phase in einem privaten Repository.

## Installation

### Homebrew (empfohlen)

```bash
brew tap torben-erz/agentry
brew install agentry
```

Die Formula installiert ein vorgebautes Binary — kein Build nötig.
macOS-Binaries sind signiert (Developer-ID) und notarisiert, deshalb
akzeptiert Gatekeeper sie ohne Sperre.

### Manueller Download

Tarball aus den
[Releases](https://github.com/torben-erz/agentry-dist/releases) holen:

| Plattform | Datei |
|---|---|
| macOS Apple Silicon | `agentry-vX.Y.Z-macos-arm64.tar.gz` |
| Linux x86_64 | `agentry-vX.Y.Z-linux-x86_64.tar.gz` |

```bash
tar -xzf agentry-vX.Y.Z-macos-arm64.tar.gz
mv agentry /usr/local/bin/
agentry version
```

## Erster Start

```bash
agentry init                       # schreibt ~/.agentry/config.json
$EDITOR ~/.agentry/config.json     # 'watch' auf dein Repo setzen
agentry config validate            # Exit 0 = bereit
agentry daemon                     # Daemon starten
```

Den ausführlichen 15-Minuten-Beta-Walkthrough teilen wir direkt mit
Beta-Testern — bei Interesse einfach melden.

## Updates

```bash
brew upgrade agentry               # bei Homebrew-Installation
```

Der Daemon prüft dieses Repo alle 24 Stunden auf neue Releases und
loggt WARN, sobald ein Update verfügbar ist. Manueller Check ohne
Daemon-Restart:

```bash
agentry update
```

Liegt das Binary unter einem Homebrew-Prefix, zeigt der Log/CLI-Output
direkt `brew upgrade agentry` als Update-Pfad.

## Voraussetzungen

| Tool | Pflicht | Zweck |
|---|---|---|
| `git` | ✅ | Daemon klont/pusht in Worktrees |
| `gh` *oder* `glab` | ✅ | GitHub- bzw. GitLab-Provider-CLI für Ticket-API |
| `claude` *oder* `codex` | ✅ | Mindestens ein Agent-Backend |
| `bubblewrap` (Linux) | ✅ | Default-Sandbox auf Linux |

Optionale Provider/Backends kann der Operator über die Config
auswählen — siehe `agentry init`-Template.

## Bug-Reports

Für Beta-Tester — strukturierten Diagnose-Block erzeugen und mit dem
Bug-Report mitschicken:

```bash
agentry diagnose | pbcopy          # macOS-Zwischenablage
agentry diagnose                   # stdout
```

Der Block enthält Version, Plattform, Tool-Verfügbarkeit, Sandbox-
Status, Config-Health und die letzten 30 WARN/ERROR-Log-Zeilen.
**Nicht enthalten**: Tokens, Webhook-Secrets, Ticket-Inhalte,
vollständige Pfade zu Secret-Dateien.

## Lizenz

Binaries in diesem Repository werden unter der MIT-Lizenz verteilt
(siehe `LICENSE`). Der Agentry-Source-Code ist während der Beta-
Phase proprietär; die langfristige Source-Lizenz wird im Zuge der
Vertriebsmodell-Entscheidung festgelegt.

## Status

Closed Beta seit 2026-05. Eine öffentliche Source-Veröffentlichung
ist geplant, aber noch nicht terminiert.
