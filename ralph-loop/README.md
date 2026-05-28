<div align="center">

# 🔄 Ralph-Loop™

### 6-Phasen Execution Pipeline — Frischer Kontext für jeden Task

[![Phasen](https://img.shields.io/badge/Phasen-6-fa1e4e?style=for-the-badge&logo=circuitverse&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Prinzip](https://img.shields.io/badge/Prinzip-Fresh_Context-00ff88?style=for-the-badge&logo=sparkles&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Phase 1](https://img.shields.io/badge/Phase_1-LESEN-3b82f6?style=for-the-badge&logo=readme&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Phase 2](https://img.shields.io/badge/Phase_2-SPAWN-6366f1?style=for-the-badge&logo=rocket&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Phase 3](https://img.shields.io/badge/Phase_3-EXECUTE-ffb800?style=for-the-badge&logo=code&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Phase 4](https://img.shields.io/badge/Phase_4-VERIFY-00ff88?style=for-the-badge&logo=checkmarx&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Phase 5](https://img.shields.io/badge/Phase_5-COMMIT-3b82f6?style=for-the-badge&logo=git&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Phase 6](https://img.shields.io/badge/Phase_6-LOOP-fa1e4e?style=for-the-badge&logo=loop&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Context](https://img.shields.io/badge/Context-No_Drift-00ff88?style=for-the-badge&logo=shield&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Tasks](https://img.shields.io/badge/Tasks-Atomic-ffb800?style=for-the-badge&logo=atom&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![PRD](https://img.shields.io/badge/PRD-JSON-6366f1?style=for-the-badge&logo=json&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Constitution](https://img.shields.io/badge/Constitution-Enforced-fa1e4e?style=for-the-badge&logo=security&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Rollback](https://img.shields.io/badge/Rollback-Auto-3b82f6?style=for-the-badge&logo=undo&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Timeout](https://img.shields.io/badge/Timeout-30min-ffb800?style=for-the-badge&logo=timer&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Retry](https://img.shields.io/badge/Retry-3x-00ff88?style=for-the-badge&logo=refresh&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![License](https://img.shields.io/badge/License-Proprietary-060608?style=for-the-badge&logo=gnuprivacyguard&logoColor=fa1e4e)](https://github.com/777/devkitz-ecosystem)

**Ralph-Loop™** ist das Herzstück der DEVKiTZ™ Task-Execution. Jeder Task durchläuft exakt 6 Phasen — von der Kontextanalyse bis zum Git-Commit. Das Kernprinzip: **Jeder Task bekommt einen frischen Kontext**, sodass kein Context-Drift die Qualität beeinträchtigt.

[Phasen](#-die-6-phasen) · [Flowchart](#-pipeline-flowchart) · [Context-Drift](#-context-drift-prevention) · [Fehler](#-fehlerbehandlung) · [Config](#%EF%B8%8F-konfiguration)

</div>

---

## 🔁 Die 6 Phasen

Jede Phase hat einen klar definierten Eingang, eine Verantwortung und einen Ausgang. Scheitert eine Phase, greift das automatische Rollback — der gesamte Loop wird sauber zurückgesetzt.

### Phase 1 — 📖 LESEN

Der Einstiegspunkt jedes Loops. James™ analysiert die Task-Tags und lädt **nur relevante** Artefakte aus dem Iceberg™-Archiv. Irrelevanter Kontext wird bewusst ausgelassen.

```javascript
// Phase 1: Kontextanalyse durch James™
async function phaseLesen(task) {
  const prd = await loadJSON('prd.json');
  const constitution = await loadFile('CLAUDE.md');
  const agents = await loadFile('AGENTS.md');
  
  // Nur relevante Artefakte laden
  const artifacts = await iceberg.query({
    tags: task.tags,
    module: task.module,
    limit: 5  // Maximal 5 Kontext-Artefakte
  });
  
  return { prd, constitution, agents, artifacts };
}
```

### Phase 2 — 🚀 SPAWN

Eine **neue Agent-Instanz** wird mit frischem Kontext gestartet. Kein alter State, keine veralteten Annahmen. Der Agent erhält exakt die Informationen aus Phase 1.

### Phase 3 — ⚡ EXECUTE

Der Developer™ schreibt Code. Jeder Task ist **atomar** — ein Feature, ein Bug-Fix, eine Verbesserung. Niemals mehrere Dinge gleichzeitig in einem Loop.

### Phase 4 — ✅ VERIFY

Reviewer™ und Tester™ prüfen das Ergebnis. Code-Qualität, Regelwerk-Konformität, Screenshots und E2E-Tests werden automatisch durchgeführt.

### Phase 5 — 📝 COMMIT

Bei bestandener Verifikation wird ein Git-Commit erstellt und die `prd.json` mit dem neuen Task-Status aktualisiert. Das Artefakt wird dreifach verankert.

### Phase 6 — 🔄 LOOP

Der Loop prüft, ob weitere Tasks in der Queue stehen. Falls ja, wird Phase 1 mit dem **nächsten Task** gestartet — mit komplett frischem Kontext.

---

## 📊 Pipeline-Flowchart

```mermaid
graph LR
    START(("🎯 Task<br/>aus Queue")) --> P1

    subgraph Ralph["🔄 Ralph-Loop™"]
        P1["📖 Phase 1<br/>LESEN<br/>──────────<br/>prd.json laden<br/>Constitution lesen<br/>Artefakte filtern"]
        P2["🚀 Phase 2<br/>SPAWN<br/>──────────<br/>Frische Instanz<br/>Kontext injizieren<br/>Timeout setzen"]
        P3["⚡ Phase 3<br/>EXECUTE<br/>──────────<br/>Code schreiben<br/>Atomarer Task<br/>Developer™"]
        P4["✅ Phase 4<br/>VERIFY<br/>──────────<br/>Review + Tests<br/>Regelwerk-Check<br/>Screenshots"]
        P5["📝 Phase 5<br/>COMMIT<br/>──────────<br/>Git Commit<br/>prd.json Update<br/>Dreifach-Anker"]
        P6{"🔄 Phase 6<br/>LOOP<br/>──────────<br/>Weitere Tasks?"}
    end

    P1 --> P2 --> P3 --> P4
    P4 -->|"✅ Bestanden"| P5
    P4 -->|"❌ Fehlgeschlagen"| RB["↩️ Rollback"]
    RB --> P1
    P5 --> P6
    P6 -->|"Ja"| P1
    P6 -->|"Nein"| DONE(("✅ Fertig"))

    style Ralph fill:#060608,stroke:#fa1e4e,stroke-width:2px,color:#fff
    style START fill:#3b82f6,stroke:#3b82f6,color:#fff
    style DONE fill:#00ff88,stroke:#00ff88,color:#060608
    style RB fill:#ffb800,stroke:#ffb800,color:#060608
```

---

## 🛡️ Context-Drift Prevention

Context-Drift ist der größte Feind langlebiger Agent-Sessions. Ralph-Loop™ eliminiert dieses Problem durch konsequente Isolation.

| Problem | Lösung | Mechanismus |
|:--------|:-------|:------------|
| Veraltete Annahmen | Frischer Kontext pro Task | Phase 2: SPAWN erzeugt neue Instanz |
| Kontext-Überladung | Selektives Laden | James™ filtert nach Task-Tags |
| Halluzination durch alten State | Kein State-Carry-Over | Jeder Loop startet bei Null |
| Widersprüchliche Instruktionen | Constitution First | `CLAUDE.md` + `AGENTS.md` immer geladen |
| Schleichende Qualitätsabnahme | Atomare Tasks | Ein Task = Ein Loop = Ein Commit |

```javascript
// Context-Drift Guard — verhindert veralteten Kontext
function validateContextFreshness(context) {
  const maxAge = 30 * 60 * 1000; // 30 Minuten
  
  if (Date.now() - context.loadedAt > maxAge) {
    throw new ContextDriftError(
      'Kontext älter als 30min — SPAWN wird erzwungen'
    );
  }
  
  // Prüfe ob Constitution aktuell ist
  const currentHash = hashFile('CLAUDE.md');
  if (context.constitutionHash !== currentHash) {
    throw new ContextDriftError(
      'Constitution hat sich geändert — Reload erforderlich'
    );
  }
}
```

---

## 🚨 Fehlerbehandlung pro Phase

Jede Phase hat eine spezifische Fehlerbehandlung. Das System unterscheidet zwischen **transienten** Fehlern (Retry) und **permanenten** Fehlern (Eskalation).

| Phase | Fehlertyp | Aktion | Max. Retries |
|:------|:----------|:-------|:-------------|
| LESEN | Datei nicht gefunden | Fallback auf Cache | 2 |
| LESEN | prd.json korrupt | Eskalation an James™ | 0 |
| SPAWN | Timeout beim Start | Auto-Retry mit Backoff | 3 |
| EXECUTE | Code-Fehler | Rollback + Retry | 3 |
| EXECUTE | Timeout (30min) | Task pausieren, nächsten starten | 1 |
| VERIFY | Test fehlgeschlagen | Zurück zu EXECUTE | 2 |
| VERIFY | Regelwerk-Verletzung | Sofort-Stopp, James™ Alert | 0 |
| COMMIT | Git-Konflikt | Rebase + Retry | 3 |
| COMMIT | Dreifach-Anker fehlgeschlagen | Warnung, Commit trotzdem | 1 |

---

## 📋 PRD-Format (prd.json)

Die `prd.json` ist die Single Source of Truth für alle Tasks im Loop. Sie wird nach jedem COMMIT automatisch aktualisiert.

```json
{
  "project": "devkitz-dashboard",
  "version": "2.4.0",
  "tasks": [
    {
      "id": "TASK-2026-0528-001",
      "title": "Swarm README erstellen",
      "module": "temp_swarm",
      "priority": "P1",
      "status": "completed",
      "assignee": "DkZ Dokumentar™",
      "tags": ["docs", "readme", "swarm"],
      "loop": {
        "phase": 5,
        "retries": 0,
        "startedAt": "2026-05-28T16:00:00Z",
        "completedAt": "2026-05-28T16:05:00Z"
      }
    }
  ]
}
```

---

## ⚙️ Konfiguration

```json
{
  "ralphLoop": {
    "phases": 6,
    "taskMode": "atomic",
    "contextMode": "fresh",
    "maxContextArtifacts": 5,
    "timeout": 1800000,
    "maxRetries": 3,
    "rollback": {
      "auto": true,
      "gitReset": "soft"
    },
    "constitution": ["CLAUDE.md", "AGENTS.md", "REGELWERK.md"],
    "driftGuard": {
      "enabled": true,
      "maxAge": 1800000,
      "hashCheck": true
    }
  }
}
```

---

## 🔗 Verwandte Systeme

| System | Rolle im Loop | Link |
|:-------|:-------------|:-----|
| 🐝 Agent Swarm™ | Orchestriert die Agenten | [agent-swarm/](../agent-swarm/) |
| 🧊 Iceberg™ | Artefakt-Persistenz in Phase 5 | [iceberg-data/](../iceberg-data/) |
| 🤖 Copilot Bridge™ | LLM-Provider für EXECUTE | [copilot-bridge/](../copilot-bridge/) |
| 📨 Hermes™ | Benachrichtigungen bei Fehlern | [hermes-comms/](../hermes-comms/) |
| 🕸️ BotNet™ | Deployment nach Loop | [botnet-ops/](../botnet-ops/) |

---

<div align="center">

**🔄 Ralph-Loop™** — Teil des [DEVKiTZ™ Ökosystems](https://github.com/777/devkitz-ecosystem)

`Built with 🔥 by 777 · Fresh Context · Zero Drift · Atomic Tasks`

[![DEVKiTZ](https://img.shields.io/badge/DEVKiTZ™-Ecosystem-fa1e4e?style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZD0iTTEyIDJMMyAyMGgyMEwxMiAyeiIgZmlsbD0iI2ZhMWU0ZSIvPjwvc3ZnPg==)](https://github.com/777/devkitz-ecosystem)

</div>
