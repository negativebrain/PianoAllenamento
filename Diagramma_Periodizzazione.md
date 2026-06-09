# 📊 DIAGRAMMA PERIODIZZAZIONE 6 MESI
## VERSIONE BILANCIATA: Tonificazione + Performance

## Panoramica Visuale del Programma

### Timeline Completa

```mermaid
gantt
    title Piano Allenamento 6 Mesi - Versione Bilanciata (Mezza 1:48-1:50)
    dateFormat YYYY-MM-DD
    section Mesociclo 1
    Base Aerobica + Costruzione Muscolare :m1, 2026-06-09, 56d
    section Mesociclo 2
    Soglia Anaerobica + Ipertrofia Massima :m2, after m1, 56d
    section Mesociclo 3
    Picco Performance + Mantenimento Muscolo :m3a, after m2, 42d
    Tapering :m3b, after m3a, 14d
    section Gare
    MEZZA MARATONA 1:48-1:50 :milestone, after m3b, 1d
```

---

## Progressione Volume Corsa (RIDOTTO per Tonificazione)

```mermaid
graph LR
    A[Settimane 1-4<br/>34-38 km<br/>Lungo MAX 18km] --> B[Settimane 5-8<br/>38-42 km<br/>Lungo MAX 20km]
    B --> C[Settimane 9-12<br/>38-42 km<br/>Lungo MAX 20km]
    C --> D[Settimane 13-16<br/>40-44 km<br/>Lungo MAX 22km]
    D --> E[Settimane 17-20<br/>40-44 km<br/>Lungo MAX 22km]
    E --> F[Settimane 21-22<br/>40-42 km<br/>Lungo MAX 20km]
    F --> G[Settimane 23-24<br/>30-35 km<br/>TAPERING]
    G --> H[GARA<br/>21.1 km<br/>1:48-1:50]
    
    style A fill:#90EE90
    style B fill:#90EE90
    style C fill:#FFD700
    style D fill:#FFD700
    style E fill:#FF6B6B
    style F fill:#FF6B6B
    style G fill:#87CEEB
    style H fill:#FF1493
```

---

## Struttura Settimanale

```mermaid
graph TD
    A[SETTIMANA TIPO] --> B[LUN: Full Body A]
    A --> C[MAR: Ripetute]
    A --> D[MER: Riposo]
    A --> E[GIO: Z2/Tempo]
    A --> F[VEN: Full Body B]
    A --> G[SAB: Lungo]
    A --> H[DOM: Recupero Attivo]
    
    B --> B1[Spinta + Core<br/>45-60 min]
    C --> C1[Velocità Z4-Z5<br/>8-14 km]
    D --> D1[Recupero Completo<br/>Stretching]
    E --> E1[Aerobico Z2-Z3<br/>10-14 km]
    F --> F1[Trazione + Gambe<br/>60 min Ipertrofia]
    G --> G1[Resistenza Z1-Z2<br/>16-22 km MAX 2h]
    H --> H1[Camminata/Bici/Nuoto<br/>30-45 min]
    
    style A fill:#4169E1,color:#fff
    style B fill:#FF6347
    style C fill:#32CD32
    style D fill:#808080
    style E fill:#32CD32
    style F fill:#FF6347
    style G fill:#1E90FF
    style H fill:#FFD700
```

---

## Progressione Intensità Ripetute

```mermaid
graph TB
    subgraph Mesociclo 1
    A1[Sett 1-4<br/>6-8 x 400m<br/>Z4] --> A2[Sett 5-8<br/>5-6 x 800m<br/>Z3-Z4]
    end
    
    subgraph Mesociclo 2
    B1[Sett 9-12<br/>4-5 x 1000m<br/>Z4] --> B2[Sett 13-16<br/>3-4 x 2000m<br/>Z3-Z4]
    end
    
    subgraph Mesociclo 3
    C1[Sett 17-20<br/>5-6 x 1600m<br/>Ritmo Gara] --> C2[Sett 21-22<br/>3 x 3000m<br/>Ritmo Gara]
    C2 --> C3[Sett 23-24<br/>Tapering<br/>Volume ridotto]
    end
    
    A2 --> B1
    B2 --> C1
    
    style A1 fill:#90EE90
    style A2 fill:#90EE90
    style B1 fill:#FFD700
    style B2 fill:#FFD700
    style C1 fill:#FF6B6B
    style C2 fill:#FF6B6B
    style C3 fill:#87CEEB
```

