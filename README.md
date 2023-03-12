# custom-google-forms-UI

Teste interface customizada + Google Forms.

### Passo 0:
Para o teste, foi criado um formulário para recolher telefone e email do usuário.
O formulário do index.html contém dois inputs(email e telefone) e um botão de subimit.

<p align="center">
    <img src="/assets/forms.png" title="forms" style="display: block; margin-left: auto; margin-right: auto; width: 70%;">
</p>

### Passo 1:
Acessar Google Forms: https://forms.google.com

![alt text](/assets/step1.png)

### Passo 2:
Crie perguntas, como no exemplo email e telefone.

![alt text](/assets/step2.png)

### Passo 3:
Após criar o formulário, na barra superior nos 3 pontinhos escolha a opção "Gerar link preenchido automaticamente".

![alt text](/assets/step3.png)

### Passo 4
Preencha o formulário e então clique em "Gerar link". Em seguida copie o link que foi gerado.

![alt text](/assets/step4.png)

### Passo 5
O link gerado é algo mais ou menos assim:

```
https://docs.google.com/forms/d/e/1FAIpQLScOZXt985Ly-pGu9EO67klsahg43498ow/viewform?usp=pp_url&entry.1936217447=teste@gmail.com&entry.678287860=31999999999
```

Perceba que no final do link aparece as duas respostas do passo anterior, teste@gmail.com e 31999999999. Agora é necessário modificar a URL. 

Estrutura do link:
- Formulário: https://docs.google.com/forms/d/e/1FAIpQLScOZXt985Ly-pGu9EO67klsahg43498ow/viewform
- Campo email: entry.1936217447
- Campo telefone: entry.678287860

No arquivo index.html o entry.1936217447 será adicionado no input de email e o entry.678287860 no input de telefone. Também será adicionado a referência do formulário trocando viewform por formResponse para obtermos a URL do POST.

```
Linha 13:  <form class="form" action="https://docs.google.com/forms/d/e/1FAIpQLScOZXt985Ly-pGu9EO67klsahg43498ow/formResponse">

Linha 17: <input id="email" class="input" type="text" placeholder=" " name="entry.1936217447">

Linha 22: <input id="phone" class="input" type="text" placeholder=" " name="entry.678287860">
```

Feito essa integração com o Google Forms, já pode testar se o formulário customizado irá salvar os inputs.

### Passo 6
Testando o formulário customizado.

<p align="center">
    <img src="/assets/step6a.png" title="step6a" style="display: block; margin-left: auto; margin-right: auto; width: 70%;">
    <br>
    <em>Preenchendo os campos</em>
    <br><br><br>
    <img src="/assets/step6b.png" title="step6b" style="display: block; margin-left: auto; margin-right: auto; width: 70%;">
    <br>
    <em>Página de confirmação após submter formulário</em>
    <br><br><br>
    <img src="/assets/step6c.png" title="step6c" style="display: block; margin-left: auto; margin-right: auto; width: 70%;">
    <br>
    <em>Registro salvo</em>
</p>


Poderia validação de email e telefone tanto no frontend quanto no Google forms, mas o propósito aqui é apenas testar a possibilidade de usar o Google Forms customizado.