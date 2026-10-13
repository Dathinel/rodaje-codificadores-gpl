# Licencias de rodaje-codificadores-gpl

El `ffmpeg.exe` del paquete es **GPL-3.0-or-later**: FFmpeg (commit `2a571b6`) se configuró con `--enable-gpl --enable-version3` y se compiló con `build\compilar-ffmpeg-gpl.ps1` de Rodaje (scripts de BtbN/FFmpeg-Builds en el commit `6c9aec5`, imagen `base-win64` fijada por huella, GCC 16.2.0). Todo lo de la tabla va enlazado de forma estática dentro del exe; cada aviso viaja en el paquete, en `licencias/`, sacado de la fuente que se compiló.

| Pieza | Licencia | Aviso en `licencias/` |
|---|---|---|
| FFmpeg | GPL-3.0-or-later por la configuración | `FFmpeg-LICENSE.md`, `FFmpeg-CREDITS.txt` y `COPYING.GPLv3.txt` en la raíz |
| x264 | GPL-2.0-or-later | `x264-COPYING.txt`, `x264-AUTHORS.txt` |
| x265 (8, 10 y 12 bits, HDR10+) | GPL-2.0-or-later; json11, MIT | `x265-COPYING.txt`, `x265-dynamicHDR10-LICENSE.txt`, `x265-json11-LICENSE.txt` |
| libopus | BSD-3-Clause | `libopus-COPYING.txt`, `libopus-LICENSE_PLEASE_READ.txt`, `libopus-AUTHORS.txt` |
| LAME (libmp3lame), sin modificar | LGPL-2.0-or-later | `lame-COPYING.txt`, `lame-LICENSE.txt` |
| libiconv (con gnulib) | LGPL-2.1-or-later | `libiconv-COPYING.LIB.txt`, `libiconv-AUTHORS.txt` |
| CRT de mingw-w64 y winpthreads | Aviso de tipo BSD del runtime, con las piezas que lista; winpthreads, MIT; el proyecto, ZPL-2.1 | `mingw-w64-COPYING.txt`, `mingw-w64-runtime-COPYING.txt`, `mingw-w64-DISCLAIMER*.txt`, `winpthreads-COPYING.txt` |
| mingw-std-threads | BSD-2-Clause | `mingw-std-threads-LICENSE.txt` |
| libgcc y libstdc++ (GCC 16.2.0) | GPL-3.0 con la GCC Runtime Library Exception 3.1 | `gcc-COPYING.RUNTIME.txt` |

Todas son compatibles con la GPLv3 (las GPL-2.0 y LGPL «o posterior» por su cláusula de versiones posteriores; las permisivas, según la lista de la FSF). Este paquete usa LAME: https://lame.sourceforge.io/.

**Fuente correspondiente** (GPLv3, sección 6): `rodaje-codificadores-gpl-<versión>-fuente.tar`, en la misma release que cada `.paquete`, con su `.sha256`. El `LEEME.md` del paquete da su URL y su huella.

## Patentes (nota informativa, no es consejo legal)

H.264/AVC y H.265/HEVC son formatos con patentes que se licencian en pools (Via LA para AVC; Access Advance y Via LA para HEVC). Las licencias de copyright de arriba no conceden licencias de patentes, y codificar con x264 o x265 puede requerir una según el país y el uso, en especial si es comercial. Por eso Rodaje no trae este complemento por defecto y nunca lo elige solo: cada quien decide si lo instala y responde por su uso. Opus tiene licencias de patentes sin regalías declaradas ante la IETF, y el programa de licencias de MP3 terminó en 2017; tampoco esto es una garantía.
