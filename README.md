# AnyBox

Abre um AnyDesk novo e isolado numa caixa do Sandboxie a cada execução, cada um com ID próprio.
É portátil: nada é instalado na máquina.

## Download

**[Baixar a última versão do AnyBox.exe](https://github.com/kleitofi/anybox-releases/releases/latest/download/AnyBox.exe)**

Todas as versões: <https://github.com/kleitofi/anybox-releases/releases>

## Controle de versões

Cada compilação do `AnyBox.exe` tem um ID formado pela versão e pela data de compilação,
por exemplo `1.6.0-20261109-1430`. O ID aparece em Propriedades > Detalhes do exe e nas notas
de cada release.

Ao abrir, o exe consulta o [`versoes.json`](versoes.json) deste repositório:

| Status | O que acontece |
|---|---|
| `ativa` | Abre normalmente. |
| `aviso` | Abre, e mostra a mensagem com o link do motivo. |
| `desativada` | **Não abre.** Mostra a mensagem e oferece abrir o motivo com as orientações. |

Se o exe estiver abaixo da `minima.versao`, ele também fica desativado.
Compilações fora da lista seguem a regra `desconhecida`.
Sem internet, o exe abre normalmente, a não ser que já tenha sido visto como desativado naquela máquina.

O motivo de cada desativação fica em [`motivos/`](motivos), com as orientações de como proceder
e o link da versão nova.

### Exemplo de compilação desativada

```json
"1.6.0-20261109-1430": {
  "status": "desativada",
  "mensagem": "Falha ao carregar o driver no Windows 11 24H2. Baixe a versão nova.",
  "motivo": "motivos/2026-11-falha-driver.md",
  "desde": "2026-11-20 09:00"
}
```

Para editar, use o `versoes.py` do repositório do código-fonte (ele cria o `.md` a partir do
[modelo](motivos/_modelo.md)), ou edite os arquivos direto aqui no GitHub.
