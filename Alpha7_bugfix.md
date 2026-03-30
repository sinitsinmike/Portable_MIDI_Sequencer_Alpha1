
Encoder instability (major fix)
	•	Fixed inconsistent rotary encoder behavior:
	•	missed steps
	•	random double steps (+2)
	•	jitter and non-linear response
	•	Root cause:
	•	incorrect detent state assumption (00 instead of actual hardware 11)
	•	combined with non-deterministic polling / ISR timing
	•	Solution:
	•	switched to detent-based decoding at correct state (0b11)
	•	stabilized quadrature decoding logic
	•	removed timing-based filtering artifacts
	•	Result:
	•	1 physical click = 1 step (consistent)
	•	no missed steps
	•	no random acceleration or drops
	•	stable behavior across all rotation speeds
	•	Note:
	•	encoder detent is hardware-dependent
	•	current implementation assumes detent = 0b11

⸻

🇷🇺 RU — Release Notes (добавка)

Исправления ошибок

Нестабильная работа энкодера (критический фикс)
	•	Исправлена нестабильная работа энкодера:
	•	пропуски шагов
	•	случайные двойные шаги (+2)
	•	дрожание и нелинейный отклик
	•	Причина:
	•	неверное предположение о detent состоянии (00 вместо реального 11)
	•	в сочетании с нестабильным polling / ISR
	•	Решение:
	•	переход на detent-based обработку с правильным состоянием (0b11)
	•	стабилизация quadrature decoding
	•	удаление временных костылей (millis / delay)
	•	Результат:
	•	1 физический щелчок = 1 шаг (стабильно)
	•	нет пропусков
	•	нет случайных ускорений
	•	стабильная работа на любых скоростях
	•	Примечание:
	•	detent зависит от конкретного энкодера
	•	текущая реализация использует 0b11