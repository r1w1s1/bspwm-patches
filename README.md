# bspwm patches

Patches locais relacionados ao [bspwm](https://github.com/baskerville/bspwm).

## `0001-do-not-raise-focused-window.patch`

Este patch reúne a correção proposta no PR [#1541](https://github.com/baskerville/bspwm/pull/1541), relacionada ao issue [#1537](https://github.com/baskerville/bspwm/issues/1537), para o problema descrito também no issue [#1540](https://github.com/baskerville/bspwm/issues/1540).

### Problema

Com `focus_follows_pointer=true` e duas janelas flutuantes sobrepostas, trocar
para outro desktop e voltar podia elevar a janela focada acima da outra como se
ela tivesse recebido um clique, mesmo sem clicar.

O problema foi reproduzido no Slackware Linux com bspwm 0.9.12.

### Conteúdo

O patch inclui:

1. a alteração do PR #1541, que desativa temporariamente `auto_raise` durante
   dois refocos internos;
2. uma pequena melhoria local: o valor anterior de `auto_raise` é salvo e
   restaurado, em vez de sempre ser forçado para `true`.

A segunda parte ainda é uma proposta local e não foi enviada ao upstream.

### Base e origem

- Base: bspwm `0.9.12`, commit `c5cf7d3`.
- Código de origem local: `/home/data/tmp/bspwm/bspwm-1541`.
- Commit do PR presente na origem: `bfa15f6` (`Do not raise focused window for desktop and mouse`).
- Patch gerado em: 16 de novembro de 2026.
- Comentário de reprodução já publicado: [PR #1541, comentário](https://github.com/baskerville/bspwm/pull/1541#issuecomment-6904614552).

### Aplicação

A partir de uma cópia limpa do bspwm 0.9.12:

```sh
git apply 0001-do-not-raise-focused-window.patch
make
```

Para verificar sem aplicar:

```sh
git apply --check 0001-do-not-raise-focused-window.patch
```

### Teste reproduzido

```sh
bspc config focus_follows_pointer true
bspc config click_to_focus button1
```

Com dois `xterm` flutuantes e parcialmente sobrepostos:

1. mover o ponteiro para a parte visível da janela de trás, sem clicar;
2. trocar do desktop IV para I;
3. voltar para o desktop IV.

Com a correção, a janela focada não deve ser elevada indevidamente.
