# 🗳️ Boatos em Rede: Respostas e Registros

**Disciplina:** Inteligência Artificial

**Aluno:** Rafael Sampaio (Matrícula: 2374682)

> Este documento reúne as respostas dos registros experimentais (Semanas 1 a 3) e das questões discursivas (Semana 4) do notebook `Cópia_de_boatos_em_rede_ALUNO.ipynb`. Os números citados vêm das tabelas geradas no próprio notebook.

## 📅 SEMANA 1: Contexto e Modelo Base

### 📝 Registro 1 (Experimento 1: O boato se espalhando)

**Pergunta:** O que muda quando vocês trocam a semente? Em algum caso o boato "morreu" logo no início? Por que, então, faz sentido rodar **várias** simulações e tirar a média, em vez de olhar uma só?

**Resposta:**

> Além das sementes sugeridas, testei 8 sementes diferentes (707, 376, 969, 578, 494, 420, 940 e 264) para ter uma base maior de comparação. Mesmo com as mesmas regras, os resultados variaram bastante. Na rodada 5, só uma semente passou de 10% de alcance (a 707, com 12%), e um alcance maior nessa rodada não significou um boato mais forte no final: as três sementes que estavam em apenas 3% na rodada 5 (940, 969 e 264) terminaram com os maiores alcances (70%, 66% e 65%). Como são poucos casos, não dá para afirmar que isso é uma regra.
>
> Na rodada 15, o alcance sempre aumentou bastante, com média de cerca de 29% sem contar o caso em que o boato morreu. Com o passar das rodadas, o boato circula por boa parte da rede, mas isso não quer dizer que todo mundo acredita ou se engaja. As bolinhas cinzas não são só quem nunca ouviu falar do boato: também são pessoas que receberam a mensagem e não acreditaram. E mesmo quem acreditou não continua engajado para sempre: o número de espalhadores (vermelhos) diminui e o de céticos (azuis) aumenta, porque as pessoas perdem o interesse. Na rodada 40, quase não há mais vermelhos, e o alcance final ficou entre 56% e 70%. Ou seja, o boato chega a muita gente, mas perde força sozinho antes de convencer todo mundo.
>
> Na semente 420, o boato morreu logo no início: as 5 pessoas iniciais perderam o interesse antes de convencer alguém, e o alcance ficou em 2% do começo ao fim. Se eu tivesse olhado só essa simulação, concluiria que o boato não se espalha; olhando só a 940, concluiria que ele chega a 70%. Por isso faz sentido rodar várias simulações e tirar a média: uma simulação isolada depende da sorte dos sorteios, e só a média de muitas mostra o comportamento típico do modelo. A média das minhas 8 sementes foi de 55%.

### 📝 Registro 2 (Experimento 2: A forma da rede importa?)

**Pergunta:** Em qual rede o boato teve maior alcance? Em qual ele chegou ao pico mais rápido? Por que a rede "mundo pequeno" segura melhor o boato? (Dica: pensem em quantos contatos em comum vocês têm com seus amigos.)

**Resposta:**

> Comparando os três tipos de rede com 50 repetições, a rede sem escala teve o maior alcance final médio (59,6%) e também foi a que atingiu o pico de espalhadores mais rápido (rodada 18, com 14,6%). Isso acontece porque, nesse formato, existem poucos perfis com muitíssimos contatos (os influenciadores). Assim que o boato chega a um deles, se espalha rapidamente para boa parte da rede. Logo depois, porém, os espalhadores ativos caem bruscamente porque a maioria das pessoas suscetíveis já foi atingida e os espalhadores vão perdendo o interesse com o tempo.
>
> A rede aleatória teve um crescimento mais lento que a sem escala, com um pico bem menor e mais tardio (9,3% na rodada 28), decaindo também mais devagar. Como as conexões são distribuídas ao acaso e não há influenciadores, o boato se propaga em ritmo mais constante, alcançando praticamente o mesmo público final (58,3%).
>
> Já a rede mundo pequeno apresentou o menor alcance final (21,8%) e a maior taxa de boatos que morreram cedo (20%). Apesar de ter os mesmos 300 agentes e a mesma média de contatos, as conexões ficam muito fechadas em grupos locais, onde os amigos também são amigos entre si. Com poucas conexões de longa distância, o boato fica circulando nos mesmos ciclos de contatos e perde força antes de conseguir escapar para outras partes da rede.

