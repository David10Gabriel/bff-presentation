---
marp: true
theme: default
---

<!-- class: invert -->

# Simplificando o Front-end com BFF\*

## \*Significa Back-end For Front-end

---

## Sumário

1. Introdução
2. O que é BFF?
3. Quais problemas BFF resolve
4. Arquitetura do BFF
5. Desafios e considerações
6. Exemplos de uso do BFF na indústria
7. Conclusão

---

## Introdução

1. A importância da separação entre front-end e back-end em aplicações web.
<!--

- A separação é importante pois proporciona modularidade e especialização de código.

- Especialização: O front-end deve forcar em prover uma boa experiência ao usuário e o back-end em gerir lógicas de negócio e guardar e processar as informações.

- Na TerraMagna, historicamente o front-end sempre teve muita lógica embutida, e isso borra os limites entre o que deve ser feito no back e o que deve ser feito no front, além de aumentar a complexidade do que se tem no front-end -->

2. BFF como uma abordagem para otimizar a comunicação entre front-end e back-end e reduzir complexidade aplicada no front-end.

---

## O que é BFF (Back-end For Front-end)?

- Definição básica de BFF e sua função principal.
<!-- 1. BFF é uma camada intermediária entre o front-end e o back-end de uma aplicação web que visa otimizar a comunicação entre as partes. -->

- Como o BFF atua como uma camada intermediária entre o front-end e o back-end.
<!--

2. Na renderização de uma página, o front faria apenas uma requisição para um endpoint específico para aquela página, e o BFF se encarregaria de:

- Cachear informações que podem estar em cache a nível de usuário, cliente ou grupos de clientes;
- Fazer as requisições para os múltiplos serviços;
- Agregar e formatar as informações;

Quando o front-end precisa enviar informações para o back-end, o BFF pode ter o papel de validador. -->

- Destaque para a flexibilidade e personalização oferecidas pelo BFF em relação às necessidades do front-end.
<!--

3. Exemplos:

- Endpoints personalizados: Uma rota por página (?).

- Adaptação de dados: O BFF pode alterar os dados recebidos dos serviços para uma estrutura que faça mais sentido para a página, filtrar informações irrelevantes e combinar informações diferentes em um formato adequado para a interface do usuário.

- Otimização de desempenho: Cache, a agregação de múltiplas chamadas de API em uma única solicitação, e o pré-processamento de dados (tradução).

- Muito mais rápido e menos custoso trocar tecnologias no front-end, como o que fizemos com a plataforma nova, visto que o front fica focado apenas na interface e usabilidade. -->

---

## Problemas resolvidos pelo BFF

1. Over-fetching e under-fetching de dados
<!-- 1. Só trafega o que o front realmente precisa -->
2. Dificuldade de adaptação às necessidades do front-end
<!-- 2. Possibilidade de um endpoint por página e estrutura de dados adaptável ao front -->
3. Complexidade e acoplamento entre front-end e back-end
<!-- 3. O front fica muito mais simples, pois a maior parte da lógica fica no back-end ou no BFF, e o BFF diminui o acoplamento entre o front e o back -->

4. Performance e tempo de resposta
<!-- 4. O front faz menos chamadas para o back e pode haver cache no BFF -->

---

## Como o BFF ajuda a diminuir a complexidade do código no front

1. Agregação de dados

   - Cada página pode receber apenas os dados dos quais precisa.

2. Normalização e adaptação de dados

   - A página recebe os dados traduzidos, ordenados e condensados (podemos combinar informações para gerar um status de uma operação), na estrutura que precisar.
     - Adeus enums de tradução;
     - Adeus repetir o uso das mesmas funções em diversas páginas para formatar moedas, datas, CNPJ e CPF e etc;

3. Exposição de endpoints customizados e lógica de negócio no BFF

   - Não precisaríamos de vários dos services no front-end;
   - Poderíamos fazer toda a validação dos dados no BFF, retornando a mensagem de erro que o front deve renderizar em cada caso.

---

## Desafios e considerações

- Discussão sobre os possíveis desafios e considerações ao implementar o BFF, como a complexidade da arquitetura.
- Sugestão de boas práticas para superar esses desafios e maximizar os benefícios do BFF.

---

## Tá, mas quais os tradeoffs?

1. Complexidade adicional, uma nova camada

   - De fato é um item novo pra se preocupar (só é preciso um novo serviço de início, mas no futuro pode ser necessário quebrar em mais de um).
   - Além das novas rotas dos serviço, seria necessário implementar a rota no client do serviço, e o endpoint no BFF com todas as tratativas que antes eram feitas no front.

2. Aumento da complexidade da infraestrutura (?)

   - Se fossemos usar para validação de dados enviados para o back, precisaríamos hospedar esse serviço no Brasil, para que a latência seja mais baixa.

---

## Tá, mas quais os tradeoffs?

3. Potencial SPOF (Single Point Of Failure)

   - Se o BFF enfrentar problemas ou ficar indisponível, todas as solicitações do front-end aos back-ends serão afetadas. Dá-lhe monitoramento para minimizar o impacto de possíveis falhas.

4. Introdução de possíveis gargalos de desempenho
   - Se o BFF não for bem implementado, pode haver a introdução de possíveis gargalos de desempenho.

---

## Exemplos de uso do BFF na indústria

Usado por

- [Soundcloud](https://www.thoughtworks.com/insights/blog/bff-soundcloud)
- Flickr
- [Netflix](https://netflixtechblog.com/seamlessly-swapping-the-api-backend-of-the-netflix-android-app-3d4317155187)

Recomendado por

- [Microsoft](https://learn.microsoft.com/en-us/azure/architecture/patterns/backends-for-frontends)
- [IBM](https://www.ibm.com/cloud/blog/announcements/bluemix-developer-console-bff-backend-for-frontend-pattern)

---

## Conclusão

- Recapitulação dos principais pontos abordados na apresentação.
<!--  -->
- Reforço dos benefícios do BFF para a separação entre front-end e back-end.
<!--  -->
- Estímulo à adoção do BFF em projetos futuros e encorajamento à exploração de suas vantagens.
<!--  -->

---

## Bibliografia

- [Why big companies and rapidly growing startups need Back-end for Front-end](https://medium.com/blue-harvest-tech-blog/why-big-companies-and-rapidly-growing-startups-need-back-end-for-front-end-ee8e6ab8f575)
- [The BFF Pattern (Backend for Frontend): An Introduction](https://blog.bitsrc.io/bff-pattern-backend-for-frontend-an-introduction-e4fa965128bf)
