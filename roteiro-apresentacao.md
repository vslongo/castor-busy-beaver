# Roteiro da apresentação: O Jogo do Castor Ocupado

Tempo sugerido: 10 a 12 minutos + perguntas.
Abra o arquivo `index.html` no navegador antes de começar e deixe a página carregada.

---

## 1. Abertura (1 min)

**Fale:**
> "Hoje vou mostrar um problema famoso da computação chamado *Castor Ocupado*. A pergunta é simples de dizer: dado um número *n* de estados, qual é a máquina que escreve mais 1s na fita e depois para?"

**Mostre:** o título do dashboard.

---

## 2. O que é uma Máquina de Turing (2 min)

Explique com um desenho no quadro ou na tela:

- **Fita:** uma linha infinita de células. Cada célula guarda 0 ou 1 (começa tudo em 0).
- **Cabeça:** lê e escreve uma célula por vez e se move uma casa para a esquerda (E) ou para a direita (D).
- **Estados:** a "memória" da máquina (A, B, C...). Um estado especial, **PARA**, encerra a execução.
- **Tabela de regras:** para cada par (estado, o que foi lido), a máquina decide: *o que escrever, para onde andar e qual é o próximo estado*.

**Frase-chave:** "Uma máquina com poucos estados e regras simples já consegue fazer contas bem longas."

---

## 3. O desafio (1 min)

**Fale:**
> "Para *n* estados, existe um número finito de máquinas possíveis. Queremos a que escreve mais 1s antes de parar. Esse número máximo se chama **Σ(n)**, e a função do castor ocupado é justamente essa."

Escreva no quadro: **n = 2** e **n = 3** (são os valores que o trabalho pede).

---

## 4. Por que é difícil (1 min) — o ponto mais interessante

**Fale:**
> "Não dá para simplesmente rodar cada máquina e esperar. Algumas nunca param. E não existe um programa geral que consiga dizer, para qualquer máquina, se ela vai parar ou não. Isso é o **problema da parada**, provado por Alan Turing em 1936."

Consequência: o castor ocupado **não é computável** no sentido geral. Por isso precisamos de limites e heurísticas.

---

## 5. Como o nosso programa funciona (3 min)

Mostre estes três passos, na ordem:

1. **Enumerar todas as máquinas.** Cada máquina é só uma tabela de regras. Para 2 estados são **20.736** tabelas; para 3 estados são **16.777.216**.
2. **Simular cada uma com um limite de 100 passos.** Isso é o *controle de parada*.
3. **Classificar o resultado em três grupos:**
   - **Parou**: entra no ranking; guardamos quantos 1s escreveu.
   - **Loop detectado**: a máquina voltou ao estado A, lendo branco, com a fita toda em branco. A configuração inicial se repete para sempre, então ela **nunca para**. Descartamos sem esperar.
   - **Limite atingido**: passou de 100 passos sem parar. Tratamos como **divergente** (não para).

**Por que 100 basta?** Os resultados conhecidos da literatura dizem que, entre as máquinas de 2 estados que param, a mais demorada leva **6 passos**; entre as de 3 estados, **21 passos**. Assim, qualquer máquina que chega a 100 passos sem parar não vai parar mais. *(Confirme esse dado no material da disciplina antes de apresentar.)*

**Frase-chave:** "Esse é o truque: não precisamos resolver o problema da parada em geral, só precisamos saber que, para este tamanho, 100 passos já são suficientes."

---

## 6. Demonstração ao vivo (3 min)

Siga esta ordem na página:

1. **Ao abrir**, a busca de 2 estados já roda sozinha. Mostre o **resumo**: total de máquinas, quantas param, quantas entram em loop e quantas divergem.
2. Aponte a **MT campeã**: 2 estados, **4 uns**, **6 passos**. Leia a tabela de regras em voz alta para uma linha.
3. Aponte os dois gráficos: o da **seção 4** mostra quantas máquinas que param escrevem 0, 1, 2... uns; o da **seção 5** mostra quantas param em 1, 2, 3... passos.
4. Mostre o **controle de parada** (campo "Limite de passos"): troque para 50 e depois volte para 100. Explique que o limite é a decisão de quando desistir de uma máquina.
5. Clique em **"3 estados"**. Explique que a busca é maior (16,7 milhões de máquinas) e leva alguns segundos. Enquanto a barra anda, fale sobre o método.
6. Quando terminar, mostre a campeã de 3 estados: **6 uns**, **14 passos**.
7. Na **seção 6 (simulação passo a passo)**, clique em **Play** e depois **Pausar**. Mostre a cabeça (quadrado laranja) andando e os 1s aparecendo em verde. Use **Anterior** e **Próximo** para explicar um passo específico.

**Frase-chave no fim da demo:** "O programa não adivinha nada: ele testa todas as máquinas possíveis dentro do limite e mostra a melhor."

---

## 7. Resultados para destacar (1 min)

| Estados (n) | Máquinas testadas | Campeã (uns) | Passos | Observação |
|---|---|---|---|---|
| 2 | 20.736 | 4 | 6 | Resultado clássico |
| 3 | 16.777.216 | 6 | 14 | Resultado clássico |

Comente que, com 4 estados, o valor já passa de **13 uns** e que ele cresce tão rápido que virou um tema de pesquisa. *(Confira o valor de n = 4 na fonte que você usar.)*

---

## 8. Limitações e próximos passos (1 min)

Seja honesto sobre o que o projeto **não** faz:

- Usa força bruta: funciona bem para 2 e 3 estados, mas não para 4 ou 5.
- O loop detectado é um caso específico (volta ao estado A com fita em branco). Outros loops são pegos apenas pelo limite de 100 passos.
- Com mais estados, seria preciso detectores de loop mais sofisticados, como comparar configurações antigas com as atuais.

**Frase-chave:** "O próximo passo seria estudar as máquinas que chegam ao limite, para ver quais realmente nunca param."

---

## 9. Perguntas prováveis (e respostas curtas)

- **"Por que não rodar as máquinas por mais tempo?"**
  Porque algumas nunca param, e nunca saberíamos quando desistir. O limite é a nossa decisão de parada.

- **"O programa tem certeza de que a campeã é a melhor?"**
  Para 2 e 3 estados, sim: testamos todas as máquinas e nenhuma que para passa de 21 passos, então o limite de 100 não deixa de fora nenhuma máquina que pararia.

- **"Por que o número cresce tão rápido?"**
  Cada estado novo multiplica o número de tabelas possíveis, e algumas máquinas de tamanho pequeno conseguem fazer contas muito longas.

- **"Isso serve para alguma coisa prática?"**
  É um problema teórico. Ele mostra os limites do que pode ser calculado e é usado para estudar a computabilidade.

---

## 10. Checklist antes de subir

- [ ] `index.html` abre no navegador sem erro.
- [ ] A busca de 2 estados termina rápido ao abrir.
- [ ] A busca de 3 estados termina (leva alguns segundos).
- [ ] Os números 4 uns / 6 passos (2 estados) e 6 uns / 14 passos (3 estados) aparecem.
- [ ] Os dois gráficos (uns e passos) aparecem preenchidos depois da busca de 3 estados.
- [ ] O campo "Limite de passos" re-roda a busca ao trocar o valor.
- [ ] Você conferiu os dados da seção 5 e da seção 7 no material da disciplina.
- [ ] Você já treinou a demo uma vez, com o cronômetro.