### 📝 Registro 3 (Experimento 3: E se o boato começar por um influenciador?)

**Pergunta:** Comparem a **rodada do pico**, o **desvio padrão** e a coluna **boato morreu cedo** dos dois cenários. O que muda quando o boato começa num influenciador? Por que isso é preocupante numa véspera de eleição?

**Resposta:**

> Embora o alcance final médio seja praticamente o mesmo nos dois cenários (59,6% começando em pessoas comuns contra 59,8% em influenciadores), o comportamento inicial muda bastante. Quando o boato começa nos influenciadores, a rodada do pico cai de 18 para 11 (e o pico de espalhadores sobe de 14,6% para 16,3%), mostrando que a desinformação se espalha muito mais rápido porque esses perfis alcançam dezenas de contatos logo na primeira rodada.
>
> Além disso, o desvio padrão cai quase pela metade (de 12,7 para 7,1) e a taxa de boato morreu cedo vai de 2% para 0%. Isso significa que, quando um influenciador inicia o boato, a viralização deixa de depender da sorte e passa a ser quase garantida em todas as simulações.
>
> Numa véspera de eleição, esse cenário é especialmente preocupante porque o fator tempo é decisivo: como o pico acontece muito rápido, a notícia falsa atinge uma grande parcela dos eleitores antes que agências de checagem ou órgãos oficiais consigam desmenti-la a tempo da votação.

## 🛡️ SEMANA 2: Intervenções das Plataformas

### 📝 Registro 4 (Experimento 4: Quanto de checagem é preciso?)

**Pergunta:** Como o alcance muda conforme a checagem aumenta? O efeito é proporcional (dobrar a checagem reduz o alcance pela metade)? No mundo real, o que significaria aumentar `prob_checagem`? Quem pagaria por isso?

**Resposta:**

> Os resultados mostram que a checagem de fatos reduz drasticamente a propagação mesmo em taxas baixas. Sem checagem, o boato atinge 60,5% da rede, com pico de 14,3% de espalhadores na rodada 17. Com apenas 5% de chance de checagem por rodada, o alcance final já cai quase pela metade (35,1%), o pico de espalhadores baixa para 6,5% e a taxa de boatos que morrem cedo salta de 2% para 22%. Isso acontece porque, ao checar a notícia antes de compartilhá-la, o agente vira cético imediatamente e interrompe toda a cadeia de repasses que sairia dele.
>
> O efeito, porém, não é proporcional. Dobrar a checagem de 5% para 10% reduziu o alcance de 35,1% para 22,0%, uma queda de cerca de 37%, ou seja, menos que a metade. Já dobrar de 10% para 20% levou o alcance de 22,0% para 7,5%, uma queda de cerca de 66%, mais que a metade. Com 20% de checagem, o boato é contido logo na origem: o pico ocorre na rodada 0 (apenas os 1,7% espalhadores iniciais), o número de ativos só diminui e 78% das simulações morrem cedo. O efeito acelera quando a checagem fica alta o suficiente para os espalhadores serem barrados antes de convencer alguém. Nota-se também que o desvio padrão aumenta nos níveis intermediários (20,1 em 5%), porque o boato ora morre no início, ora consegue escapar, e volta a cair quando a checagem é alta o bastante para barrá-lo quase sempre.
>
> No mundo real, aumentar `prob_checagem` significa ampliar a capacidade e a velocidade de verificação de notícias, exibindo rótulos de alerta, links para fontes confiáveis e desmentidos diretamente nas plataformas antes que o usuário compartilhe o conteúdo. Os custos dessa operação recaem principalmente sobre as próprias plataformas digitais (equipes, parcerias com agências de checagem e sistemas automatizados de detecção), além de veículos de imprensa, instituições públicas e organizações independentes de checagem.

### 📝 Registro 5 (Experimento 5: O limite do WhatsApp)

**Pergunta:** O limite de 5 reduziu muito o alcance? E o limite de 1? Quem é mais afetado pelo limite: o eleitor comum ou o influenciador? Comparem com o resultado real do WhatsApp (notícia 5).

**Resposta:**

