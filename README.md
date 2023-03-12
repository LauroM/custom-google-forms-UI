# custom-google-forms-UI

Teste customizando Google Forms na interface frontend.

### Passo 0:
Para o teste, foi criado um formulário apenas para recolher telefone e email do usuário.
Formulário basico no index.html com dois inputs(email e telefone) e um botão de subimit.

![alt text](/assets/forms.png)

### Passo 1:
Acessar a conta do google e propucar por Formulários.

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
O linke gerado é algo mais ou menos assim:

```
https://docs.google.com/forms/d/e/1FAIpQLScOZXt985Ly-pGu9EO67klsahg43498ow/viewform?usp=pp_url&entry.1936217447=teste@gmail.com&entry.678287860=31999999999
```

Agora é necessário modificar este link. Perceba que no final do link contém as duas respostas dados no passo anterior, teste@gmail.com e 31999999999.

Estrutura:
- Formulário: https://docs.google.com/forms/d/e/1FAIpQLScOZXt985Ly-pGu9EO67klsahg43498ow/viewform
- Campo email: entry.1936217447
- Campo telefone: entry.678287860

No arquivo index.html o entry.1936217447 será add no input de email e o entry.678287860 ao input de telefone

```
Linha 18: <input id="email" class="input" type="text" placeholder=" " name="entry.1936217447">
Linha 23: <input id="phone" class="input" type="text" placeholder=" " name="entry.678287860">
```