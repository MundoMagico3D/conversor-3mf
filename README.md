# Conversor 3MF

Converte projetos `.3mf` do **MakerWorld / BambuStudio** para abrir e fatiar sem
erro no **Anycubic Slicer Next**.

Feito pela [Mundo Mágico 3D](https://www.mundomagico3d.com.br).

### ⬇️ [Baixar a última versão](../../releases/latest)

---

## O problema

Você baixa um projeto do MakerWorld, abre no Anycubic Slicer Next e toma um erro.
Dependendo da versão do fatiador:

- uma lista de *"valor inválido"* logo ao abrir — `wall_filament`,
  `tree_support_wall_count`, `raft_first_layer_expansion`…
- `process not compatible with printer`
- ou o pior: o arquivo abre normalmente e **só quebra na hora de fatiar**, com
  `Parsing error` e `Please check the custom G-code`

Não é problema do seu arquivo nem da sua impressora. O projeto foi salvo pelo
BambuStudio, que grava vários ajustes num formato que o Anycubic Slicer Next não
entende — e traz junto o G-code de partida da outra impressora.

## O que o programa faz

Corrige o projeto e devolve um arquivo pronto, em seis etapas:

1. **Tipo** — velocidade e aceleração vêm como lista e viram valor único
2. **Faixa** — corrige os valores fora do intervalo aceito
3. **Máquina** — troca o bloco da impressora pelo perfil real da sua
4. **Limite** — corta velocidade, aceleração e altura de camada no teto da máquina
5. **Extra** — remove os ajustes que só existem no outro fatiador
6. **Objeto** — aplica as mesmas correções peça a peça

**Não toca** na geometria, na posição das peças, nos modificadores nem na pintura
de cor e de suporte. O arquivo original não é alterado: sai um arquivo novo ao
lado, com `(Anycubic)` no nome.

## Funciona com qual impressora?

Com todas. Ele lê os perfis do Anycubic Slicer Next **instalado no seu
computador** — Kobra 1, 2, 3, 4, S1, Max, V2, X, em qualquer bico.

Como lê do seu fatiador, continua correto depois que ele for atualizado.

## Instalação

Baixe o **instalador** e execute. Ele não pede administrador.

Prefere não instalar? Baixe a **versão portátil**, extraia a pasta inteira e rode
o `Conversor3MF.exe`.

> Na primeira execução o Windows pode mostrar *"O Windows protegeu o computador"*.
> Isso acontece com programas de desenvolvedor pequeno, sem certificado digital.
> Clique em **Mais informações → Executar assim mesmo**.

### Precisa ter instalado

O **Anycubic Slicer Next**, que é gratuito:
[anycubic.com/slicerNextDownload](https://www.anycubic.com/slicerNextDownload)

O programa não funciona sem ele, porque é dele que vêm os perfis da sua impressora.

Windows 10 ou 11. Não precisa de Python nem de mais nada.

## Como usar

1. Abra o programa
2. Escolha o arquivo `.3mf`
3. Confira a impressora
4. Clique em **CONVERTER**

Também funciona arrastar o `.3mf` para cima do ícone, ou clicar com o botão
direito no arquivo e escolher **Converter para Anycubic**.

## Uso gratuito e licença

O programa é gratuito para baixar e usar, com **3 conversões por dia durante 5
dias**. O prazo só começa na primeira conversão.

A licença definitiva tira o limite diário e libera o relatório detalhado das
correções. Ela é vendida pela [Mundo Mágico 3D](https://www.mundomagico3d.com.br).

## Perguntas frequentes

**As peças ficaram fora do centro da mesa.**
Normal — as posições vieram da mesa da outra impressora. Aperte `A` no Anycubic
Slicer Next para reorganizar.

**Apareceu "não há nada para converter".**
O arquivo tem só o modelo 3D, sem configuração de fatiamento. Pode abrir direto no
fatiador.

**O arquivo foi fatiado para outro bico.**
O programa avisa no relatório. As larguras de extrusão continuam as do arquivo
original — troque o perfil de processo no fatiador depois de abrir.

---

Este projeto não tem vínculo com a Anycubic nem com a Bambu Lab. Os nomes citados
pertencem aos seus respectivos donos e aparecem apenas para descrever
compatibilidade.
