<p align="center">
  <a href="https://github.com/Dathinel/rodaje"><img src="https://raw.githubusercontent.com/Dathinel/rodaje/main/assets/marca/rodaje.svg" alt="Logotipo de Rodaje" width="104"></a>
</p>

<h1 align="center">rodaje-codificadores-gpl</h1>

<p align="center">
  Complemento opcional para <a href="https://github.com/Dathinel/rodaje">Rodaje</a>: añade x264 y x265 (H.264 y HEVC por CPU, 8 y 10 bits) en Exportar → Avanzado, con un <code>ffmpeg.exe</code> GPL propio que corre aparte.
</p>

<p align="center">
  <a href="#licencia"><img src="https://img.shields.io/badge/licencia-GPLv3-E8833A?style=flat-square&labelColor=1D1D1D" alt="Licencia GPLv3"></a>
  <a href="https://github.com/Dathinel/rodaje-codificadores-gpl/releases/latest"><img src="https://img.shields.io/github/v/release/Dathinel/rodaje-codificadores-gpl?style=flat-square&labelColor=1D1D1D&color=E8833A&label=versi%C3%B3n" alt="Última versión"></a>
  <img src="https://img.shields.io/badge/formato-.paquete-E8833A?style=flat-square&labelColor=1D1D1D" alt="Formato .paquete">
  <a href="https://github.com/Dathinel/rodaje"><img src="https://img.shields.io/badge/para-Rodaje-E8833A?style=flat-square&labelColor=1D1D1D" alt="Para Rodaje"></a>
</p>

Rodaje trae su propio FFmpeg LGPL y codifica H.264 y HEVC por la GPU o con Windows. Este complemento suma los codificadores de software x264 y x265 para quien los prefiera: un `ffmpeg.exe` estático (FFmpeg 9.0.2 con `--enable-gpl --enable-version3`, x264, x265, libopus, LAME y libiconv, nada más) que Rodaje ejecuta como un proceso aparte por una tubería. Nunca entran en una elección automática ni en un preajuste: aparecen en «Avanzado» como «Complemento GPL».

| Codificador | Formatos |
|---|---|
| `libx264` | H.264, 8 y 10 bits |
| `libx265` | HEVC, 8, 10 y 12 bits (HDR10+) |
| `libopus`, `libmp3lame`, `aac` | El audio de la misma exportación |

## Instalar en Rodaje

En Rodaje, Complementos → Codificadores GPL → Instalar lo baja, comprueba la firma del catálogo y el hash y lo instala. A mano: descarga `rodaje-codificadores-gpl-<versión>.paquete` de las [releases](https://github.com/Dathinel/rodaje-codificadores-gpl/releases) y usa «Instalar desde archivo…» en Complementos.

## Código fuente y compilación

Cada release adjunta, junto al `.paquete`, la **fuente correspondiente** (`rodaje-codificadores-gpl-<versión>-fuente.tar`, con su `.sha256`): FFmpeg, los scripts de BtbN/FFmpeg-Builds y cada biblioteca en el árbol exacto que se compiló, con los scripts y las instrucciones para repetir la compilación. Los scripts viven en el repositorio de Rodaje:

```
powershell -NoProfile -ExecutionPolicy Bypass -File build\compilar-ffmpeg-gpl.ps1    # Docker, unos 25 min
powershell -NoProfile -ExecutionPolicy Bypass -File build\armar-codificadores-gpl.ps1
```

El armado comprueba la huella del exe, que `-buildconf` solo active lo previsto y que x264 y x265 codifiquen en 8 y 10 bits; las mismas entradas dan el mismo `.paquete` byte a byte.

| Archivo | Qué es |
|---|---|
| `paquete.json` | El manifiesto: módulo con `protocol: 0` (una herramienta, no un módulo del protocolo) |
| `LICENCIAS.md` | Licencia de cada pieza y nota sobre patentes |
| `LICENSE` | GNU GPL versión 3 |

## Licencia

GNU GPL versión 3 o posterior (`LICENSE`). Cada biblioteca conserva la suya y sus avisos van dentro del paquete, en `licencias/`: ver [LICENCIAS.md](LICENCIAS.md), que incluye una nota sobre las patentes de H.264 y HEVC. El logotipo de Rodaje es marca de su autor ([TRADEMARK.md](https://github.com/Dathinel/rodaje/blob/main/TRADEMARK.md)).
