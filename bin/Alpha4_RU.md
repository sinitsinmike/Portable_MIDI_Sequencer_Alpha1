# Alpha4 – Реализация MIDI Clock и Transport

## Обзор

В версии Alpha4 реализован стабильный и соответствующий спецификации MIDI Clock OUT и Transport OUT.

Поддерживаются сообщения:
- MIDI Clock (0xF8)
- Start (0xFA)
- Stop (0xFC)
- Continue (0xFB)

Логика транспорта основана на переходах состояний и исключает повторную отправку сообщений.

---

## MIDI Clock Output

Внутреннее разрешение: 96 PPQN  
MIDI Clock: 24 PPQN  
Делитель: 96 / 24 = 4

Реализация:

midiClockDivider++;

if (midiClockDivider >= 4) {
    Serial1.write(0xF8);
    midiClockDivider = 0;
}

Clock отправляется только если isPlaying == true.

---

## Transport Output

Отслеживание состояния в Core1:

static bool lastIsPlaying = false;
static bool lastIsPaused  = false;

bool playing = midiEngine.isPlaying;
bool paused  = midiEngine.isPaused;

---

### START (0xFA)

Отправляется только если:
playing == true
lastIsPlaying == false
lastIsPaused == false

---

### CONTINUE (0xFB)

Отправляется при возобновлении после паузы:

else if (playing && lastIsPaused) {
    Serial1.write(0xFB);
}

---

### STOP (0xFC)

Отправляется при переходе playing → stopped:

if (!playing && lastIsPlaying) {
    Serial1.write(0xFC);
}

---

## Поведение

Play после Stop → Start (0xFA)  
Pause → Stop (0xFC)  
Resume → Continue (0xFB)  
Stop → Stop (0xFC)

---

## Архитектура

Clock и Transport работают на Core1  
UI работает на Core0  
Transport не зависит от UI  
Flash не выполняется на Core1  
MIDI Clock отделён от UI

---

Alpha4 Code Freeze
