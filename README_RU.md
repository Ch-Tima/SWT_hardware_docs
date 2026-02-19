# SWT – Smart Watch Table (Smart Desk Clock on STM32F103)

### SWT — настольные умные часы на базе микроконтроллера STM32F103, с графическим ЖК-дисплеем LX-12864-B5.

**Дата: 19.02.2026**

Актуальная версия схемы — **[sh_v4b2](/sh/sh_v4b2/sh_v4b2.pdf)**.

`sh_v4b2` - полностью "_**рабочая**_" схема настольных часов, хотя в ней всё ещё есть некоторые проблемы.

| Компоненты | Информация    |  Количество
|------------|---------------|----------------------|
| **MCU**    | [STM32F103C8T6](mc/STM32F103X4.PDF)  | x1
| **CHRG**   | [LTH7R](pw/LTH7R-1.PDF)              | x1
| **LDO**    | [SC662K](pw/_662K.PDF)               | x1
| **Quartz** | [32.768](scomp/XKZEL89CII_32768K.PDF)| x1
| **NTC_T**  | [C394021](scomp/C394021.pdf)         | x1
| **Diodes** | SS14                                 | x2

#### Подробнее о количестве компонентов смотрите [здесь](/sh/sh_v4b2/BOM_SWT_shv4b2.csv)

## Прошивка 
Хотите собрать и протестировать устройство? 
Базовая рабочая прошивка доступна здесь: **[SWT_firmware](https://github.com/Ch-Tima/SWT_firmware)**


## Хочешь помочь?
Если есть идеи, советы или просто желание поучаствовать - буду рад любой помощи!

## Language
 - [English version](README.md)
 - Русская версия (текущая)

## Developer

- **Name**: Tymofii
- **GitHub**: [Ch-Tima](https://github.com/Ch-Tima)
- **Ko-fi**: [Ch-Tima](https://ko-fi.com/chtima)