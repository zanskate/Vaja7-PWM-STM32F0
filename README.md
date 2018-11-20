# Vaja7-PWM-STM32F0
Generiranje PWM signala z STM32F0. Za preizkus rabimo osciloskop.
------------------------------------------------------------------------------------------------------------------------------------------
ODGOVORI

a) V levem Pinout oknu razširite nabor možnosti za časovnik TIM1. Clock Source nastavite kot Internal
Clock. Prvi kanal aktivirajte kot PWM Generation CH1. Kateri pin ste omogočili? PA8.
 Kaj se izpiše poleg pina? TIM1_CH1.
b) V Configuration kliknemo TIM1 gumb. Vrednost Prescaler v zavihku Parameter Settinngs določite tako, da bo časovnik delal s frekvenco 1 MHz. Koliko je vrednost Perscaler? 16.
c) Parameter Counter Period nastavimo na 100 in s tem še dodatno znižamo takt časovnika. Koliko znaša sedaj? 10kHz.
č) Pulse (16 bits value) nastavite na 50. Kaj pomeni ta parameter? Izpiše 50% vrednost.
d) Poiščite prenastavljeni parameter Pulse (ki je 50) v vaši kodi in prepišite ukaz, ki ga je generiral CubeMX: sConfigOC.Pulse = 50;
e) V kodi spremenite vrednost širine pulza na 25 %. Zapišite popravljeni ukaz v kodi: sConfigOC.Pulse = 25;
f) Zapišite kaj počnejo ukazi v 1.,2. in 3. vrstici (v user code begin 3):
1.ukaz) htim1.Instance-->CCR1 = dutyCycle;
2.ukaz) dutyCycle+=10;
3.ukaz) if(dutyCycle>90) dutyCycle=10;
1. ukaz: Prisiljena sprememba dutycyclea preko registra
2. ukaz: Dodaja 10% razmerju širine impulza.
3. ukaz: Ko dosežemo več kot 90% se vrne nazaj na 10%.
------------------------------------------------------------------------------------------------------------------------------------------
KOMENTAR NA DELOVANJE:
S pomočjo CUBE MX in HAL knjižnicami v µVision 5 sprogramiramo mikroprocesor tako, da boste
generirali PWM signal in ga tudi krmilili na izbranem izhodu STM32F0. Za preizkus potrebujemo osciloskop. Delovanje je potekalo brez večjih težav, le na osciloskopu je prišlo do manjšega popačenja signala.
