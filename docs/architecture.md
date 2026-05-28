# 📐 Architektur

## System-Übersicht

```mermaid
graph TB
    subgraph GATEWAY["🌐 API Gateway"]
        GW["Gateway / MCP"]
    end
    
    subgraph SWARM["🐝 Agent Swarm"]
        MC["🎛️ Mission Control"]
        J["🎯 James™ Guardian"]
        
        subgraph BMAD["BMAD™ Agenten"]
            PM["📋 PM"] --> AR["🏗️ Architekt"]
            AR --> DEV["👨‍💻 Developer"]
            DEV --> REV["🔍 Reviewer"]
            DEV --> TEST["🧪 Tester"]
            REV --> DOK["📚 Dokumentar"]
        end
    end
    
    subgraph INFRA["⚙️ Infrastruktur"]
        BN["🕸️ BotNet™"]
        CB["🤖 Copilot Bridge"]
        H["📨 Hermes™"]
        ICE["🧊 Iceberg™"]
        RL["🔄 Ralph-Loop™"]
    end
    
    GW --> MC
    MC --> J
    J --> BMAD
    J --> RL
    RL --> DEV
    CB --> |"18 Provider"| GW
    H --> MC
    ICE --> MC
    BN --> BMAD
    
    style GATEWAY fill:#fa1e4e,color:#fff
    style MC fill:#ffb800,color:#060608
    style J fill:#fa1e4e,color:#fff
```

## Datenfluss

1. **Request** → API Gateway → Mission Control
2. **Routing** → James™ analysiert Task → delegiert an Agent
3. **Execution** → Ralph-Loop™ (6 Phasen)
4. **Persistenz** → Iceberg™ (Dreifach-Verankerung)
5. **Kommunikation** → Hermes™ (Matrix + NanoChat)
