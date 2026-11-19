# DIODE — Diode circuit solver for TI-84 Plus CE

A menu-driven TI-BASIC program that solves common diode circuit problems: the Shockley equation, a source–resistor–diode circuit (with load-line graph), Zener shunt regulators, rectifiers, and the small-signal resistance.

一个 TI-84 Plus CE 上的 TI-BASIC 二极管电路求解程序：肖克利方程、电源–电阻–二极管串联电路（带负载线图）、稳压管稳压电路、整流电路和小信号电阻。

---

## Features

1. **SHOCKLEY I-V** — `ID = IS(e^(VD/nVT) − 1)`: VD → ID, ID → VD, ΔV for a current ratio (plus mV/decade), and IS from one (VD, ID) point
2. **SERIES R+DIODE** — `VS – R – diode` with four models: ideal, constant VON, VON + rd, exponential (bisection solve). Shows ID, VD, VR, PD; the exponential model can plot the diode curve and the load line with the Q point labelled
3. **ZENER REGULATOR** — VOUT, IS, IL, IZ, regulation check against IZmin, Zener power, minimum RL, maximum RS, minimum VS
4. **RECTIFIER** — opens [RECT](https://github.com/INLEI12138/ti84-rect) (half-wave ±, center-tapped, bridge, optional filter capacitor, with waveform plot). RECT must be installed on the calculator; when it finishes you return to the DIODE menu
5. **SMALL-SIGNAL RD** — `rd = nVT/ID`, `gd`

## 功能

1. **SHOCKLEY I-V（肖克利方程）**：已知 VD 求 ID、已知 ID 求 VD、已知电流比求电压差（含每十倍频 mV 数）、由一组 (VD, ID) 反求 IS
2. **SERIES R+DIODE（电阻二极管串联）**：理想、恒压降、恒压降 + rd、指数模型（二分法求解）四种模型，输出 ID、VD、VR、PD；指数模型可画二极管曲线和负载线并标出 Q 点
3. **ZENER REGULATOR（稳压管稳压）**：VOUT、IS、IL、IZ，判断是否稳压，稳压管功耗、RL 最小值、RS 最大值、VS 最小值
4. **RECTIFIER（整流）**：调用 [RECT](https://github.com/INLEI12138/ti84-rect)（正/反半波、中心抽头全波、桥式，可选滤波电容，带波形图）。计算器上需要同时装有 RECT；算完会回到 DIODE 菜单
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

## Rectifiers / 整流电路

Since this version the rectifier code lives only in RECT, so both programs give the same results. RECT computes the average output by exact integration over the conduction interval; the old DIODE menu used the estimate `(VP − n·VD)·J/π`, which is about 7% high for a 12 V bridge (6.7482 V vs. the exact 6.2915 V).

整流部分现在只保留在 RECT 里，两个程序结果一致。RECT 的平均输出电压是对导通区间精确积分得到的；旧版 DIODE 用的是近似式 `(VP − n·VD)·J/π`，对 12 V 桥式整流大约偏高 7%（6.7482 V，精确值为 6.2915 V）。

---

## Notes

- Results are shown in Normal mode with units in each label; currents in mA, power in mW.
- The load-line graph overwrites `Y₁`, `Y₂` and the window settings.
- Variables A–Z, θ, `Str1`, `Str9` are used.

## 注意事项

- 结果以普通模式显示，单位写在名称里；电流单位为 mA，功率为 mW。
- 画负载线会覆盖 `Y₁`、`Y₂` 和窗口设置。
- 程序会用到变量 A–Z、θ、`Str1`、`Str9`。

---

## Files / 文件说明

- `DIODE.8xp` — program for the calculator / 可直接发送到计算器的程序
- `DIODE.txt` — readable source / 可读的源码


## Related programs / 相关程序

Other TI-84 Plus CE programs by INLEI / INLEI 的其他 TI-84 Plus CE 程序：

| Program / 程序 | Purpose | 用途 |
|---|---|---|
| [AMPCALC](https://github.com/INLEI12138/ti84-ampcalc) | Op-amp (inverting / non-inverting) gain, phase and Bode plot | 运放（反相/同相）增益、相位与 Bode 图 |
| [FILTER](https://github.com/INLEI12138/ti84-filter) | Passive RLC voltage-divider filter response and Bode plot | 无源 RLC 分压滤波器频率响应与 Bode 图 |
| [ITER](https://github.com/INLEI12138/ti84-iteration) | Diode bias point by iteration, two-source mode, rd | 二极管工作点迭代求解（含双电源模式）与 rd |
| [ZFORMULA](https://github.com/INLEI12138/ti84-zformula) | Series / parallel RLC impedance formula reference | 串联/并联 RLC 阻抗公式速查 |
| [RECT](https://github.com/INLEI12138/ti84-rect) | Rectifier solver (half-wave, center-tapped, bridge) with waveform plot | 整流电路求解（半波、中心抽头、桥式）与波形图 |

## License / 许可证

MIT
