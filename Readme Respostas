# 🗳️ Boatos em Rede — Respostas e Registros da Equipe

**Disciplina:** Inteligência Artificial

**Membros da Equipe:**

1. Rafael Sampaio (Matrícula: 2374682)

> Este documento reúne todas as respostas dos registros experimentais (Semanas 1 a 3) e das questões discursivas (Semana 4) referentes ao notebook `Cópia_de_boatos_em_rede_ALUNO.ipynb`.

## 📅 SEMANA 1 — Contexto e Modelo Base

### 📝 Registro 1 (Experimento 1 — O boato se espalhando)

**Pergunta:** O que muda quando vocês trocam a semente? Em algum caso o boato "morreu" logo no início? Por que, então, faz sentido rodar **várias** simulações e tirar a média, em vez de olhar uma só?

**Resposta da equipe:**

> Ao trocar a semente, muda toda a parte aleatória da simulação: tanto o formato exato das conexões sorteadas na rede quanto quem são os 5 espalhadores iniciais e quais contatos decidem acreditar, repassar ou perder o interesse em cada rodada. Em alguns testes (como na semente 494), o boato morre logo no início, alcançando apenas uma pequena fração da população, enquanto em outras sementes ele atinge influenciadores logo cedo e se espalha para a maior parte da rede. Por causa dessa forte variação causada pelo acaso, olhar apenas uma execução pode gerar uma conclusão distorcida; rodar várias simulações e tirar a média permite identificar o comportamento padrão e confiável do modelo.

### 📝 Registro 2 (Experimento 2 — A forma da rede importa?)

**Pergunta:** Em qual rede o boato teve maior alcance? Em qual ele chegou ao pico mais rápido? Por que a rede "mundo pequeno" segura melhor o boato?

**Resposta da equipe:**

> Comparando os três tipos de rede com 50 repetições, a rede **sem escala** teve o maior alcance final médio (59,6%) e também foi a que atingiu o pico de espalhadores mais rápido (rodada 18, com 14,6%). Isso acontece porque, nesse formato, existem poucos perfis com muitíssimos contatos (os influenciadores). Assim que o boato chega a um deles, se espalha rapidamente para boa parte da rede. Logo depois, porém, os espalhadores ativos caem bruscamente porque a maioria das pessoas suscetíveis já foi atingida e os espalhadores vão perdendo o interesse com o tempo.
>
> A rede **aleatória** teve um crescimento mais lento que a sem escala, com um pico bem menor e mais tardio (9,3% na rodada 28), decaindo também mais devagar. Como as conexões são distribuídas ao acaso e não há influenciadores, o boato se propaga em ritmo mais constante, alcançando praticamente o mesmo público final (58,3%).
>
> Já a rede **mundo pequeno** apresentou o menor alcance final (21,8%) e a maior taxa de boatos que morreram cedo (20%). Apesar de ter os mesmos 300 agentes e a mesma média de contatos, as conexões ficam muito fechadas em grupos locais, onde os amigos também são amigos entre si. Com poucas conexões de longa distância, o boato fica circulando nos mesmos ciclos de contatos e perde força antes de conseguir escapar para outras partes da rede.

### 📝 Registro 3 (Experimento 3 — E se o boato começar por um influenciador?)

**Pergunta:** Comparem a **rodada do pico**, o **desvio padrão** e a coluna **boato morreu cedo** dos dois cenários. O que muda quando o boato começa num influenciador? Por que isso é preocupante numa véspera de eleição?

**Resposta da equipe:**

