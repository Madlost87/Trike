VESC MKSESC 75200 V2 – README per GitHub

Questo README è formattato per essere inserito direttamente in un repository GitHub. Include:

panoramica ingressi

spiegazione dei Control Type del firmware Makerbase

setup pulsanti reverse / brake / kill

limitazioni reali del firmware

configurazioni consigliate



---

🚀 Panoramica

Centralina: Makerbase MKSESC 75200 V2
Firmware: compatibile VESC 6.x (modificato Makerbase)
App attiva negli screenshot: ADC and UART

Questa documentazione riassume come funzionano ADC1, ADC2, PPM, DC/A15, e come configurare pulsante reverse, freno rigenerativo e kill switch.


---

🔌 Ingressi disponibili

Ingresso	Tipo	Uso Primario	Limiti

ADC1	Analogico	Throttle	Non rimappabile
ADC2	Analogico	Brake analogico oppure Kill software	Non usabile come pulsante reverse
PPM/SERVO	Digitale	Pulsante Reverse	Supporta 1 solo pulsante
UART RX	Digitale	Alternativa a PPM per Reverse	Solo pulsante reverse
DC/A15	Digitale/Hardware	Kill hardware (ON/OFF reale)	Non gestito dall’App ADC



---

⚙️ Control Type disponibili

Modalità	Reverse	Brake	Note

Current No Reverse Brake Center	❌	✔ Integrato	Brake quando l’ADC1 va sotto il centro
Current Reverse Center	✔ (via manopola)	✔	Reverse senza pulsante
Current Reverse Button	✔ (PPM/UART)	❌	La modalità più semplice per pulsante reverse
Current Reverse ADC2 Brake Button	✔ (PPM)	✔ (ADC2)	ADC2 = freno analogico
Current No Reverse Brake Button	❌	✔ Pulsante	Nessun reverse
Current No Reverse Brake ADC2	❌	✔ ADC2	Brake proporzionale su ADC2



---

🛑 Kill Switch: software vs hardware

Kill software (ADC2)

Si configura in App Settings → General → Kill Switch Mode

Triggerato quando ADC2 va Low o High

Effetto: taglio coppia, non spegne la scheda


Kill hardware (DC/A15)

Richiede DC-DC switch su scheda in modalità Control

Abbassa DC/A15 → spegne fisicamente la centralina



---

🔄 Pulsante Reverse su PPM – configurazione ufficialmente supportata

Collegamento

Pulsante → PPM Signal
Pulsante → GND

NON collegare i 5V.

VESC Tool

App to use: ADC and UART
Control Type: Current Reverse Button

Funzionamento

Pulsante rilasciato → marcia avanti

Pulsante premuto → reverse


ADC2 rimane disponibile come:

Brake analogico, oppure

Kill software



---

🧩 Configurazioni realistiche

A) Reverse + Kill software su ADC2 + Brake Center

Reverse → pulsante PPM

Brake → integrato su ADC1

Kill → ADC2 Low/High

Semplice da cablare


B) Reverse + Brake su ADC2 + Kill hardware (DC/A15)

Reverse → PPM

Brake → ADC2 analogico

Kill → DC/A15 (hardware reale)

La più completa


C) Solo Kill hardware + Brake Center

Kill → DC/A15

Brake → da manopola

Nessun reverse



---

❗ Limiti del firmware

ADC1 è sempre throttle.

ADC2 non può essere usato come pulsante reverse.

È possibile gestire un solo pulsante digitale tramite PPM o UART.

Non è possibile avere 3 pulsanti indipendenti (reverse + brake on/off + kill) solo tramite App ADC.



---

📁 Struttura consigliata repo GitHub

/README.md
/docs/
   wiring.svg
   logic_diagram.png
   vesc_settings_screenshots/
/config/
   recommended_modes.md

