# custom-google-forms-UI

Interface customizada + Google Forms. Objetivo do teste é criar um formulário para recolher telefone e email do usuário.

### Passo 0:

Primeiro crie o arquivo index.html que será a interface do formulário contendo dois inputs(email e telefone) e um botão de subimit.

- index.html
```
<!DOCTYPE html>
<html>

    <head>
        <meta charset="utf-8">
        <meta name="viewport" content="width=device-width, initial-scale=1">
        <link rel="stylesheet" href="forms.css">
        <script src="forms.js"></script>
        <title>Teste Custom Google Forms</title>
    </head>

    <body>
        <form class="form" action="">
            <div class="title">Teste</div>
            <div class="subtitle">Custom Google Forms UI</div>
            <div class="input-container ic2">
                <input id="email" class="input" type="text" placeholder=" " name="">
                <div class="cut cut-short"></div>
                <label for="email" class="placeholder">Email</label>
            </div>
            <div class="input-container ic2">
                <input id="phone" class="input" type="text" placeholder=" " name="">
                <div class="cut"></div>
                <label for="phone" class="placeholder">Telefone</label>
            </div>
            <button type="submit" class="submit">submit</button>
        </form>
    </body>

</html>
```

Crie também um arquivo css para dar uma embelezada na interface.

- forms.css
```
body {
align-items: center;
    background-color: #000;
    display: flex;
    justify-content: center;
    height: 100vh;
}

.form {
    background-color: #15172b;
    border-radius: 20px;
    box-sizing: border-box;
    height: 430px;
    padding: 20px;
    width: 320px;
}

.title {
    color: #eee;
    font-family: sans-serif;
    font-size: 36px;
    font-weight: 600;
    margin-top: 30px;
    text-align: center;
}

.subtitle {
    color: #eee;
    font-family: sans-serif;
    font-size: 16px;
    font-weight: 600;
    margin-top: 10px;
    text-align: center;
}

.input-container {
    height: 50px;
    position: relative;
    width: 100%;
}

.ic1 {
    margin-top: 40px;
}

.ic2 {
    margin-top: 30px;
}

.input {
    background-color: #303245;
    border-radius: 12px;
    border: 0;
    box-sizing: border-box;
    color: #eee;
    font-size: 18px;
    height: 100%;
    outline: 0;
    padding: 4px 20px 0;
    width: 100%;
}

.cut {
    background-color: #15172b;
    border-radius: 10px;
    height: 20px;
    left: 20px;
    position: absolute;
    top: -20px;
    transform: translateY(0);
    transition: transform 200ms;
    width: 76px;
}

.cut-short {
    width: 50px;
}

.input:focus ~ .cut,
.input:not(:placeholder-shown) ~ .cut {
    transform: translateY(8px);
}

.placeholder {
    color: #65657b;
    font-family: sans-serif;
    left: 20px;
    line-height: 14px;
    pointer-events: none;
    position: absolute;
    transform-origin: 0 50%;
    transition: transform 200ms, color 200ms;
    top: 20px;
    }

.input:focus ~ .placeholder,
.input:not(:placeholder-shown) ~ .placeholder {
    transform: translateY(-30px) translateX(10px) scale(0.75);
}

.input:not(:placeholder-shown) ~ .placeholder {
    color: #808097;
}

.input:focus ~ .placeholder {
    color: #dc2f55;
}

.submit {
    background-color: #08d;
    border-radius: 12px;
    border: 0;
    box-sizing: border-box;
    color: #eee;
    cursor: pointer;
    font-size: 18px;
    height: 50px;
    margin-top: 38px;
    text-align: center;
    width: 100%;
}

.submit:active {
    background-color: #06b;
}
```

- Resultado:
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

<p align="center">
    <img src="/assets/estruturaurl.png" title="Estrutura do link" style="display: block; margin-left: auto; margin-right: auto; width: 100%;">
    <br>
    <em>Estrutura do link</em>
</p>

No arquivo index.html o entry.1936217447 será adicionado no input de email e o entry.678287860 no input de telefone. Também será adicionado a referência do formulário trocando viewform por formResponse para obtermos a URL do POST.

```
Linha 13:  <form class="form" action="https://docs.google.com/forms/d/e/1FAIpQLScOZXt985Ly-pGu9EO67klsahg43498ow/formResponse">

Linha 17: <input id="email" class="input" type="text" placeholder=" " name="entry.1936217447">

Linha 22: <input id="phone" class="input" type="text" placeholder=" " name="entry.678287860">
```

Feito essa integração com o Google Forms, já pode testar se o formulário customizado irá salvar os inputs.

### Teste

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


Poderia incluir validação de email e telefone tanto no frontend quanto no Google forms, mas o propósito aqui é apenas testar a possibilidade de usar o Google Forms adaptado para o frontend.