
# Página com Layout de Sessões - HTML e CSS

Este projeto foi criado para demonstrar como criar uma página com layout dividido em três seções, com um `header` fixo no topo e cada seção possuindo sua própria rolagem independente. Abaixo segue a explicação detalhada do que foi implementado.

## Estrutura e Layout

### 1. Header Fixo
- O `header` da página é fixo no topo da tela, possui a cor **roxa** e contém um texto centralizado.
- Para manter o header fixo, foi usada a propriedade `position: fixed`. Isso garante que o header esteja sempre visível, independentemente de qualquer rolagem nas seções da página.

### 2. Três Seções com Rolagem Independente
A página contém três seções principais (`left`, `center`, `right`) que ocupam diferentes larguras da tela:
- **Seção da esquerda**: 15% da largura da tela, cor **marrom**, e rolagem independente.
- **Seção central**: 55% da largura da tela, cor **azul**, e rolagem independente.
- **Seção da direita**: 30% da largura da tela, cor **vermelha**, e rolagem independente.

Cada seção rola individualmente somente quando o cursor está sobre ela. Para garantir isso:
- Foi usada a propriedade `overflow-y: auto`, que ativa a rolagem interna da seção se o conteúdo for maior que a altura visível.
- O `body` e `html` da página têm a propriedade `overflow: hidden`, para evitar que a página principal role. Isso assegura que apenas as seções individuais rolem quando necessário.

### 3. Remoção das Barras de Rolagem Visíveis
Para melhorar a estética, foi implementada a remoção das barras de rolagem visíveis, mantendo ainda a funcionalidade de rolagem:
- **Para navegadores WebKit (Chrome, Safari)**: A regra `section::-webkit-scrollbar { display: none; }` foi adicionada para esconder as barras de rolagem.
- **Para navegadores Firefox**: Foi usada a propriedade `scrollbar-width: none;` para ocultar as barras de rolagem.

### Código HTML e CSS

```html
<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Página com Layout de Sessões</title>
    <style>
        * {
            margin: 0;
            padding: 0;
            box-sizing: border-box;
        }

        body, html {
            height: 100%;
            font-family: Arial, sans-serif;
            overflow: hidden; /* Evita rolagem na página principal */
        }

        /* Header fixo */
        header {
            position: fixed;
            top: 0;
            left: 0;
            width: 100%;
            height: 60px;
            background-color: purple;
            color: white;
            text-align: center;
            line-height: 60px;
            font-size: 24px;
            z-index: 1000;
        }

        /* Layout das três seções */
        main {
            display: flex;
            height: 100%;
            margin-top: 60px; /* Ajusta o espaço devido ao header */
        }

        section {
            height: calc(100vh - 60px); /* Altura total menos a altura do header */
            overflow-y: auto; /* Rolagem somente na seção */
            scrollbar-width: none; /* Para navegadores Firefox */
        }

        /* Esconde a barra de rolagem para Webkit (Chrome, Safari) */
        section::-webkit-scrollbar {
            display: none;
        }

        /* Seção da esquerda */
        .left {
            width: 15%;
            background-color: brown;
        }

        /* Seção central */
        .center {
            width: 55%;
            background-color: blue;
        }

        /* Seção da direita */
        .right {
            width: 30%;
            background-color: red;
        }

        /* Estilos opcionais para conteúdo */
        p {
            padding: 10px;
            color: white;
        }
    </style>
</head>
<body>
    <header>
        Título
    </header>

    <main>
        <section class="left">
            <p>Conteúdo da seção esquerda.</p>
            <p>Texto de exemplo para a rolagem independente nesta seção. Adicione mais conteúdo para testar a rolagem.</p>
            <p>Mais conteúdo...</p>
            <p>Mais conteúdo...</p>
            <p>Mais conteúdo...</p>
        </section>

        <section class="center">
            <p>Conteúdo da seção central.</p>
            <p>Texto de exemplo para a rolagem independente nesta seção. Adicione mais conteúdo para testar a rolagem.</p>
            <p>Mais conteúdo...</p>
            <p>Mais conteúdo...</p>
            <p>Mais conteúdo...</p>
        </section>

        <section class="right">
            <p>Conteúdo da seção direita.</p>
            <p>Texto de exemplo para a rolagem independente nesta seção. Adicione mais conteúdo para testar a rolagem.</p>
            <p>Mais conteúdo...</p>
            <p>Mais conteúdo...</p>
            <p>Mais conteúdo...</p>
        </section>
    </main>
</body>
</html>
```

## Resumo das Propriedades Importantes
- `position: fixed`: Mantém o header fixo no topo da tela.
- `overflow-y: auto`: Ativa a rolagem dentro de uma seção quando o conteúdo excede a altura.
- `overflow: hidden` no `body`: Desabilita a rolagem geral da página.
- `scrollbar-width: none` e `::-webkit-scrollbar { display: none; }`: Escondem as barras de rolagem visíveis, mantendo a rolagem funcional.