> O limite de 5 encaminhamentos reduziu muito pouco o alcance final médio (de 60,5% para 58,1%), mantendo praticamente o mesmo pico de espalhadores (14,2%) e a mesma taxa de boatos que morreram cedo (2%). Isso ocorre porque, com uma probabilidade de compartilhamento de 10%, a maioria dos agentes já envia o boato para menos de 5 contatos por rodada. Já o limite de 1 teve um impacto drástico: o alcance final caiu para 21,6%, o pico de espalhadores baixou para 3,3% e 22% das simulações morreram cedo, impedindo a explosão viral da notícia.
>
> O influenciador é muito mais afetado por essa medida do que o eleitor comum. Como o eleitor comum possui poucas conexões, o limite raramente altera o seu comportamento; já o influenciador, que concentra dezenas de contatos na rede sem escala, perde a capacidade de disparar o boato em massa de uma só vez e passa a agir no mesmo ritmo que qualquer outro usuário.
>
> Esse resultado é muito semelhante ao que aconteceu na prática com o WhatsApp (notícia 5): quando a plataforma reduziu o encaminhamento para 5 conversas em 2019, o efeito foi moderado (queda de cerca de 25%), mas ao restringir mensagens altamente encaminhadas para apenas 1 conversa por vez em 2020, o volume caiu 70%.

## 🎓 SEMANA 3: Educação Midiática e Proposta

### 📝 Registro 6 (Experimento 6: Quanta educação é preciso?)

**Pergunta:** A educação midiática funciona mesmo que só parte da população seja alcançada? Qual é a diferença de **prazo** entre essa intervenção e as da Semana 2 (quanto tempo leva para colocar cada uma em prática)?

**Resposta:**

> Sim. A educação midiática funciona mesmo alcançando só parte da população. Com 30% de letrados, o alcance final caiu de 60,5% para 38,0%, o pico de espalhadores caiu quase pela metade (de 14,3% para 7,1%) e ainda foi adiado da rodada 17 para a 24. Com 60% de letrados, o alcance ficou em 18,1% e 42% das simulações morreram cedo; com 90%, o alcance foi de apenas 6,3% e 78% das simulações morreram cedo. O efeito vai além das próprias pessoas educadas: cada letrado que não acredita deixa de repassar o boato, funcionando como uma barreira que também protege os seus contatos, parecido com o que acontece com a vacinação.
>
> A grande diferença está no prazo. O limite de encaminhamento é uma mudança de design que a plataforma aplica a todos os usuários praticamente de um dia para o outro, como o WhatsApp fez em 2019 e 2020. A checagem de fatos leva semanas ou meses para ser estruturada (equipes, parcerias com agências, ferramentas de detecção), mas também depende de agir rápido a cada boato. Já a educação midiática leva anos: envolve escolas, formação de professores e campanhas, e o resultado aparece aos poucos. Em compensação, ela é a mais duradoura e funciona contra qualquer boato, em qualquer plataforma, inclusive os que ainda não surgiram. Por isso as intervenções se complementam: as da Semana 2 atuam no curto prazo e a educação no longo prazo.

### 📝 Registro 7 (Experimento 7: A proposta com orçamento)

**Pergunta:** Qual proposta a equipe escolheu e por quê? Ela continua funcionando quando o boato começa em influenciadores?

**Resposta:**

> Escolhi a Proposta A: checagem de 5%, limite de encaminhamento 1 e 10% da população com letramento midiático, usando os 15 pontos do orçamento. Ela reduziu o alcance de 60,5% (sem intervenção) para 8,4%, com pico de apenas 1,8% de espalhadores e 68% das simulações em que o boato morreu cedo. A Proposta B (checagem de 6%, limite 3 e 30% de letrados, também com 15 pontos) teve resultado bom, mas pior: alcance de 13,9%.
>
> A escolha se explica pelo Experimento 5: o limite de 1 é a medida que mais atinge os influenciadores, que são o ponto fraco da rede sem escala. A checagem corta as cadeias de repasse e o letramento reduz quem acredita, então as três frentes se somam.
>
> A Proposta A continua funcionando quando o boato começa em influenciadores: o alcance sobe só de 8,4% para 10,1% (contra 59,9% sem intervenção nesse cenário), e o boato ainda morre cedo em 44% das simulações. Já a Proposta B perde mais força nesse cenário: o alcance sobe de 13,9% para 20,8%, e o boato morre cedo em só 8% das simulações. A desvantagem da Proposta A é que o limite de 1 é a medida mais restritiva para os usuários (custa 8 dos 15 pontos), o que discuto na questão D5.