---

## Progressione Forza

```mermaid
graph LR
    subgraph Mesociclo 1: Adattamento
    A[3-4 serie<br/>8-15 reps<br/>Tecnica]
    end
    
    subgraph Mesociclo 2: Ipertrofia
    B[4-5 serie<br/>10-15 reps<br/>Volume alto]
    end
    
    subgraph Mesociclo 3: Forza Max
    C[4-5 serie<br/>6-12 reps<br/>Carico max]
    end
    
    A --> B
    B --> C
    
    style A fill:#90EE90
    style B fill:#FFD700
    style C fill:#FF6B6B
```

---

## Obiettivi per Mesociclo

```mermaid
mindmap
  root((Piano 6 Mesi))
    Mesociclo 1
      Base Aerobica
        Lungo 18-20 km MAX 2h
        Volume 34-42 km
      Costruzione Muscolare
        Push-up 25+ reps
        Ipertrofia iniziale
        Proteine 165-180g
      Composizione
        Perdita 0.5 kg grasso
        Guadagno muscolo
        Surplus giorni forza
    Mesociclo 2
      Soglia Anaerobica
        10 km sotto 55 min
        Volume 38-44 km
      Ipertrofia Massima
        Pistol squat 5+ reps
        Drop sets + superset
        Focus petto/spalle
      Composizione
        Circonferenza -2 cm
        Massa +0.5-1 kg
        BCAA durante lunghi
    Mesociclo 3
      Picco Performance
        10 km sotto 54 min
        Volume 40-44 km
        Lungo MAX 22 km
      Forza Mantenimento
        Carico massimale
        Preservare muscolo
      Obiettivo Finale
        Mezza 1:48-1:50
        Peso 73.5-74.5 kg
        Massa +1-1.5 kg
        Corpo tonico
```

---

## Ciclizzazione Calorica Settimanale

```mermaid
graph TD
    A[Lunedì<br/>Full Body A] --> A1[2650-2750 kcal<br/>SURPLUS +100-200]
    B[Martedì<br/>Ripetute] --> B1[2500-2600 kcal<br/>Manutenzione]
    C[Mercoledì<br/>Riposo] --> C1[2300-2400 kcal<br/>Deficit moderato]
    D[Giovedì<br/>Z2/Tempo] --> D1[2450-2550 kcal<br/>Leggero deficit]
    E[Venerdì<br/>Full Body B] --> E1[2650-2750 kcal<br/>SURPLUS +100-200]
    F[Sabato<br/>Lungo] --> F1[2500-2600 kcal<br/>Manutenzione]
    G[Domenica<br/>Recupero] --> G1[2300-2400 kcal<br/>Deficit moderato]
    
    A1 --> H[Media Settimanale<br/>2500-2600 kcal<br/>Deficit netto -100-150]
    B1 --> H
    C1 --> H
    D1 --> H
    E1 --> H
    F1 --> H
    G1 --> H
    
    style A fill:#FF6347
    style B fill:#32CD32
    style C fill:#808080
    style D fill:#32CD32
    style E fill:#FF6347
    style F fill:#1E90FF
    style G fill:#FFD700
    style H fill:#4169E1,color:#fff
```

---

## Flusso Decisionale Recupero

```mermaid
flowchart TD
    A[Inizio Settimana] --> B{FC riposo<br/>normale?}
    B -->|Sì| C{Sonno<br/>qualità ok?}
    B -->|No +5 bpm| D[Giorno riposo extra]
    
    C -->|Sì| E{Dolori<br/>articolari?}
    C -->|No| D
    
    E -->|No| F[Procedi con<br/>allenamento]
    E -->|Sì| G{Durata<br/>dolore?}
    
    G -->|<3 giorni| F
    G -->|>3 giorni| H[Riposo e<br/>valutazione]
    
    F --> I{Performance<br/>in calo?}
    I -->|No| J[Continua<br/>programma]
    I -->|Sì 2+ sett| K[Settimana<br/>scarico]
    
    D --> L[Riprendi giorno<br/>successivo]
    H --> M[Consulta<br/>fisioterapista]
    K --> J
    
    style A fill:#4169E1,color:#fff
    style F fill:#90EE90
    style J fill:#90EE90
    style D fill:#FFD700
    style H fill:#FF6B6B
    style K fill:#FFD700
    style M fill:#FF6B6B
```

