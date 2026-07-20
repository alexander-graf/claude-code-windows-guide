# Claude Code Installation (Windows 10/11 & Linux)

Dieser Guide beschreibt eine saubere Installation von Claude Code über npm für **Windows** (mit Fokus auf PATH-Probleme) und **Linux / macOS**.

## 🚀 Quick Start: Linux / macOS

Auf Unix-basierten Systemen ist die Installation dank nativer Bash-Integration meist ein Kinderspiel:

```bash
# 1) Node.js (Version 22+) prüfen:
node -v
npm -v

# 2) Claude Code global installieren:
npm install -g @anthropic-ai/claude-code

# 3) Prüfen & starten:
claude --version
claude doctor
```
*(Tipp: Vermeide `sudo npm install -g`. Nutze stattdessen [NVM](https://github.com/nvm-sh/nvm), falls du Rechte-Probleme (EACCES) hast).*

## 🚀 Quick Start: Windows 10/11

Auf Windows sollen diese Befehle am Ende in einem **neu geöffneten** PowerShell-Fenster (ohne Adminrechte) funktionieren:

```powershell
# 1) Nach Node.js LTS Installation (nodejs.org) prüfen:
node -v
npm -v

# 2) Claude Code global per npm installieren:
npm install -g @anthropic-ai/claude-code

# 3) Falls 'claude' danach nicht gefunden wird, den User-PATH per PowerShell reparieren:
$currentPath = [Environment]::GetEnvironmentVariable('PATH', 'User')
[Environment]::SetEnvironmentVariable('PATH', "$currentPath;$env:USERPROFILE\.local\bin", 'User')

# 4) Komplett neues PowerShell Terminal öffnen und prüfen:
claude --version
claude doctor
```

## Vorbereitung & Häufige Fehlerquellen

1. **Windows Version & Architektur:**
   Claude Code benötigt mindestens Windows 10 (Version 1809) 64-Bit oder ARM64. Keine 32-Bit Systeme. Nutze normales PowerShell (nicht x86, nicht CMD).
2. **Node.js LTS Version:**
   Es wird zwingend **Node.js 22 oder neuer** empfohlen.
3. **PATH-Problem nach Node.js Installation:**
   Nach der Installation von Node.js muss das Terminal *zwingend* neu geöffnet werden, sonst kommt der Fehler `npm is not recognized`.
4. **Git for Windows (Optional):**
   Damit Claude Code Bash-Werkzeuge nutzen kann, ist [Git for Windows](https://git-scm.com/downloads/win) extrem hilfreich.
5. **Mehrere Installationen vermeiden:**
   Solltest du Claude über WinGet und npm gemischt installiert haben, entferne eine davon. Nutze `where.exe claude` um Konflikte zu finden.

> Weitere, sehr detaillierte Troubleshooting-Tipps (Netzwerkfehler, blockierte Dateien, EBADENGINE) findest du im Originalartikel: 
> [Alexander Graf Blog: Claude Code installieren](https://alexandergraf.de/blog/claude-code-installieren/)