## 💬 SEMANA 4: Parte Discursiva

### D1: Avaliação dos resultados

**Pergunta:** Considerando todos os experimentos, qual intervenção, sozinha, mais reduziu o alcance do boato? Apresentem os números e expliquem **por que** ela funciona tão bem, ligando o resultado às regras do modelo (qual regra ela modifica e qual efeito isso tem nos espalhadores).

**Resposta:**

> Olhando cada intervenção sozinha, as duas que mais reduziram o alcance foram o letramento midiático e a checagem de fatos. Sem nenhuma intervenção, o boato chega a 60,5% da rede. Com 90% da população letrada, o alcance caiu para 6,3% (78% das simulações morreram cedo); com 20% de checagem, caiu para 7,5% (também 78% morreram cedo). O limite de encaminhamento, mesmo no nível mais forte (limite 1), só levou o alcance a 21,6%.
>
> Considero a checagem de fatos a intervenção mais eficaz, porque ela chega a quase o mesmo resultado com uma mudança muito menor: basta cada espalhador ter 20% de chance por rodada de checar, enquanto o letramento precisa alcançar 90% da população. Mesmo com só 5% de checagem o alcance já cai para 35,1%.
>
> Ela funciona tão bem porque modifica a regra 1 do modelo, que acontece antes de tudo: se o espalhador checa, ele vira cético e para ali, sem enviar nada. Ou seja, a checagem age diretamente sobre os espalhadores e encurta o tempo em que cada um fica ativo. Somando a chance de checar (20%) com a de perder o interesse (15%), cada espalhador passa a repassar o boato por poucas rodadas e tende a gerar menos de um novo espalhador. Quando isso acontece, cada geração do boato é menor que a anterior e ele morre sozinho, como mostra o pico de espalhadores na rodada 0 com 20% de checagem. O letramento age na regra 3 (quem recebe acredita menos), e o limite age na regra 2, mas só faz diferença para quem tem muitos contatos.

### D2: Rede e influenciadores

**Pergunta:** Expliquem por que a estrutura da rede (Experimento 2) e o ponto de partida do boato (Experimento 3) mudam o resultado. Relacionem com o caso de Guarujá (notícia 2) e com o estudo do MIT (notícia 1).

**Resposta:**

> A estrutura da rede muda o resultado porque define por onde o boato consegue passar. No Experimento 2, com o mesmo número de pessoas e de contatos, a rede sem escala teve alcance de 59,6% e pico de 14,6% na rodada 18, a aleatória teve 58,3% com pico menor e mais tardio (9,3% na rodada 28), e a rede mundo pequeno segurou o boato em 21,8%, com 20% das simulações morrendo cedo. No mundo pequeno, os amigos de uma pessoa também são amigos entre si, então o boato fica circulando no mesmo grupo e os espalhadores perdem o interesse antes de ele escapar. Na rede sem escala, os poucos perfis com dezenas de contatos funcionam como atalhos que levam o boato para toda a rede.
>
> O ponto de partida importa pelo mesmo motivo. No Experimento 3, quando o boato começou nos 5 perfis mais conectados, o alcance final foi parecido (59,8%), mas o pico chegou na rodada 11 em vez da 18, o desvio padrão caiu de 12,7 para 7,1 e o boato nunca morreu cedo (0%, contra 2%). Começar num influenciador tira a sorte da equação: a viralização fica rápida e quase garantida.
>
> O caso de Guarujá (notícia 2) é exatamente esse cenário: uma página com mais de 24 mil seguidores é um nó de altíssimo grau, e o boato que saiu dela se espalhou tão rápido que nem o aviso da própria página de que não havia crianças desaparecidas chegou a tempo. O estudo do MIT (notícia 1) mostra que notícias falsas são cerca de 70% mais compartilhadas, o que equivale a um `prob_compartilhar` alto, e que quem espalha são as pessoas, não os robôs. No modelo também não há robôs: só pessoas seguindo regras simples numa rede parecida com a do Twitter (sem escala), e isso já basta para o boato viralizar.

### D3: Do modelo para o mundo real

**Pergunta:** Escolham **duas** notícias da Semana 1. Para cada uma, digam qual intervenção do modelo teria ajudado (ou ajudou) e se o resultado da simulação é coerente com o que aconteceu de fato. Usem o caso do WhatsApp (notícia 5) como uma das comparações possíveis.