> Embora o alcance final médio seja praticamente o mesmo nos dois cenários (59,6% começando em pessoas comuns contra 59,8% em influenciadores), o comportamento inicial muda bastante. Quando o boato começa nos influenciadores, a **rodada do pico** cai de 18 para 11 (e o pico de espalhadores sobe de 14,6% para 16,3%), mostrando que a desinformação se espalha muito mais rápido porque esses perfis alcançam dezenas de contatos logo na primeira rodada.
>
> Além disso, o **desvio padrão** cai quase pela metade (de 12,7 para 7,1) e a taxa de **boato morreu cedo** vai de 2% para 0%. Isso significa que, quando um influenciador inicia o boato, o viralizamento deixa de depender da sorte e passa a ser quase garantido em todas as simulações.
>
> Numa véspera de eleição, esse cenário é especialmente preocupante porque o fator tempo é decisivo: como o pico acontece muito rápido, a notícia falsa atinge uma grande parcela dos eleitores antes que agências de checagem ou órgãos oficiais consigam desmenti-la a tempo da votação.

## 🛡️ SEMANA 2 — Intervenções das Plataformas

### 📝 Registro 4 (Experimento 4 — Quanto de checagem é preciso?)

**Pergunta:** Como o alcance muda conforme a checagem aumenta? O efeito é proporcional (dobrar a checagem reduz o alcance pela metade)? No mundo real, o que significaria aumentar `prob_checagem`? Quem pagaria por isso?

**Resposta da equipe:**

> Os resultados mostram que a checagem de fatos reduz drasticamente a propagação mesmo em taxas baixas, mas o efeito não é estritamente linear: cada aumento gera um ganho ainda mais forte na contenção. Sem checagem, o boato atinge 60,5% da rede com pico de 14,3% de espalhadores na rodada 17. Com apenas 5% de chance de checagem por rodada, o alcance final já cai quase pela metade (35,1%), o pico de espalhadores baixa para 6,5% e a taxa de boatos que morrem cedo salta de 2% para 22%. Aumentando para 10%, o alcance cai para 22,0% (36% morrem cedo), e com 20% o boato é barrado logo na origem: o pico ocorre na rodada 0 (apenas os 1,7% espalhadores iniciais), 78% das simulações morrem cedo e o alcance médio fica limitado a 7,5%. Isso ocorre porque, ao checar a notícia antes de compartilhá-la, o agente vira cético imediatamente e interrompe toda a cadeia de repasses que sairia dele.
>
> No mundo real, aumentar `prob_checagem` significa ampliar a capacidade e a velocidade de verificação de notícias, exibindo rótulos de alerta, links para fontes confiáveis e desmentidos diretamente nas plataformas antes que o usuário compartilhe o conteúdo. Os custos dessa operação recaem principalmente sobre as próprias plataformas digitais (investimento em equipes, parcerias com agências de checagem e sistemas automatizados de detecção), além de veículos de imprensa, instituições públicas e organizações independentes de fact-checking.

### 📝 Registro 5 (Experimento 5 — O limite do WhatsApp)

**Pergunta:** O limite de 5 reduziu muito o alcance? E o limite de 1? Quem é mais afetado pelo limite: o eleitor comum ou o influenciador? Comparem com o resultado real do WhatsApp (notícia 5).

**Resposta da equipe:**

> O **limite de 5** encaminhamentos reduziu muito pouco o alcance final médio (de 60,5% para 58,1%), mantendo praticamente o mesmo pico de espalhadores (14,2%) e a mesma taxa de boatos que morreram cedo (2%). Isso ocorre porque, com uma probabilidade de compartilhamento de 10%, a maioria dos agentes já envia o boato para menos de 5 contatos por rodada. Já o **limite de 1** teve um impacto drástico: o alcance final caiu para 21,6%, o pico de espalhadores baixou para 3,3% e 22% das simulações morreram cedo, impedindo a explosão viral da notícia.
>
> O **influenciador** é muito mais afetado por essa medida do que o eleitor comum. Como o eleitor comum possui poucas conexões, o limite raramente altera o seu comportamento; já o influenciador, que concentra dezenas de contatos na rede sem escala, perde a capacidade de disparar o boato em massa de uma só vez e passa a agir no mesmo ritmo que qualquer outro usuário.
>
> Esse resultado é muito semelhante ao que aconteceu na prática com o WhatsApp (notícia 5): quando a plataforma reduziu o encaminhamento para 5 chats em 2019, o efeito foi moderado (queda de ~25%), mas ao restringir mensagens altamente encaminhadas para apenas 1 conversa por vez em 2020, o volume caiu 70%.

