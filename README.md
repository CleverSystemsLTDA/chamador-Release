# chamador-Release

Firmware publicado da placa **chamador** (controle de botões, ESP8266) da Clever Systems.

Os arquivos ficam nas [Releases](../../releases). O **Gravador de placas Clever** (`clever-flasher.exe`) busca a release mais recente daqui e baixa o firmware sozinho.

## Formato de cada release

O gravador depende deste formato. A Action que publica as releases precisa seguir:

| Item | Formato | Exemplo |
|---|---|---|
| Tag | `codigo-placas-<N>` (mesmo valor do `#define VERSION` do `chamador.ino`) | `codigo-placas-7` |
| Firmware | `chamador-<tag>.bin`: imagem a partir de `0x0` (programa, sem a área de configuração) | `chamador-codigo-placas-7.bin` |
| Checksum | `<firmware>.sha256`: SHA-256 em hex, sozinho na linha | `chamador-codigo-placas-7.bin.sha256` |

- O gravador usa só `releases/latest`. Rascunhos e pré-releases são ignorados.
- O gravador confere o SHA-256 antes de usar o arquivo e recusa se não bater.
- O firmware nunca contém a configuração da placa (Wi-Fi, senha, servidor). Ela fica na EEPROM (`0x3FB000`) e é gravada pelo gravador.