**Resposta:**

> Notícia 5 (limite do WhatsApp). A intervenção do modelo correspondente é o limite de encaminhamento. Na simulação, o limite de 5 quase não mudou nada (alcance de 60,5% para 58,1%), e o limite de 1 reduziu o alcance para 21,6%, uma queda de cerca de 64%. Na vida real, o limite de 5 conversas em 2019 reduziu os encaminhamentos em cerca de 25%, e o limite de 1 conversa para mensagens muito encaminhadas, em 2020, reduziu esse tipo de mensagem em 70%. O resultado é coerente no padrão: um limite moderado tem efeito pequeno e o limite de 1 tem efeito forte. Os números não são iguais porque o modelo mede quantas pessoas acreditaram e não o volume de mensagens, e porque no modelo o limite vale para todo mundo, enquanto no WhatsApp ele vale só para mensagens já muito encaminhadas.
>
> Notícia 4 (enchentes no Rio Grande do Sul). Aqui a intervenção que teria ajudado é a checagem de fatos. No Experimento 4, com 5% de checagem o alcance já cai de 60,5% para 35,1%, e com 10% cai para 22,0%. No caso real os órgãos desmentiram cada boato, mas o desmentido chegou depois que eles já tinham se espalhado. Isso é coerente com a simulação de outra forma: o pico de espalhadores acontece por volta da rodada 17 (ou 11, se o boato começa num influenciador), então a checagem só funciona se acontecer antes do pico. No modelo, a checagem existe desde a primeira rodada; na vida real ela chega atrasada, o que significa que o efeito real foi menor que o da simulação. A lição é que a velocidade da checagem importa tanto quanto a quantidade.

### D4: Limitações do modelo

**Pergunta:** Todo modelo é uma simplificação. Citem **pelo menos três** aspectos do mundo real que a simulação ignora (por exemplo: robôs, algoritmos de recomendação, grupos de WhatsApp, polarização, o desmentido também se espalhar, pessoas que voltam a acreditar). Para cada um, expliquem se a inclusão dele **aumentaria ou diminuiria** o alcance do boato, e por quê. Proponham como uma dessas limitações poderia ser incluída no código.

**Resposta:**

> 1. Algoritmos de recomendação e robôs. No modelo, cada pessoa só alcança os próprios contatos e todo espalhador acaba perdendo o interesse. Na vida real, os algoritmos mostram conteúdo de alto engajamento para quem não segue quem postou, e robôs compartilham sem parar e nunca desistem. Incluir isso aumentaria o alcance, porque o boato teria atalhos extras e espalhadores que nunca viram céticos.
>
> 2. O desmentido também se espalha. No modelo, quem checa vira cético, mas guarda isso para si. Na vida real, quem descobre que era falso costuma avisar os contatos. Incluir isso diminuiria o alcance, porque os desmentidos protegeriam pessoas antes de o boato chegar a elas.
>
> 3. Grupos de WhatsApp. No modelo, as mensagens vão de pessoa para pessoa. Na vida real, uma única mensagem num grupo chega a centenas de pessoas de uma vez. Isso aumentaria o alcance e ainda tornaria o limite de encaminhamento menos eficaz, porque um encaminhamento para um grupo já alcança muita gente.
>
> 4. Pessoas que voltam a acreditar. No modelo, quem vira cético nunca mais acredita. Na vida real, ver o mesmo boato várias vezes faz ele parecer verdadeiro, e algumas pessoas voltam a acreditar e a compartilhar. Isso aumentaria o alcance e faria o boato durar mais.
>
> Proposta de código para o item 2: quando um espalhador checa os fatos, em vez de só virar cético, ele também envia o desmentido aos contatos, e um suscetível que recebe o desmentido vira cético e fica imune ao boato:
>
```python
def step(self):
    if self.checar_fatos():
        self.estado = CETICO
        for contato in self.vizinhos():
            if contato.estado == SUSCETIVEL and self.random.random() < self.model.prob_compartilhar:
                contato.estado = CETICO   # recebeu o desmentido antes do boato
        return
    ...
```

### D5: Proposta de solução