## 🎓 SEMANA 3 — Educação Midiática e Proposta da Equipe

### 📝 Registro 6 (Experimento 6 — Quanta educação é preciso?)

**Pergunta:** A educação midiática funciona mesmo que só parte da população seja alcançada? Qual é a diferença de **prazo** entre essa intervenção e as da Semana 2 (quanto tempo leva para colocar cada uma em prática)?

**Resposta da equipe:**

> *(Preencha aqui a resposta do Registro 6)*

### 📝 Registro 7 (Experimento 7 — A proposta da equipe com orçamento)

**Pergunta:** Qual proposta a equipe escolheu e por quê? Ela continua funcionando quando o boato começa em influenciadores?

**Resposta da equipe:**

> *(Preencha aqui a resposta do Registro 7)*

## 💬 SEMANA 4 — Parte Discursiva

### D1 — Avaliação dos resultados

**Pergunta:** Considerando todos os experimentos, qual intervenção, sozinha, mais reduziu o alcance do boato? Apresentem os números e expliquem **por que** ela funciona tão bem, ligando o resultado às regras do modelo (qual regra ela modifica e qual efeito isso tem nos espalhadores).

**Resposta da equipe:**

> *(Preencha aqui a resposta da questão D1 — 10 a 20 linhas)*

### D2 — Rede e influenciadores

**Pergunta:** Expliquem por que a estrutura da rede (Experimento 2) e o ponto de partida do boato (Experimento 3) mudam o resultado. Relacionem com o caso de Guarujá (notícia 2) e com o estudo do MIT (notícia 1).

**Resposta da equipe:**

> *(Preencha aqui a resposta da questão D2 — 10 a 20 linhas)*

### D3 — Do modelo para o mundo real

**Pergunta:** Escolham **duas** notícias da Semana 1. Para cada uma, digam qual intervenção do modelo teria ajudado (ou ajudou) e se o resultado da simulação é coerente com o que aconteceu de fato. Usem o caso do WhatsApp (notícia 5) como uma das comparações possíveis.

**Resposta da equipe:**

> *(Preencha aqui a resposta da questão D3 — 10 a 20 linhas)*

### D4 — Limitações do modelo

**Pergunta:** Todo modelo é uma simplificação. Citem **pelo menos três** aspectos do mundo real que a simulação ignora (por exemplo: robôs, algoritmos de recomendação, grupos de WhatsApp, polarização, o desmentido também se espalhar, pessoas que voltam a acreditar). Para cada um, expliquem se a inclusão dele **aumentaria ou diminuiria** o alcance do boato, e por quê. Proponham como uma dessas limitações poderia ser incluída no código.

**Resposta da equipe:**

> *(Preencha aqui a resposta da questão D4 — 10 a 20 linhas)*

### D5 — Proposta de solução

**Pergunta:** Apresentem a proposta da equipe para combater a desinformação, envolvendo **pelo menos dois** destes atores: plataformas digitais, poder público/Justiça Eleitoral, escolas e universidades, imprensa e agências de checagem, cidadãos. Apoiem a proposta no Experimento 7. Depois, apresentem honestamente **um argumento contra** a própria proposta: custos, riscos para a liberdade de expressão, quem decide o que é falso, possibilidade de abuso. Expliquem como a proposta lida com esse risco.

**Resposta da equipe:**

> *(Preencha aqui a resposta da questão D5 — 10 a 20 linhas)*

### D6 — O papel da Inteligência Artificial

**Pergunta:** A IA aparece dos dois lados desse problema. Deem um exemplo de como a IA **piora** a desinformação (pensem em deepfakes, notícia 6) e um de como ela pode **ajudar** a combatê-la. Em termos do modelo, qual parâmetro um deepfake muito convincente alteraria? Testem essa mudança no código abaixo e comentem o resultado.

**Resposta da equipe:**

> *(Preencha aqui a resposta da questão D6 — 10 a 20 linhas)*
