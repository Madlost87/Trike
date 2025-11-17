# Trike
VESC MKSESC 75200 V2 – Canvas Pronto da Incollare

✔ Panorama ingressi disponibili

ADC1 (analogico): throttle fisso (acceleratore). Sempre usato come input principale.

ADC2 (analogico): freno rigenerativo proporzionale oppure kill software (ADC2 Low/High). Non può essere pulsante reverse.

DC/A15 (digitale/hardware): kill hardware vero (ON/OFF della centralina se impostata in Control).

PPM/SERVO (digitale): unico ingresso per pulsante reverse.

UART RX (digitale): alternativa a PPM per pulsante reverse.



---

✔ Tabella dei “Control Type” reali del tuo firmware

Modalità	Reverse	Brake	Note

Current No Reverse Brake Center	No	Sì (manopola sotto il centro)	Modalità accel+freno integrata
Current Reverse Center	Sì (da manopola)	Sì	Reverse senza pulsanti
Current Reverse Button	Sì (pulsante PPM/ UART RX)	No	ADC2 non usato
Current Reverse ADC2 Brake Button	Sì (pulsante PPM)	Sì (ADC2 analogico)	ADC2 = freno, NON pulsante
Current No Reverse Brake Button	No	Sì (pulsante digitale)	Nessun reverse
Current No Reverse Brake ADC2	No	Sì (ADC2 analogico)	Nessun pulsante



---

✔ Kill Switch: software vs hardware

Kill software (ADC2 Low/High)

App Settings → General → Kill Switch Mode

Se ADC2 scende o sale oltre il limite → il VESC taglia la coppia (non spegne l’elettronica).


Kill hardware (DC/A15)

Richiede DC-DC Switch → modalità "Control" sulla scheda Makerbase.

DC/A15 basso = spegne la centralina


