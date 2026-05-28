<div align="center">

# 🐝 Agent Swarm™

### Intelligente Multi-Agenten Orchestrierung für DEVKiTZ™

[![System](https://img.shields.io/badge/System-Orchestrator-fa1e4e?style=for-the-badge&logo=apachekafka&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Agents](https://img.shields.io/badge/Agents-7-00ff88?style=for-the-badge&logo=robot&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Loops](https://img.shields.io/badge/Loops-8-ffb800?style=for-the-badge&logo=loop&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Status](https://img.shields.io/badge/Status-Production-00ff88?style=for-the-badge&logo=statuspage&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Monitoring](https://img.shields.io/badge/Monitoring-Ampel-ffb800?style=for-the-badge&logo=grafana&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Dashboard](https://img.shields.io/badge/Dashboard-Live-3b82f6?style=for-the-badge&logo=dashboard&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Modules](https://img.shields.io/badge/Modules-132+-6366f1?style=for-the-badge&logo=puzzle&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Health](https://img.shields.io/badge/Health-Auto--Check-00ff88?style=for-the-badge&logo=checkmarx&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Recovery](https://img.shields.io/badge/Recovery-Graceful-ffb800?style=for-the-badge&logo=shield&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Priority](https://img.shields.io/badge/Priority-P0-fa1e4e?style=for-the-badge&logo=target&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Events](https://img.shields.io/badge/Events-Real--time-3b82f6?style=for-the-badge&logo=eventbrite&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Queue](https://img.shields.io/badge/Queue-FIFO-6366f1?style=for-the-badge&logo=rabbitmq&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![Scaling](https://img.shields.io/badge/Scaling-Horizontal-00ff88?style=for-the-badge&logo=kubernetes&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![API](https://img.shields.io/badge/API-REST-3b82f6?style=for-the-badge&logo=fastapi&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![WebSocket](https://img.shields.io/badge/WebSocket-Live-fa1e4e?style=for-the-badge&logo=socketdotio&logoColor=white)](https://github.com/777/devkitz-ecosystem)
[![License](https://img.shields.io/badge/License-Proprietary-060608?style=for-the-badge&logo=gnuprivacyguard&logoColor=fa1e4e)](https://github.com/777/devkitz-ecosystem)

**Agent Swarm™** ist das zentrale Nervensystem des DEVKiTZ™ Ökosystems — ein Event-getriebener Orchestrator, der 7 spezialisierte BMAD™-Agenten über 8 parallele Loops koordiniert. Jeder Agent besitzt einen klar definierten Verantwortungsbereich und kommuniziert über eine priorisierte FIFO-Queue.

[Architektur](#-architektur) · [Agenten](#-bmad-agenten) · [Event-System](#-event-system) · [API](#-api-referenz) · [Konfiguration](#%EF%B8%8F-konfiguration)

</div>

---

## 🏗️ Architektur

Das folgende Diagramm zeigt den vollständigen Orchestrierungs-Flow — von eingehenden Tasks über die FIFO-Queue bis zur Ausführung durch die spezialisierten Agenten und die Rückmeldung ans Ampel-Dashboard.

```mermaid
graph TB
    subgraph Eingang["📥 Task-Eingang"]
        PRD["prd.json"]
        API["REST API"]
        WS["WebSocket"]
        GH["GitHub Webhook"]
    end

    subgraph Orchestrator["🐝 Agent Swarm™ Orchestrator"]
        Q["FIFO Queue<br/>Priorisiert P0-P3"]
        SCHED["Scheduler<br/>Round-Robin + Priority"]
        EVT["Event Bus<br/>Real-time Dispatch"]
        HM["Health Monitor<br/>Ampel-System"]
    end

    subgraph Agenten["🤖 BMAD™ Agenten"]
        J["🎯 James™<br/>Guardian"]
        PM["📋 DkZ PM™<br/>Product Manager"]
        AR["🏗️ DkZ Architekt™<br/>Planer"]
        DEV["👨‍💻 DkZ Developer™<br/>Coder"]
        REV["🔍 DkZ Reviewer™<br/>CodeRabbit"]
        TST["🧪 DkZ Tester™<br/>Validation"]
        DOC["📚 DkZ Dokumentar™<br/>Docs"]
    end

    subgraph Output["📤 Output"]
        DASH["Ampel Dashboard"]
        GIT["Git Commit"]
        LOG["Event Log"]
    end

    PRD --> Q
    API --> Q
    WS --> Q
    GH --> Q
    Q --> SCHED
    SCHED --> EVT
    EVT --> J
    EVT --> PM
    EVT --> AR
    EVT --> DEV
    EVT --> REV
    EVT --> TST
    EVT --> DOC
    J --> HM
    HM --> DASH
    DEV --> GIT
    EVT --> LOG

    style Orchestrator fill:#060608,stroke:#fa1e4e,stroke-width:2px,color:#fff
    style Agenten fill:#060608,stroke:#00ff88,stroke-width:2px,color:#fff
    style Eingang fill:#060608,stroke:#3b82f6,stroke-width:2px,color:#fff
    style Output fill:#060608,stroke:#ffb800,stroke-width:2px,color:#fff
```

---

## 🤖 BMAD™ Agenten

Die 7 Agenten bilden das Rückgrat der BMAD™-Methodik (Blueprint → Mapping → Analyse → Design). Jeder Agent hat einen isolierten Verantwortungsbereich und wird vom Orchestrator gezielt aktiviert.

| # | Agent | Rolle | Verantwortung | Auto-Start |
|:--|:------|:------|:--------------|:-----------|
| 1 | 🎯 **James™** | Guardian | Überwacht alle Agenten, enforced Constitution, coded **NICHT** | ✅ Immer |
| 2 | 📋 **DkZ PM™** | Product Manager | Erstellt `spec.md`, User Stories, Akzeptanzkriterien | Bei neuem Feature |
| 3 | 🏗️ **DkZ Architekt™** | Planer | Erstellt `plan.md`, definiert Tech-Stack, Modul-Grenzen | Bei neuem Feature |
| 4 | 👨‍💻 **DkZ Developer™** | Coder | Schreibt Code im Ralph-Loop™, führt Tasks atomar aus | Bei `EXECUTE` Phase |
| 5 | 🔍 **DkZ Reviewer™** | CodeRabbit | Pull-Request-Reviews, Code-Qualität, Regelwerk-Check | Nach jedem Commit |
| 6 | 🧪 **DkZ Tester™** | Validation | E2E-Tests, Screenshot-Vergleiche, Regression | Nach Review |
| 7 | 📚 **DkZ Dokumentar™** | Docs | README, Wiki, CHANGELOG, Learnings-Einträge | Nach Merge |

---

## 🔄 Agent-Lifecycle Management

Jeder Agent durchläuft einen definierten Lebenszyklus. Der Orchestrator verwaltet den State jedes Agenten und stellt sicher, dass bei Fehlern ein Graceful Recovery greift.

```javascript
// Agent-Lifecycle States
const AgentState = {
  IDLE:      'idle',       // Bereit, wartet auf Task
  SPAWNING:  'spawning',   // Frischer Kontext wird geladen
  ACTIVE:    'active',     // Führt Task aus
  BLOCKED:   'blocked',    // Wartet auf Dependency
  RECOVERY:  'recovery',   // Fehler erkannt, Auto-Recovery
  COMPLETED: 'completed'   // Task abgeschlossen
};

// Orchestrator spawnt Agent mit frischem Kontext
function spawnAgent(agentType, taskPayload) {
  const agent = {
    id: `agent-${agentType}-${Date.now()}`,
    type: agentType,
    state: AgentState.SPAWNING,
    context: loadFreshContext(taskPayload),
    timeout: 30 * 60 * 1000,  // 30 Minuten
    retries: 3,
    priority: taskPayload.priority || 'P2'
  };
  
  eventBus.emit('agent:spawned', agent);
  return agent;
}
```

---

## ⚡ Event-System

Das Event-System ist das Kommunikations-Backbone des Swarm. Alle Agenten und Subsysteme kommunizieren ausschließlich über typisierte Events — niemals direkte Aufrufe.

| Event | Emitter | Listener | Beschreibung |
|:------|:--------|:---------|:-------------|
| `task:created` | API / PRD Parser | Scheduler | Neuer Task in der Queue |
| `agent:spawned` | Orchestrator | James™, Dashboard | Agent wurde gestartet |
| `agent:completed` | Agent | Orchestrator | Task abgeschlossen |
| `agent:failed` | Agent | Recovery Manager | Fehler aufgetreten |
| `health:check` | Health Monitor | Alle Agenten | Heartbeat-Request |
| `health:response` | Agent | Health Monitor | Heartbeat-Antwort |
| `ampel:update` | Health Monitor | Dashboard | Ampel-Status geändert |
| `commit:ready` | Developer™ | Reviewer™ | Code zum Review bereit |

---

## 🚦 Fehlerbehandlung & Recovery

Der Orchestrator implementiert ein dreistufiges Fehlerbehandlungs-System mit automatischem Retry und Graceful Degradation.

```javascript
// Fehlerbehandlung mit Retry + Escalation
async function handleAgentFailure(agent, error) {
  agent.state = AgentState.RECOVERY;
  
  // Stufe 1: Auto-Retry (bis 3x)
  if (agent.retries > 0) {
    agent.retries--;
    eventBus.emit('agent:retry', { agent, attempt: 3 - agent.retries });
    return respawnAgent(agent);
  }
  
  // Stufe 2: Graceful Degradation
  eventBus.emit('ampel:update', { status: 'gelb', agent: agent.type });
  
  // Stufe 3: Eskalation an James™
  eventBus.emit('escalation:james', {
    agent: agent.type,
    error: error.message,
    priority: 'P0'
  });
}
```

| Stufe | Trigger | Aktion | Ampel |
|:------|:--------|:-------|:------|
| 1 — Retry | Agent-Fehler | Auto-Respawn (max. 3x) | 🟢 Grün |
| 2 — Degradation | Retry erschöpft | Feature deaktivieren, Dashboard warnen | 🟡 Gelb |
| 3 — Eskalation | Kritischer Fehler | James™ benachrichtigen, 777 alarmieren | 🔴 Rot |

---

## 📡 API-Referenz

| Endpoint | Methode | Beschreibung |
|:---------|:--------|:-------------|
| `/api/swarm/status` | `GET` | Aktueller Swarm-Status aller Agenten |
| `/api/swarm/agents` | `GET` | Liste aktiver Agenten mit State |
| `/api/swarm/spawn` | `POST` | Neuen Agent manuell starten |
| `/api/swarm/kill/:id` | `DELETE` | Agent stoppen |
| `/api/swarm/events` | `WS` | WebSocket-Stream aller Events |
| `/api/swarm/queue` | `GET` | Aktuelle FIFO-Queue einsehen |
| `/api/swarm/health` | `GET` | Health-Check Ergebnis (Ampel) |

---

## ⚙️ Konfiguration

```json
{
  "swarm": {
    "maxConcurrentAgents": 4,
    "queueType": "FIFO",
    "priorities": ["P0", "P1", "P2", "P3"],
    "healthCheckInterval": 30000,
    "agentTimeout": 1800000,
    "maxRetries": 3,
    "gracefulShutdown": true,
    "eventLog": "logs/swarm-events.jsonl",
    "dashboard": {
      "port": 3100,
      "websocket": true,
      "ampelEnabled": true
    }
  }
}
```

---

## 🔗 Verwandte Systeme

| System | Beschreibung | Link |
|:-------|:-------------|:-----|
| 🔄 Ralph-Loop™ | 6-Phasen Execution Pipeline | [ralph-loop/](../ralph-loop/) |
| 🕸️ BotNet™ | Multi-Agent Deployment | [botnet-ops/](../botnet-ops/) |
| 🤖 Copilot Bridge™ | 18 LLM Provider | [copilot-bridge/](../copilot-bridge/) |
| 📨 Hermes™ | Kommunikation & Chat | [hermes-comms/](../hermes-comms/) |
| 🧊 Iceberg™ | Daten-Persistenz | [iceberg-data/](../iceberg-data/) |

---

<div align="center">

**🐝 Agent Swarm™** — Teil des [DEVKiTZ™ Ökosystems](https://github.com/777/devkitz-ecosystem)

`Built with 🔥 by 777 · Powered by BMAD™ · Coordinated by James™`

[![DEVKiTZ](https://img.shields.io/badge/DEVKiTZ™-Ecosystem-fa1e4e?style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZD0iTTEyIDJMMyAyMGgyMEwxMiAyeiIgZmlsbD0iI2ZhMWU0ZSIvPjwvc3ZnPg==)](https://github.com/777/devkitz-ecosystem)

</div>
