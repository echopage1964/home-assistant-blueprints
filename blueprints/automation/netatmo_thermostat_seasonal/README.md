# 🧩 Termostato Netatmo con Logica Stagionale

Blueprint per Home Assistant che gestisce il termostato Netatmo in modo intelligente, tenendo conto della temperatura interna, esterna, della stagione e di condizioni ambientali come presenza e finestra aperta.

---

## 🎯 Funzionalità

- Controllo dinamico del riscaldamento basato su soglie configurabili
- Logica stagionale: soglie diverse per estate e inverno
- Supporto per sensori di presenza e finestra aperta
- Modalità Netatmo configurabile (`manual`, `away`, `frost guard`)
- Intervallo di controllo ogni 5 minuti

---

## 📦 Requisiti

- Integrazione Netatmo attiva in Home Assistant
- Sensore temperatura interna (es. `sensor.netatmo_salon_temperature`)
- Sensore temperatura esterna (es. `sensor.netatmo_giardino_temperature`)
- (Facoltativi) Sensore di presenza e sensore finestra aperta

---

## ⚙️ Parametri configurabili

| Nome nella UI | Chiave YAML | Descrizione |
|-----------------------------|----------------------------|-----------------------------|
| Termostato Netatmo | `climate_entity` | Entità del termostato da controllare |
| Sensore temperatura interna | `internal_temp_sensor` | Sensore che rileva la temperatura interna |
| Sensore temperatura esterna | `external_temp_sensor` | Sensore che rileva la temperatura esterna |
| Soglia minima interna in inverno | `winter_min_temp` | Temperatura sotto la quale si accende il riscaldamento in inverno |
| Soglia massima interna in inverno | `winter_max_temp` | Temperatura sopra la quale si spegne il riscaldamento in inverno |
| Soglia minima interna in estate | `summer_min_temp` | Temperatura sotto la quale si accende il riscaldamento in estate |
| Soglia massima interna in estate | `summer_max_temp` | Temperatura sopra la quale si spegne il riscaldamento in estate |
| Soglia temperatura esterna per distinguere estate/inverno | `seasonal_threshold` | Temperatura esterna che separa estate da inverno |
| Temperatura target interna | `target_temp` | Temperatura da impostare quando si accende il riscaldamento |
| Modalità Netatmo da usare | `preset_mode` | Modalità da applicare al termostato (`manual`, `away`, `frost guard`) |
| Sensore di presenza (opzionale) | `presence_entity` | Sensore che rileva se qualcuno è presente |
| Sensore finestra aperta (opzionale) | `window_entity` | Sensore che rileva se la finestra è aperta |

---

## 🔁 Logica di funzionamento

- Ogni 5 minuti, il sistema valuta:
  - Temperatura interna
  - Temperatura esterna
  - Presenza in casa
  - Stato della finestra

### 🔥 Inverno
- Se **temperatura esterna < soglia stagionale**
- Usa soglie **invernali** per accendere/spegnere

### ☀️ Estate
- Se **temperatura esterna > soglia stagionale**
- Usa soglie **estive** per accendere/spegnere

### 🧠 Condizioni ambientali
- Se **temperatura interna < soglia minima** → accende
- Se **temperatura interna > soglia massima** → spegne
- Se **assenza o finestra aperta** → imposta `away`

---

## 🧠 Suggerimenti

- Imposta la programmazione Netatmo su **modalità Notte 24h** (es. 14°C) per evitare conflitti
- Usa Home Assistant come gestore attivo del comfort
- Puoi duplicare l’automazione per gestire più zone o stanze

---

## 🔗 Importazione in Home Assistant

Puoi importare questo blueprint direttamente da Home Assistant usando questo link:


