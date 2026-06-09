# 🚀 Guida Implementazione Step-by-Step

## 📋 Indice

1. [Preparazione Iniziale](#preparazione-iniziale)
2. [Setup Piattaforma](#setup-piattaforma)
3. [Configurazione Database](#configurazione-database)
4. [Implementazione Autenticazione](#implementazione-autenticazione)
5. [Sezione Corsa](#sezione-corsa)
6. [Sezione Full Body](#sezione-full-body)
7. [Sezione Alimentazione](#sezione-alimentazione)
8. [Integrazione Garmin](#integrazione-garmin)
9. [Integrazione Claude AI](#integrazione-claude-ai)
10. [Testing e Deploy](#testing-e-deploy)

---

## 1. Preparazione Iniziale

### 1.1 Requisiti

**Account Necessari:**
- [ ] Account Google (per OAuth)
- [ ] Account Bubble.io o Softr + Airtable
- [ ] Account Garmin Developer (per API)
- [ ] Account Anthropic (per Claude AI)

**Strumenti Consigliati:**
- Browser moderno (Chrome, Firefox, Safari)
- Editor di testo (per note e configurazioni)
- Postman o simili (per testare API)

### 1.2 Checklist Pre-Implementazione

```
✓ Decisione piattaforma (Bubble.io vs Softr+Airtable)
✓ Registrazione account necessari
✓ Lettura documentazione completa
✓ Preparazione contenuti (loghi, immagini)
✓ Piano di backup dati
```

### 1.3 Struttura Progetto

```
fitness-tracker/
├── docs/
│   ├── PROGETTO_SITO_FITNESS.md
│   ├── MOCKUP_UI.md
│   ├── GUIDA_IMPLEMENTAZIONE.md
│   ├── SCHEMA_DATABASE.md
│   ├── INTEGRAZIONE_GARMIN.md
│   └── INTEGRAZIONE_AI.md
├── assets/
│   ├── images/
│   ├── icons/
│   └── fonts/
├── config/
│   ├── api-keys.txt (NON committare!)
│   └── settings.json
└── backups/
    └── [backup files]
```

---

## 2. Setup Piattaforma

### Opzione A: Bubble.io

#### 2.1 Creazione Account e App

**Step 1: Registrazione**
```
1. Vai su https://bubble.io
2. Click "Get started for free"
3. Compila form registrazione
4. Verifica email
5. Login al dashboard
```

**Step 2: Creazione App**
```
1. Click "New app"
2. Nome: "FitnessTracker"
3. Template: "Blank" (partiamo da zero)
4. Click "Create app"
```

**Step 3: Configurazione Iniziale**
```
1. Settings → General
   - App name: Fitness Tracker
   - App description: Personal fitness tracking app
   
2. Settings → SEO/metatags
   - Title: Fitness Tracker - Track Your Progress
   - Description: Complete fitness tracking with AI analysis
   
3. Settings → Languages
   - Primary language: Italian (it)
   - Add translations se necessario
```

#### 2.2 Setup Editor

**Layout Principale:**
```
1. Design → Responsive settings
   - Enable responsive: ✓
   - Mobile breakpoint: 768px
   
2. Styles → Create new style
   - Primary Button
   - Secondary Button
   - Card Container
   - Input Field
   
3. Reusable Elements
   - Header
   - Navigation
   - Footer
```

**Plugins Necessari:**
```
1. Plugins → Add plugins
   - Google OAuth
   - API Connector
   - Chart.js (per grafici)
   - Date/Time Picker
   
2. Installa e configura ciascun plugin
```

### Opzione B: Softr + Airtable

#### 2.1 Setup Airtable

**Step 1: Creazione Base**
```
1. Vai su https://airtable.com
2. Click "Add a base"
3. Nome: "Fitness Tracker DB"
4. Crea tabelle (vedi SCHEMA_DATABASE.md)
```

**Step 2: Configurazione Tabelle**
```
Tabelle da creare:
1. Users
2. Running_Activities
3. Workouts
4. Exercises
5. Meals
6. Foods
7. Body_Metrics
8. Goals

(Vedi dettagli in SCHEMA_DATABASE.md)
```

**Step 3: API Setup**
```
1. Account → API documentation
2. Copia Base ID
3. Genera API Key
4. Salva in config/api-keys.txt
```

#### 2.2 Setup Softr

**Step 1: Creazione App**
```
1. Vai su https://softr.io
2. Click "Build from Airtable"
3. Connetti account Airtable
4. Seleziona base "Fitness Tracker DB"
5. Scegli template "Blank"
```

**Step 2: Configurazione Iniziale**
```
1. Settings → General
   - App name: Fitness Tracker
   - Subdomain: fitness-tracker-[yourname]
   
2. Settings → Branding
   - Logo
   - Colors (vedi MOCKUP_UI.md)
   - Fonts: Inter
```

---

## 3. Configurazione Database

### 3.1 Schema Database (Bubble.io)

**Data Types da Creare:**

```
1. User (built-in, estendere)
   - google_id: text
   - age: number
   - height: number
   - weight: number
   - target_weight: number
   - gender: text
   - hr_max: number
   - hr_rest: number
   - created_at: date

2. Running_Activity
   - user: User
   - date: date
   - type: text (Facile, Medio, Lungo, Veloce)
   - distance_km: number
   - duration_seconds: number
   - avg_pace: text
   - avg_hr: number
   - max_hr: number
   - cadence: number
   - elevation: number
   - calories: number
   - hr_zones: text (JSON)
   - notes: text
   - garmin_activity_id: text
   - created_at: date

3. Workout
   - user: User
   - date: date
   - workout_type: text (PUSH, PULL, LEGS, FULL)
   - exercises: text (JSON array)
   - duration_minutes: number
   - total_volume_kg: number
   - rpe: number
   - notes: text
   - created_at: date

4. Exercise
   - name: text
   - category: text (PUSH, PULL, LEGS)
   - muscle_groups: text
   - description: text
   - video_url: text
   - image_url: text
   - created_at: date

5. Meal
   - user: User
   - date: date
   - meal_type: text (Colazione, Pranzo, Cena, Snack)
   - foods: text (JSON array)
   - total_calories: number
   - total_protein: number
   - total_carbs: number
   - total_fats: number
   - notes: text
   - created_at: date

6. Food
   - name: text
   - category: text (Proteine, Carboidrati, Grassi)
   - calories_per_100g: number
   - protein_per_100g: number
   - carbs_per_100g: number
   - fats_per_100g: number
   - created_at: date

7. Body_Metric
   - user: User
   - date: date
   - weight: number
   - water_intake_ml: number
   - notes: text
   - created_at: date

8. Goal
   - user: User
   - goal_type: text (running, workout, nutrition)
   - target_value: number
   - current_value: number
   - period: text (daily, weekly, monthly)
   - created_at: date
```

**Creazione in Bubble:**
```
1. Data → Data types → New type
2. Per ogni tipo sopra:
   - Inserisci nome
   - Aggiungi campi uno per uno
   - Imposta tipo campo corretto
   - Salva
```

### 3.2 Privacy Rules (Bubble.io)

```
Per ogni Data Type:

1. Running_Activity
   Rule: User can view own activities
   - When: Current User = This Running_Activity's user
   - View all fields: ✓
   - Modify all fields: ✓

2. Workout
   Rule: User can view own workouts
   - When: Current User = This Workout's user
   - View all fields: ✓
   - Modify all fields: ✓

3. Meal
   Rule: User can view own meals
   - When: Current User = This Meal's user
   - View all fields: ✓
   - Modify all fields: ✓

4. Exercise (pubblico)
   Rule: Everyone can view
   - View all fields: ✓
   - Modify: Only admin

5. Food (pubblico)
   Rule: Everyone can view
   - View all fields: ✓
   - Modify: Only admin
```

### 3.3 Popolamento Dati Iniziali

**Esercizi Base:**
```sql
-- Crea questi esercizi nel database

PUSH:
- Panca Piana con Bilanciere
- Military Press
- Dips
- Alzate Laterali
- French Press
- Push-up

PULL:
- Trazioni alla Sbarra
- Rematore con Bilanciere
- Lat Machine
- Curl con Bilanciere
- Face Pull
- Shrug

LEGS:
- Squat con Bilanciere
- Stacco da Terra
- Leg Press
- Leg Curl
- Leg Extension
- Calf Raise
```

**Alimenti Base:**
```sql
-- Crea questi alimenti nel database

PROTEINE:
- Petto di Pollo (165 kcal, 31g P, 0g C, 3.6g F per 100g)
- Salmone (208 kcal, 20g P, 0g C, 13g F per 100g)
- Uova (155 kcal, 13g P, 1.1g C, 11g F per 100g)
- Tonno al naturale (116 kcal, 26g P, 0g C, 0.8g F per 100g)
- Yogurt Greco 0% (59 kcal, 10g P, 3.6g C, 0.4g F per 100g)

CARBOIDRATI:
- Riso Basmati (350 kcal, 8g P, 77g C, 0.6g F per 100g)
- Pasta Integrale (348 kcal, 13g P, 67g C, 2.5g F per 100g)
- Avena (389 kcal, 17g P, 66g C, 7g F per 100g)
- Patate Dolci (86 kcal, 1.6g P, 20g C, 0.1g F per 100g)
- Banana (89 kcal, 1.1g P, 23g C, 0.3g F per 100g)

GRASSI:
- Olio EVO (884 kcal, 0g P, 0g C, 100g F per 100ml)
- Mandorle (579 kcal, 21g P, 22g C, 50g F per 100g)
- Avocado (160 kcal, 2g P, 9g C, 15g F per 100g)
```

---

## 4. Implementazione Autenticazione

### 4.1 Google OAuth Setup

**Step 1: Google Cloud Console**
```
1. Vai su https://console.cloud.google.com
2. Crea nuovo progetto "Fitness Tracker"
3. Abilita Google+ API
4. Credentials → Create credentials → OAuth 2.0 Client ID
5. Application type: Web application
6. Authorized redirect URIs:
   - Bubble: https://[your-app].bubbleapps.io/api/1.1/oauth_redirect
   - Softr: https://[your-app].softr.app/oauth/callback
7. Copia Client ID e Client Secret
```

**Step 2: Configurazione in Bubble**
```
1. Plugins → Google
2. Paste Client ID
3. Paste Client Secret
4. Scopes: email, profile
5. Save
```

**Step 3: Configurazione in Softr**
```
1. Settings → Authentication
2. Enable Google OAuth
3. Paste Client ID
4. Paste Client Secret
5. Save
```

### 4.2 Pagina Login

**Bubble Implementation:**
```
1. Crea pagina "index" (homepage/login)
2. Add element → Button
   - Text: "Accedi con Google"
   - Icon: Google logo
   - Style: Primary button
   
3. Workflow:
   - When Button is clicked
   - Account → Signup/login with a social network
   - OAuth provider: Google
   - Navigate to: dashboard
```

**Design Login Page:**
```
Layout:
- Centered container
- Logo app (top)
- Tagline
- Google login button
- Terms & Privacy links
- Features list (bottom)

Responsive:
- Mobile: Stack vertically
- Desktop: Centered card
```

### 4.3 Onboarding Flow

**Pagine da Creare:**
```
1. onboarding-1 (Dati personali)
2. onboarding-2 (Obiettivi)
3. onboarding-3 (Connessioni)
4. onboarding-4 (Completamento)
```

**Workflow Onboarding:**
```
1. Dopo login, check if User's onboarding_completed = no
2. If no → Navigate to onboarding-1
3. If yes → Navigate to dashboard

Onboarding-1:
- Form: nome, età, altezza, peso, sesso
- Button "Continua" → Save to User → Navigate to onboarding-2

Onboarding-2:
- Checkboxes: obiettivi
- Inputs: km settimanali, workout settimanali
- Button "Continua" → Save to User → Navigate to onboarding-3

Onboarding-3:
- Button "Connetti Garmin" (opzionale)
- Button "Salta" → Navigate to onboarding-4

Onboarding-4:
- Riepilogo configurazione
- Button "Inizia" → Set onboarding_completed = yes → Navigate to dashboard
```

---

## 5. Sezione Corsa

### 5.1 Dashboard Corsa

**Pagina: running-dashboard**

**Elementi da Creare:**

```
1. Header
   - Titolo "CORSA"
   - Button "+ Nuova Corsa"

2. Stats Cards (Repeating Group)
   - Data source: Do a search for Running_Activity
   - Constraints: user = Current User, date ≥ first day of current month
   - Display:
     * Total distance (sum)
     * Total time (sum)
     * Average pace (average)
     * Average HR (average)

3. Chart - Trend Passo
   - Plugin: Chart.js
   - Type: Line
   - Data: Last 30 days activities
   - X-axis: Date
   - Y-axis: Pace

4. Chart - Zone FC
   - Plugin: Chart.js
   - Type: Pie
   - Data: HR zones distribution
   - Labels: Z1, Z2, Z3, Z4, Z5

5. Repeating Group - Lista Attività
   - Data source: Do a search for Running_Activity
   - Constraints: user = Current User
   - Sort: date descending
   - Items per page: 10
   - Display: Card per attività
```

**Workflows:**
```
1. When "+ Nuova Corsa" is clicked
   → Navigate to: running-form

2. When "Dettagli" is clicked
   → Navigate to: running-detail
   → Send data: Current cell's Running_Activity

3. When "Modifica" is clicked
   → Navigate to: running-form
   → Send data: Current cell's Running_Activity

4. When "Elimina" is clicked
   → Show confirmation popup
   → If confirmed: Delete Current cell's Running_Activity
   → Refresh Repeating Group
```

### 5.2 Form Nuova Corsa

**Pagina: running-form**

**Form Elements:**
```
1. Date Picker - Data
   - Default: Current date/time

2. Dropdown - Tipo Allenamento
   - Options: Facile, Medio, Lungo, Veloce, Recupero

3. Input - Distanza (km)
   - Type: number
   - Placeholder: 10.5

4. Input - Durata
   - Type: text
   - Format: HH:MM:SS
   - Placeholder: 00:51:23

5. Input - FC Media
   - Type: number
   - Placeholder: 142

6. Input - FC Max
   - Type: number
   - Placeholder: 165

7. Group - Zone FC (opzionale)
   - 5 inputs per Z1-Z5 (percentuali)

8. Input - Calorie
   - Type: number
   - Placeholder: 520

9. Text Area - Note
   - Placeholder: Sensazioni, condizioni meteo...

10. Button - Salva Corsa
```

**Workflows:**
```
1. When "Salva Corsa" is clicked
   
   Step 1: Calcola passo medio
   - duration_seconds / distance_km / 60
   - Format as MM:SS
   
   Step 2: Create Running_Activity
   - user = Current User
   - date = Date Picker's value
   - type = Dropdown's value
   - distance_km = Input Distanza's value
   - duration_seconds = Convert time to seconds
   - avg_pace = Calculated pace
   - avg_hr = Input FC Media's value
   - max_hr = Input FC Max's value
   - calories = Input Calorie's value
   - notes = Text Area's value
   - hr_zones = JSON with Z1-Z5 values
   - created_at = Current date/time
   
   Step 3: Navigate to running-dashboard
   Step 4: Show success message
```

**Validazioni:**
```
1. Distanza > 0
2. Durata > 0
3. FC Media < FC Max
4. Zone FC totale = 100% (se compilate)
```

### 5.3 Dettaglio Corsa

**Pagina: running-detail**

**Data Source:**
```
Type: Running_Activity
Get data from page URL parameter
```

**Elementi:**
```
1. Header
   - Tipo allenamento
   - Data e ora
   - Buttons: Modifica, Elimina

2. Stats Grid
   - 8 cards con metriche principali
   - Distanza, Durata, Passo, FC Media, FC Max, Cadenza, Elevazione, Calorie

3. Chart - FC nel Tempo
   - Se disponibili dati dettagliati da Garmin
   - Altrimenti: placeholder

4. Chart - Zone FC
   - Pie chart con distribuzione

5. Table - Split per Km
   - Se disponibili dati dettagliati
   - Altrimenti: calcolo semplificato

6. Text - Note
   - Display note utente

7. AI Analysis Section
   - Placeholder per analisi AI
   - Button "Richiedi Analisi"
```

---

## 6. Sezione Full Body

### 6.1 Dashboard Workout

**Pagina: workout-dashboard**

**Elementi:**
```
1. Header
   - Titolo "FULL BODY"
   - Button "+ Nuovo Workout"

2. Stats Cards
   - Workout questo mese
   - Tempo totale
   - Volume totale (kg)
   - RPE medio

3. Chart - Progressione Forza
   - Line chart
   - Multi-serie per esercizi principali
   - Ultimi 3 mesi

4. Top 5 Esercizi
   - Lista ordinata per volume

5. Libreria Esercizi
   - Repeating Group
   - Data source: Exercise
   - Filtri per categoria
   - Search box

6. Storico Workout
   - Repeating Group
   - Data source: Workout
   - Sort: date descending
```

**Workflows:**
```
1. When "+ Nuovo Workout" is clicked
   → Navigate to: workout-form

2. When "Dettagli" workout is clicked
   → Navigate to: workout-detail
   → Send data: Current cell's Workout

3. When "Ripeti Workout" is clicked
   → Navigate to: workout-form
   → Pre-fill with previous workout data

4. When Exercise card is clicked
   → Show popup with exercise details
   → Display: description, video, progression chart
```

### 6.2 Form Nuovo Workout

**Pagina: workout-form**

**Structure:**
```
1. Header
   - Data/Ora picker
   - Dropdown tipo workout

2. Repeating Group - Esercizi
   - Add/Remove esercizi
   - Per ogni esercizio:
     * Dropdown selezione esercizio
     * Repeating Group serie
       - Input peso
       - Input ripetizioni
       - Input tempo recupero
       - Button "Aggiungi serie"

3. Input - Durata totale
4. Slider - RPE (1-10)
5. Text Area - Note
6. Button - Salva Workout
```

**Workflows:**
```
1. When "Aggiungi Esercizio" is clicked
   → Add item to exercises list
   → Show new exercise form

2. When "Aggiungi Serie" is clicked
   → Add item to series list for current exercise

3. When "Salva Workout" is clicked
   
   Step 1: Calcola volume totale
   - Sum of (peso × ripetizioni) for all series
   
   Step 2: Create JSON structure
   exercises: [
     {
       exercise_id: "...",
       exercise_name: "...",
       series: [
         {peso: 75, reps: 8, rest: 90},
         {peso: 75, reps: 8, rest: 90},
         ...
       ]
     },
     ...
   ]
   
   Step 3: Create Workout
   - user = Current User
   - date = Date Picker's value
   - workout_type = Dropdown's value
   - exercises = JSON structure
   - duration_minutes = Input's value
   - total_volume_kg = Calculated volume
   - rpe = Slider's value
   - notes = Text Area's value
   
   Step 4: Navigate to workout-dashboard
   Step 5: Show success message
```

### 6.3 Timer Workout (Opzionale)

**Pagina: workout-timer**

**Funzionalità:**
```
1. Display esercizio corrente
2. Display serie corrente
3. Timer recupero
   - Countdown da tempo impostato
   - Visual progress bar
   - Sound/vibration al termine

4. Buttons:
   - Play/Pause
   - Skip serie
   - Complete serie
   - End workout

5. Stats in tempo reale:
   - Tempo totale
   - Volume accumulato
   - Serie completate
```

**Implementation:**
```
Use custom states:
- current_exercise (number)
- current_series (number)
- timer_seconds (number)
- is_resting (yes/no)

Workflows:
- Every 1 second: Decrease timer_seconds
- When timer_seconds = 0: Play sound, show "Serie completata"
- When "Complete serie": Move to next series
- When "Skip": Move to next series without timer
```

---

## 7. Sezione Alimentazione

### 7.1 Dashboard Alimentazione

**Pagina: nutrition-dashboard**

**Elementi:**
```
1. Header
   - Titolo "ALIMENTAZIONE"
   - Date picker (default: oggi)
   - Button "+ Aggiungi Pasto"

2. Daily Summary
   - Obiettivi vs Attuale
   - Progress bars per:
     * Calorie
     * Proteine
     * Carboidrati
     * Grassi
   - Idratazione

3. Repeating Group - Pasti di Oggi
   - Data source: Do a search for Meal
   - Constraints: user = Current User, date = Selected date
   - Sort: date ascending
   - Display: Card per pasto con dettagli

4. Chart - Trend Settimanale
   - Line chart calorie giornaliere
   - Ultimi 7 giorni

5. Chart - Peso Corporeo
   - Line chart peso
   - Ultimi 30 giorni

6. AI Analysis Section
   - Consigli nutrizionali
   - Button "Richiedi Analisi"
```

**Workflows:**
```
1. When "+ Aggiungi Pasto" is clicked
   → Navigate to: meal-form

2. When Date picker changes
   → Refresh Repeating Group
   → Recalculate daily totals

3. When "Modifica" pasto is clicked
   → Navigate to: meal-form
   → Send data: Current cell's Meal

4. When "Elimina" pasto is clicked
   → Delete Current cell's Meal
   → Refresh page
```

### 7.2 Form Aggiungi Pasto

**Pagina: meal-form**

**Structure:**
```
1. Dropdown - Tipo Pasto
   - Colazione, Spuntino Mattina, Pranzo, Spuntino Pomeriggio, Cena, Spuntino Sera

2. Date/Time Picker

3. Repeating Group - Alimenti
   - Search box per cercare alimenti
   - Dropdown o autocomplete
   - Per ogni alimento:
     * Nome alimento
     * Input quantità (g)
     * Display calorie calcolate
     * Display macros calcolati
     * Button "Rimuovi"

4. Button "+ Aggiungi Alimento"

5. Summary Box
   - Totale calorie
   - Totale proteine
   - Totale carboidrati
   - Totale grassi

6. Text Area - Note

7. Button - Salva Pasto
```

**Workflows:**
```
1. When "Aggiungi Alimento" is clicked
   → Show search popup
   → User selects food
   → Add to foods list

2. When quantity changes
   → Recalculate calories and macros
   → Update summary

3. When "Salva Pasto" is clicked
   
   Step 1: Create JSON structure
   foods: [
     {
       food_id: "...",
       food_name: "...",
       quantity_g: 200,
       calories: 330,
       protein: 62,
       carbs: 0,
       fats: 7
     },
     ...
   ]
   
   Step 2: Calculate totals
   - Sum calories
   - Sum protein
   - Sum carbs
   - Sum fats
   
   Step 3: Create Meal
   - user = Current User
   - date = Date Picker's value
   - meal_type = Dropdown's value
   - foods = JSON structure
   - total_calories = Calculated
   - total_protein = Calculated
   - total_carbs = Calculated
   - total_fats = Calculated
   - notes = Text Area's value
   
   Step 4: Navigate to nutrition-dashboard
   Step 5: Show success message
```

### 7.3 Database Alimenti

**Pagina: foods-database**

**Elementi:**
```
1. Search box
2. Filters:
   - Categoria (Proteine, Carboidrati, Grassi, Verdure)
   - Sort by (Nome, Calorie, Proteine)

3. Repeating Group - Alimenti
   - Data source: Food
   - Display: Table format
   - Columns: Nome, Calorie/100g, P, C, F

4. Button "+ Nuovo Alimento" (admin only)
```

**Form Nuovo Alimento:**
```
1. Input - Nome
2. Dropdown - Categoria
3. Input - Calorie per 100g
4. Input - Proteine per 100g
5. Input - Carboidrati per 100g
6. Input - Grassi per 100g
7. Button - Salva
```

---

## 8. Integrazione Garmin

**Vedi INTEGRAZIONE_GARMIN.md per dettagli completi**

### 8.1 Quick Setup

```
1. Registra app su Garmin Developer Portal
2. Ottieni Consumer Key e Consumer Secret
3. Configura OAuth 1.0a in Bubble/Softr
4. Implementa sync workflow
5. Test connessione
```

### 8.2 Sync Workflow

```
1. Button "Sincronizza Garmin"
2. API Call: GET /activities
3. For each activity:
   - Check if already exists (garmin_activity_id)
   - If not: Create Running_Activity
   - Parse data and populate fields
4. Show success message with count
```

---

## 9. Integrazione Claude AI

**Vedi INTEGRAZIONE_AI.md per dettagli completi**

### 9.1 Quick Setup

```
1. Ottieni API key da Anthropic
2. Configura API Connector in Bubble
3. Crea workflow per analisi
4. Implementa UI per mostrare risultati
```

### 9.2 Analisi Workflow

```
1. Button "Richiedi Analisi"
2. Collect user data:
   - Last 30 days activities
   - Goals
   - Current metrics
3. Format prompt for Claude
4. API Call to Claude
5. Parse response
6. Display insights in UI
```

---

## 10. Testing e Deploy

### 10.1 Testing Checklist

**Funzionalità:**
```
✓ Login/Logout
✓ Onboarding flow
✓ CRUD Corsa
✓ CRUD Workout
✓ CRUD Alimentazione
✓ Grafici e statistiche
✓ Sync Garmin
✓ Analisi AI
✓ Responsive mobile
✓ Performance
```

**Browser Testing:**
```
✓ Chrome (desktop + mobile)
✓ Firefox
✓ Safari (desktop + mobile)
✓ Edge
```

**Device Testing:**
```
✓ iPhone (Safari)
✓ Android (Chrome)
✓ iPad
✓ Desktop (1920x1080)
✓ Laptop (1366x768)
```

### 10.2 Performance Optimization

**Bubble.io:**
```
1. Enable caching where possible
2. Optimize database searches:
   - Use constraints efficiently
   - Limit results
   - Use pagination

3. Optimize images:
   - Compress before upload
   - Use appropriate sizes
   - Lazy loading

4. Minimize workflows:
   - Combine actions
   - Use custom events
   - Avoid nested searches
```

**Softr:**
```
1. Optimize Airtable views
2. Use formulas in Airtable (not in Softr)
3. Limit records per page
4. Cache static content
```

### 10.3 Deploy

**Bubble.io:**
```
1. Settings → Domain/email
   - Choose subdomain or custom domain
   
2. Settings → SEO
   - Verify all meta tags
   
3. Deploy to live:
   - Click "Deploy to live"
   - Test on live version
   
4. Monitor:
   - Logs
   - Server capacity
   - User feedback
```

**Softr:**
```
1. Settings → Domain
   - Use subdomain or custom domain
   
2. Publish changes:
   - Click "Publish"
   - Changes live immediately
   
3. Monitor:
   - Airtable usage
   - Page views
   - User feedback
```

### 10.4 Backup Strategy

```
1. Bubble.io:
   - Automatic backups by Bubble
   - Manual export: Settings → App data → Download
   
2. Airtable:
   - Automatic backups by Airtable
   - Manual export: CSV per table
   
3. Schedule:
   - Weekly manual backup
   - Before major changes
   - Keep last 4 backups
```

### 10.5 Monitoring

**Metriche da Monitorare:**
```
1. Uptime
2. Response time
3. Error rate
4. User registrations
5. Daily active users
6. Feature usage
7. API calls (Garmin, Claude)
```

**Tools:**
```
- Google Analytics (free)
- Hotjar (heatmaps, recordings)
- Bubble logs (built-in)
- Airtable usage dashboard
```

---

## 11. Manutenzione

### 11.1 Routine Settimanale

```
✓ Check error logs
✓ Review user feedback
✓ Monitor API usage
✓ Check database size
✓ Test critical flows
✓ Update content if needed
```

### 11.2 Routine Mensile

```
✓ Full backup
✓ Performance review
✓ Security audit
✓ Update dependencies
✓ Review analytics
✓ Plan improvements
```

### 11.3 Aggiornamenti

**Priorità:**
```
1. Security fixes (immediate)
2. Critical bugs (24-48h)
3. User-requested features (planned)
4. Nice-to-have features (backlog)
```

**Process:**
```
1. Test in development
2. User acceptance testing
3. Deploy to live
4. Monitor for issues
5. Rollback if needed
```

---

## 12. Troubleshooting

### 12.1 Problemi Comuni

**Login non funziona:**
```
- Verifica OAuth credentials
- Check redirect URIs
- Clear browser cache
- Test in incognito
```

**Dati non si salvano:**
```
- Check privacy rules
- Verify workflows
- Check database constraints
- Review error logs
```

**Grafici non si caricano:**
```
- Verify data source
- Check plugin configuration
- Test with sample data
- Review browser console
```

**Sync Garmin fallisce:**
```
- Verify API credentials
- Check token expiration
- Review API limits
- Test with Postman
```

**Analisi AI non risponde:**
```
- Verify API key
- Check API limits
- Review prompt format
- Test with simple request
```

### 12.2 Supporto

**Risorse:**
```
- Bubble Forum: forum.bubble.io
- Softr Community: community.softr.io
- Garmin Developer: developer.garmin.com/forum
- Anthropic Docs: docs.anthropic.com
- Stack Overflow
```

**Contatti:**
```
- Bubble Support: support@bubble.io
- Softr Support: support@softr.io
- Community Discord/Slack
```

---

## 13. Prossimi Passi

### 13.1 Dopo il Launch

```
Settimana 1-2:
✓ Monitor closely
✓ Fix critical bugs
✓ Collect user feedback
✓ Quick improvements

Mese 1:
✓ Analyze usage patterns
✓ Implement top requests
✓ Optimize performance
✓ Plan v1.1 features

Mese 2-3:
✓ Add advanced features
✓ Improve AI analysis
✓ Enhance UI/UX
✓ Marketing push
```

### 13.2 Roadmap Futuro

**V1.1 (1-2 mesi):**
```
- Notifiche push
- Export PDF reports
- Social sharing
- Workout templates
```

**V1.2 (3-4 mesi):**
```
- Mobile app (PWA)
- Apple Health integration
- Advanced analytics
- Coach mode
```

**V2.0 (6+ mesi):**
```
- Native mobile apps
- Community features
- Marketplace
- Premium features
```

---

## 📚 Risorse Aggiuntive

### Video Tutorial
- [Bubble.io Crash Course](https://www.youtube.com/bubble)
- [Softr Tutorial Series](https://www.youtube.com/softr)
- [Airtable Basics](https://www.youtube.com/airtable)

### Documentazione
- [Bubble Manual](https://manual.bubble.io)
- [Softr University](https://university.softr.io)
- [Airtable Support](https://support.airtable.com)
- [Garmin API Docs](https://developer.garmin.com)
- [Claude API Docs](https://docs.anthropic.com)

### Community
- [Bubble Forum](https://forum.bubble.io)
- [Softr Community](https://community.softr.io)
- [Reddit r/nocode](https://reddit.com/r/nocode)
- [Reddit r/Bubble](https://reddit.com/r/Bubble)

---

**Versione:** 1.0  
**Data:** Giugno 2026  
**Autore:** Bob - Software Engineer  
**Licenza:** MIT

**Buona implementazione! 🚀**