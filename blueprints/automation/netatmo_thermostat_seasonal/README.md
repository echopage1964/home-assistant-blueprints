# Netatmo Thermostat Stagionale
Blueprint per Home Assistant che gestisce il termostato Netatmo in modo intelligente, tenendo conto della temperatura interna, esterna, della stagione e di condizioni ambientali come presenza e finestra aperta.

🎯 Funzionalità
Controllo dinamico del riscaldamento basato su soglie configurabili

Logica stagionale: soglie diverse per estate e inverno

Supporto per sensori di presenza e finestra aperta

Modalità Netatmo configurabile (manual, away, frost guard)

Intervallo di controllo ogni 5 minuti

📦 Requisiti
Integrazione Netatmo attiva in Home Assistant

Sensore temperatura interna (es. sensor.netatmo_salon_temperature)

Sensore temperatura esterna (es. sensor.netatmo_giardino_temperature)

(Opzionali) Sensore di presenza e sensore finestra aperta

⚙️ Installazione
Copia il file netatmo_thermostat_seasonal.yaml in:

Codice
config/blueprints/automation/netatmo_thermostat_seasonal/
Riavvia Home Assistant o aggiorna la pagina dei blueprint

Vai su Impostazioni > Automazioni > Progetti (Blueprints)

Clicca su Crea Automazione e configura i parametri

🛠️ Parametri configurabili
Parametro	Descrizione
climate_entity	Entità del termostato Netatmo
internal_temp_sensor	Sensore temperatura interna
external_temp_sensor	Sensore temperatura esterna
winter_min_temp / winter_max_temp	Soglie interne per l'inverno
summer_min_temp / summer_max_temp	Soglie interne per l'estate
seasonal_threshold	Temperatura esterna che distingue estate/inverno
target_temp	Temperatura da impostare quando si accende
preset_mode	Modalità Netatmo da usare (manual, away, ecc.)
presence_entity	Sensore di presenza (opzionale)
window_entity	Sensore finestra aperta (opzionale)
🔁 Logica di funzionamento
Se temperatura esterna < soglia stagionale → inverno

Se temperatura esterna > soglia stagionale → estate

Se temperatura interna < soglia minima → accende

Se temperatura interna > soglia massima → spegne

Se assenza o finestra aperta → imposta away

🧠 Suggerimenti
Imposta la programmazione Netatmo su modalità Notte 24h per evitare conflitti

Usa Home Assistant come gestore attivo del comfort

Puoi duplicare l’automazione per gestire più zone o stanze

📄 Licenza
Questo blueprint è distribuito con licenza MIT. Puoi modificarlo e riutilizzarlo liberamente.
