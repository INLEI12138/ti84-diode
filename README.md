# DIODE — Diode circuit solver for TI-84 Plus CE

A menu-driven TI-BASIC program that solves common diode circuit problems: the Shockley equation, a source–resistor–diode circuit (with load-line graph), Zener shunt regulators, rectifiers, and the small-signal resistance.

一个 TI-84 Plus CE 上的 TI-BASIC 二极管电路求解程序：肖克利方程、电源–电阻–二极管串联电路（带负载线图）、稳压管稳压电路、整流电路和小信号电阻。

---

## Features

1. **SHOCKLEY I-V** — `ID = IS(e^(VD/nVT) − 1)`: VD → ID, ID → VD, ΔV for a current ratio (plus mV/decade), and IS from one (VD, ID) point
2. **SERIES R+DIODE** — `VS – R – diode` with four models: ideal, constant VON, VON + rd, exponential (bisection solve). Shows ID, VD, VR, PD; the exponential model can plot the diode curve and the load line with the Q point labelled
3. **ZENER REGULATOR** — VOUT, IS, IL, IZ, regulation check against IZmin, Zener power, minimum RL, maximum RS, minimum VS
4. **RECTIFIER** — half-wave, center-tapped full-wave, bridge; with or without a filter capacitor: peak output, VDC, VRMS, ripple Vpp and frequency, PIV, conduction angle, average and peak diode current
5. **SMALL-SIGNAL RD** — `rd = nVT/ID`, `gd`

## 功能

1. **SHOCKLEY I-V（肖克利方程）**：已知 VD 求 ID、已知 ID 求 VD、已知电流比求电压差（含每十倍频 mV 数）、由一组 (VD, ID) 反求 IS
2. **SERIES R+DIODE（电阻二极管串联）**：理想、恒压降、恒压降 + rd、指数模型（二分法求解）四种模型，输出 ID、VD、VR、PD；指数模型可画二极管曲线和负载线并标出 Q 点
3. **ZENER REGULATOR（稳压管稳压）**：VOUT、IS、IL、IZ，判断是否稳压，稳压管功耗、RL 最小值、RS 最大值、VS 最小值
4. **RECTIFIER（整流）**：半波、中心抽头全波、桥式，带或不带滤波电容：输出峰值、VDC、VRMS、纹波峰峰值和频率、PIV、导通角、二极管平均和峰值电流
5. **SMALL-SIGNAL RD（小信号电阻）**：`rd = nVT/ID`、`gd`

---

## Install

1. Send `DIODE.8xp` to the calculator with TI Connect CE (or paste `DIODE.txt` into a new program named `DIODE` in the TI Connect CE editor and send that).
2. `PRGM` → `DIODE` → `ENTER`.

Do not rename the program: the unit parser works by the program calling itself as `prgmDIODE`.

## 安装

1. 用 TI Connect CE 把 `DIODE.8xp` 发送到计算器（或者把 `DIODE.txt` 的内容粘贴到 TI Connect CE 编辑器里新建的名为 `DIODE` 的程序中，再发送）。
2. 按 `PRGM` → 选 `DIODE` → `ENTER`。

不要给程序改名：单位识别功能是靠程序以 `prgmDIODE` 调用自己实现的。

---

## Entering values with units

Every numeric prompt accepts SI prefixes and an optional unit (type letters with `ALPHA`):

| Input | Value |
|---|---|
| `1K`, `1KOHM` | 1000 |
| `4.7MEG` | 4.7×10⁶ |
| `1000UF` | 0.001 |
| `100NF`, `10P` | 1×10⁻⁷, 1×10⁻¹¹ |
| `5MA`, `10M` | 0.005, 0.01 |
| `60HZ`, `1KHZ` | 60, 1000 |
| `0.7V`, `12`, `1E3`, `12/√(2)` | as written |

- `M` is **milli**, `MEG` is mega (SPICE convention).
- For scientific notation use `2ND` `,` (EE), not the letter E.

## 带单位输入

每个数值输入都可以带单位前缀和单位（字母用 `ALPHA` 输入），对照见上表。

- `M` 是**毫**，`MEG` 才是兆（与 SPICE 相同）。
- 科学计数法用 `2ND` `,`（EE），不要用字母 E。

---

## Example: bridge rectifier

`vs(t) = 12 sin(2π·60t) V`, `VD = 0.7 V`, `RL = 1 kΩ`, no capacitor.

`RECTIFIER` → `BRIDGE`, then enter `0` (value given as peak), `12`, `0.7`, `1K`, `0`:

```
VO PK (V)  10.6
VDC (V)    6.7482
VRMS (V)   7.4953
IDC (MA)   6.7482
PIV (V)    11.3
F RIPPLE = 2 X F LINE
```

## 示例：桥式整流

条件如上。依次选 `RECTIFIER` → `BRIDGE`，输入 `0`（题目给的是峰值）、`12`、`0.7`、`1K`、`0`，屏幕显示如上。

---

## Notes

- Results are shown in Normal mode with units in each label; currents in mA, power in mW.
- Rectifier-with-capacitor results use the standard small-ripple approximations.
- The load-line graph overwrites `Y₁`, `Y₂` and the window settings.
- Variables A–Z, θ, `Str1`, `Str9` are used.

## 注意事项

- 结果以普通模式显示，单位写在名称里；电流单位为 mA，功率为 mW。
- 带滤波电容的整流结果采用常用的小纹波近似公式。
- 画负载线会覆盖 `Y₁`、`Y₂` 和窗口设置。
- 程序会用到变量 A–Z、θ、`Str1`、`Str9`。

---

## Files / 文件说明

- `DIODE.8xp` — program for the calculator / 可直接发送到计算器的程序
- `DIODE.txt` — readable source / 可读的源码

## License / 许可证

MIT