**Pergunta:** Apresentem a proposta da equipe para combater a desinformação, envolvendo **pelo menos dois** destes atores: plataformas digitais, poder público/Justiça Eleitoral, escolas e universidades, imprensa e agências de checagem, cidadãos. Apoiem a proposta no Experimento 7. Depois, apresentem honestamente **um argumento contra** a própria proposta: custos, riscos para a liberdade de expressão, quem decide o que é falso, possibilidade de abuso. Expliquem como a proposta lida com esse risco.

**Resposta:**

> Minha proposta segue a Proposta A do Experimento 7 e envolve três atores. As plataformas digitais aplicam o limite de 1 encaminhamento para mensagens que já foram muito encaminhadas, como o WhatsApp fez em 2020, e exibem alertas com links para checagens. A imprensa e as agências de checagem verificam os boatos que mais circulam, o que no modelo corresponde aos 5% de checagem. As escolas e universidades incluem educação midiática no currículo, começando por 10% da população e ampliando com o tempo. A Justiça Eleitoral completa a proposta com as regras que já existem para conteúdo feito por IA (notícia 6).
>
> Na simulação, essa combinação reduziu o alcance do boato de 60,5% para 8,4%, e continuou funcionando quando o boato começou em influenciadores (10,1%, contra 59,9% sem intervenção). Nenhuma medida sozinha, com o mesmo orçamento, chegou perto disso.
>
> O principal argumento contra a proposta é o risco à liberdade de expressão. O limite de 1 encaminhamento atinge todo mundo, inclusive quem compartilha informação verdadeira e útil. E a checagem levanta a pergunta de quem decide o que é falso: uma agência ou um governo poderia usar esse poder para silenciar críticas ou adversários políticos, especialmente numa eleição.
>
> A proposta lida com esse risco de três formas. Primeiro, o limite não apaga nada: ele só reduz a velocidade de mensagens que já viralizaram, e a pessoa continua podendo enviar o conteúdo, uma conversa por vez. Segundo, a checagem deve ser feita por agências independentes, com método público, e deve rotular o conteúdo em vez de removê-lo, com direito de contestação. Terceiro, a educação midiática é a parte menos invasiva: ela não decide nada pelas pessoas, só as ensina a desconfiar. Se ainda assim o limite de 1 for considerado restritivo demais, a Proposta B (limite 3 com mais letramento) é uma alternativa mais leve, com custo de eficácia: alcance de 13,9%.

### D6: O papel da Inteligência Artificial

**Pergunta:** A IA aparece dos dois lados desse problema. Deem um exemplo de como a IA **piora** a desinformação (pensem em deepfakes, notícia 6) e um de como ela pode **ajudar** a combatê-la. Em termos do modelo, qual parâmetro um deepfake muito convincente alteraria? Testem essa mudança no código abaixo e comentem o resultado.

**Resposta:**

> A IA piora a desinformação principalmente com os deepfakes (notícia 6): vídeos e áudios falsos tão realistas que parecem gravações verdadeiras de um candidato. A IA também permite produzir boatos em grande quantidade e de forma personalizada, com muito pouco custo. Por isso o TSE proibiu deepfakes realistas sobre candidatos, mesmo com rótulo, e proibiu novos conteúdos sintéticos nas 72 horas antes e 24 horas depois da votação.
>
> Do outro lado, a IA pode ajudar a combater o problema: sistemas de detecção podem identificar conteúdos manipulados ou boatos que estão viralizando e avisar as agências de checagem mais cedo, e ferramentas de marca d'água podem identificar conteúdo gerado por IA. No modelo, isso equivale a aumentar a `prob_checagem`.
>
> Em termos do modelo, um deepfake muito convincente altera o `prob_acreditar`, porque mais pessoas acreditam quando recebem. No teste, subir de 0,5 para 0,8 aumentou o alcance de 60,5% para 80,5%, quase dobrou o pico de espalhadores (de 14,3% para 27,8%) e antecipou o pico da rodada 17 para a 14. O boato também nunca morreu cedo (0%) e o desvio padrão caiu de 10,6 para 4,1, ou seja, a viralização ficou quase garantida.
>
> Com a Proposta A aplicada, o deepfake teve alcance de 26,6%, bem menor que os 80,5% sem intervenção, mas mais que o triplo dos 8,4% que a mesma proposta alcançou com um boato comum. Isso mostra que a proposta continua ajudando, mas perde força contra conteúdos muito convincentes, e por isso as regras específicas para deepfakes e o uso de IA para acelerar a checagem são necessários.
