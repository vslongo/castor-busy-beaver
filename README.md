# O Jogo do Castor Ocupado (Busy Beaver Explorer)

Simulador de Máquinas de Turing com 2 e 3 estados. Procura a **MT campeã**: a máquina que escreve mais 1s na fita e depois para.

## Como rodar

Não precisa instalar nada. Basta abrir o arquivo `index.html` em qualquer navegador moderno (Chrome, Edge, Firefox).

Se preferir pelo terminal:

```bash
git clone https://github.com/vslongo/castor-busy-beaver.git
cd castor-busy-beaver
```

Depois dê dois cliques em `index.html`.

## O que tem na tela

- **Explorar todas as máquinas**: testa todas as máquinas do número de estados escolhido.
- **Limite de passos**: controle de parada. Uma máquina que passa desse limite é tratada como divergente.
- **MT campeã**: a melhor máquina encontrada, com a tabela de regras.
- **Dois gráficos**: quantas máquinas que param escrevem cada número de 1s, e quantas param em cada número de passos.
- **Simulação passo a passo**: Play, Pausar, Anterior, Próximo e Reiniciar.

## Resultados esperados

| Estados | Máquinas testadas | Campeã | Passos |
|---|---|---|---|
| 2 | 20.736 | 4 uns | 6 |
| 3 | 16.777.216 | 6 uns | 14 |

A busca de 3 estados leva alguns segundos.

## Roteiro da apresentação

Veja [roteiro-apresentacao.md](roteiro-apresentacao.md).