---

## Timeline Test Valutazione

```mermaid
gantt
    title Test Mensili di Valutazione
    dateFormat YYYY-MM-DD
    section Test Running
    5 km TT :t1, 2026-07-31, 1d
    10 km TT :t2, 2026-08-31, 1d
    15 km TT :t3, 2026-09-30, 1d
    10 km TT :t4, 2026-10-31, 1d
    18 km TT :t5, 2026-11-30, 1d
    MEZZA GARA :milestone, t6, 2026-12-31, 1d
    section Test Forza
    Push-up max :f1, 2026-07-31, 1d
    Pull-up max :f2, 2026-08-31, 1d
    Pistol squat :f3, 2026-09-30, 1d
    Dips max :f4, 2026-10-31, 1d
    Pull-up max :f5, 2026-11-30, 1d
    Test completo :f6, 2026-12-31, 1d
```

---

## Progressione Lungo Sabato

```mermaid
graph TD
    subgraph Settimane 1-8
    A[Sett 1: 16 km] --> B[Sett 2: 18 km]
    B --> C[Sett 3: 20 km]
    C --> D[Sett 4: 14 km SCARICO]
    D --> E[Sett 5: 22 km]
    E --> F[Sett 6: 24 km]
    F --> G[Sett 7: 26 km]
    G --> H[Sett 8: 16 km SCARICO]
    end
    
    subgraph Settimane 9-16
    I[Sett 9: 24 km] --> J[Sett 10: 26 km]
    J --> K[Sett 11: 28 km]
    K --> L[Sett 12: 18 km SCARICO]
    L --> M[Sett 13: 22 km TRAIL]
    M --> N[Sett 14: 30 km]
    N --> O[Sett 15: 24 km TRAIL]
    O --> P[Sett 16: 20 km SCARICO]
    end
    
    subgraph Settimane 17-24
    Q[Sett 17: 28 km] --> R[Sett 18: 30 km]
    R --> S[Sett 19: 32 km PICCO]
    S --> T[Sett 20: 20 km SCARICO]
    T --> U[Sett 21: 26 km]
    U --> V[Sett 22: 24 km TRAIL]
    V --> W[Sett 23: 16 km TAPER]
    W --> X[Sett 24: GARA 21.1 km]
    end
    
    H --> I
    P --> Q
    
    style D fill:#FFD700
    style H fill:#FFD700
    style L fill:#FFD700
    style P fill:#FFD700
    style T fill:#FFD700
    style W fill:#87CEEB
    style X fill:#FF1493
```

---

## Legenda Colori

```mermaid
graph LR
    A[Mesociclo 1<br/>Base] 
    B[Mesociclo 2<br/>Costruzione]
    C[Mesociclo 3<br/>Picco]
    D[Tapering]
    E[Gara]
    F[Scarico]
    
    style A fill:#90EE90
    style B fill:#FFD700
    style C fill:#FF6B6B
    style D fill:#87CEEB
    style E fill:#FF1493
    style F fill:#FFD700
```

**Verde:** Fase base/adattamento  
**Giallo:** Fase costruzione/ipertrofia  
**Rosso:** Fase picco/intensità massima  
**Azzurro:** Tapering pre-gara  
**Rosa:** Gara obiettivo  
**Giallo scuro:** Settimane scarico

---

## Note sui Diagrammi

Questi diagrammi visualizzano:

1. **Timeline generale:** Panoramica dei 3 mesocicli e progressione temporale
2. **Volume corsa:** Aumento graduale del chilometraggio settimanale
3. **Struttura settimanale:** Distribuzione allenamenti nei 7 giorni
4. **Progressione ripetute:** Evoluzione da 400m a 3000m
5. **Progressione forza:** Da adattamento a forza massima
6. **Obiettivi mesociclo:** Traguardi intermedi per ogni fase
7. **Ciclizzazione calorica:** Gestione calorie durante la settimana
8. **Flusso recupero:** Processo decisionale per gestire affaticamento
9. **Test valutazione:** Calendario test mensili
10. **Progressione lungo:** Evoluzione corsa lunga del sabato

Usa questi diagrammi come riferimento visivo rapido per comprendere la struttura e progressione del programma.

---

*Per dettagli completi, consulta: [`Piano_Allenamento_6_Mesi.md`](Piano_Allenamento_6_Mesi.md)*