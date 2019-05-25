---
title: JavaScript — Programação orientada a eventos? Código assíncrono? WTF?
date: '2018-03-13T16:43:16.088Z'
template: "post"
draft: false
slug: "/posts/programacao-orientada-a-eventos-codigo-assincrono-wtf/"
category: "Software Development"
tags:
  - "nodejs"
  - "javascript"
  - "software"
  - "development"
  - "beginner"
description: "O ano é 2017 e eu entrei em parafuso com tanta coisa acontecendo ao mesmo tempo na minha vida. Neste post falo um pouco de minha trajetória profissional e faço uma breve introdução a JavaScript. Espero que gostem."
---

### Como me meti com isso?

2017, muita coisa aconteceu na minha vida. Entre tanta coisa deixei as forças armadas e me mudei para Florianópolis para trabalhar como desenvolvedor full-stack. Embora tivesse zero experiência com front-end essa seria a posição que iria ocupar na empresa dos meus sonhos. A experiência por mais que tenha sido fantástica por um lado (novos ares, amizades e desafios) por outro não foi das melhores. Percebi que havia muito a aprender e onde eu estava _não havia_ tempo e nem espaço para isso. Prefiro não entrar em detalhes sobre _como o pior aconteceu_. Algumas semanas mais tarde comecei a trabalhar em outra empresa realizando manutenção no back-end de uma aplicação Java mas não estava feliz e foi ai que resolvi mudar um pouco.

### Aprendendo JavaScript

Decidi focar no front-end começando com HTML5 e JavaScript. Não estava afim de pagar por um curso caro e os primeiros vídeos que eu assisti no Youtube além de muito cansativos não eram nada direto ao ponto. Optei então por iniciar com os cursos do [Code Academy](www.codeacademy.com). São excelentes cursos para iniciar em qualquer nova linguagem e em pouco tempo você consegue aprender o suficiente para fazer bem mais que um simples _Hello World_. HTML foi bem tranquilo de aprender e eu me julgo até agora sobre o por que de não ter me interessado pelo assunto antes.

Agora falando em JavaScript… Bem, é uma linguagem simples, poderosa e que eu estou realmente amando. Porém o fato de ser uma linguagem _assíncrona_ ainda me causa dores de cabeça vez ou outra e também _efeitos especiais inesperados_.

#### Non-blocking

JavaScript é non-blocking e isso causa muita dor de cabeça em qualquer iniciante, mas você percebe os benefícios tão logo se acostuma.

Quando dizemos que uma tecnologia é non-blocking estamos dizendo que suas tasks/jobs rodam concorrentemente, isso é, _ninguém espera por ninguém_.

Se você tem _um trecho de código_ que precisa executar algo em background, o seu código vai continuar a ser executado e a tarefa em questão vai ser executada quando _for possível_, isto é concorrência. Exemplo:

```
console.log(1);  
setTimeout(function() {  
    console.log(3)  
}, 1000);  
console.log(2);
```
O que aconteceu?

*   Linha 1, seu interpretador leu a primeira linha e imprimiu **1**
*   Linha 2, o interpretador encontrou uma task que deverá ser executada daqui a 1 seg. Como _ninguém espera por ninguém_ o seu interpretador…
*   Linha 5, lê a sua última linha e imprime **2**.

 E a segunda linha? Ela vai ser alocada novamente na pilha de execução após se passarem os 1000 milésimos e por fim executada imprimindo **3**.

Então, ao invés de o resultado ser 1, 3, 2 como estamos acostumados a ver em linguagens como Java e C#, o resultado será 1, 2, 3.

Entrarei em mais detalhes no próximo artigo onde vou falar sobre EventLoop, task queue e call stack.

#### Ok, mas onde entra a tal “Orientação a eventos”?

De uma forma curta, grossa e mal polida, orientação a eventos é um paradigma onde seu programa responde a ações do cliente/usuário. Orientação a objetos e orientação a eventos não são paradigmas opostos, o primeiro diz respeito a anatomia de sua aplicação e a segunda sobre como sua aplicação “reage”. Vamos citar por exemplo o finado Delphi: Uma aplicação em Delphi pode ser orientada a objetos (já que utiliza Object Pascal) e ao mesmo tempo ser orientada a eventos, já que vai responder a iterações do usuário (botões, listas e etc) e cada iteração dispara um comportamento no seu código, caso haja associação.

#### O que vem por aí

Esse foi meu primeiro artigo. No meu próximo artigo vou falar sobre EventLoop, TaskQueue e CallStack. Você vai entender como o _runtime_ aloca as tarefas e como decide qual realizar primeiro, vai ser top!

Gostou desse artigo? Então dispare o evento _shareThisPost_.

Até a próxima pessoal :)