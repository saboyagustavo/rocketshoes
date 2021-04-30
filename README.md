# 💻 Sobre o desafio

Nesse desafio o principal objetivo é criar um hook de carrinho de compras, usando ReactJS, em uma aplicação previamente construída com duas páginas, um componente e um hook.

## Funcionalidades pedidas nesse desafio:

- Adicionar um novo produto ao carrinho;
- Remover um produto do carrinho;
- Alterar a quantidade de um produto no carrinho;
- Cálculo dos preços sub-total e total do carrinho;
- Validação de estoque;
- Exibição de mensagens de erro;
- Entre outros.

## Requisitos para o desafio

- Fake API com JSON Server;
- Preservar dados do carrinho com localStorage API;
- Mostrar erros com toastify.

## O que devo editar na aplicação?

Você deve completar onde não possui código com o código para atingir os objetivos de cada teste. Os documentos que devem ser editados são:

- [x] [src/components/Header/index.tsx](https://github.com/saboyagustavo/rocketshoes/blob/main/src/components/Header/index.tsx);
- [x] [src/pages/Home/index.tsx](https://github.com/saboyagustavo/rocketshoes/blob/main/src/pages/Home/index.tsx)
- [x] [src/pages/Cart/index.tsx](https://github.com/saboyagustavo/rocketshoes/blob/main/src/pages/Cart/index.tsx);
- [x] [src/hooks/useCart.tsx](https://github.com/https://github.com/saboyagustavo/rocketshoes/blob/main/src/hooks/useCart.tsx).

### components/Header/index.tsx

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/71a7f217-c1bb-426a-8fcc-dfb65db6bb7a/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/71a7f217-c1bb-426a-8fcc-dfb65db6bb7a/Untitled.png)

- [x] Você deve receber o array `cart` do hook `useCart` e mostrar em tela a quantidade de produtos **distintos** adicionados ao carrinho. Dessa forma, se o carrinho possui 4 unidades do item A e 1 unidade do item B o valor a ser mostrado é `2 itens`.

### pages/Home/index.tsx

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3d320e3c-a052-4f72-994e-aa69617ee85c/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/3d320e3c-a052-4f72-994e-aa69617ee85c/Untitled.png)

- [x] Você deve renderizar os produtos buscados da fake API em tela com as informações de título, imagem, preço e quantidade adicionada ao carrinho. Por fim, é preciso implementar a funcionalidade de adicionar o produto escolhido ao carrinho ao clicar no botão `ADICIONAR AO CARRINHO`.

Nesse arquivo, temos três pontos importantes a serem implementados:

- [x] **cartItemsAmount:** Deve possuir as informações da quantidade de cada produto no carrinho. Sugerimos criar um objeto utilizando `reduce` onde a chave representa o id do produto e o valor a quantidade do produto no carrinho.

- [x] **loadProducts:** Deve buscar os produtos da Fake API e formatar o preço utilizando o helper `utils/format`
- [x] **handleAddProduct:** Deve adicionar o produto escolhido ao carrinho.

### pages/Cart/index.tsx

![https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a34120df-4046-4a84-8133-6eb987bceac6/Untitled.png](https://s3-us-west-2.amazonaws.com/secure.notion-static.com/a34120df-4046-4a84-8133-6eb987bceac6/Untitled.png)

- [x] Você deve renderizar uma tabela com a imagem, título, preço unitário, quantidade de unidades e preço subtotal de cada produto o carrinho. Além disso, também é preciso renderizar o preço total do carrinho. Por fim, é preciso implementar as funcionalidades dos botões de decrementar, incrementar e remover o produto do carinho.

Nesse arquivo, temos cinco pontos importantes a serem implementados:

- [x] **cartFormatted:** Deve formatar o carrinho adicionando os campos `priceFormatted` (preço do produto) e `subTotal` (preço do produto multiplicado pela quantidade) ambos devidamente formatados com o `utils/format`.
- [x] **total:** Deve possuir a informação do valor total do carrinho devidamente formatado com o `utils/format`.
- [x] **handleProductIncrement:** Deve aumentar em 1 unidade a quantidade do produto escolhido ao carrinho.
- [x] **handleProductDecrement:** Deve diminuir em 1 unidade a quantidade do produto escolhido ao carrinho, onde o valor mínimo é 1 (nesse caso o botão deve estar desativado).
- [x] **handleRemoveProduct:** Deve remover o produto escolhido do carrinho.

### hooks/useCart.tsx

- [x] **cart:** Deve verificar se existe algum registro com o valor `@RocketShoes:cart` e retornar esse valor caso existir. Caso contrário, retornar um array vazio.
- [x] **addProduct:** Deve adicionar um produto ao carrinho. 
Porém, é preciso verificar algumas coisas:
    - [x] O valor atualizado do carrinho deve ser perpetuado no **localStorage** utilizando o método `setItem`.
    - [x] Caso o produto já exista no carrinho, não se deve adicionar um novo produto repetido, apenas incrementar em 1 unidade a quantidade;
    - [x] Verificar se existe no estoque a quantidade desejada do produto. Caso contrário, utilizar o método `error` da **react-toastify** com a seguinte mensagem:

    ```jsx
    toast.error('Quantidade solicitada fora de estoque');
    ```

    - [x] Capturar utilizando `trycatch` os erros que ocorrerem ao longo do método e, no catch, utilizar o método `error` da **react-toastify** com a seguinte mensagem:

    ```jsx
    toast.error('Erro na adição do produto');
    ```

- [x] **removeProduct:** Deve remover um produto do carrinho. 
Porém, é preciso verificar algumas coisas:
    - [x] O valor atualizado do carrinho deve ser perpetuado no **localStorage** utilizando o método `setItem`.
    - [x] Capturar utilizando `trycatch` os erros que ocorrerem ao longo do método e, no catch, utilizar o método `error` da **react-toastify** com a seguinte mensagem:

    ```jsx
    toast.error('Erro na remoção do produto');
    ```

- [x] **updateProductAmount:** Deve atualizar a quantidade de um produto no carrinho.
Porém, é preciso verificar algumas coisas:
    - [x] O valor atualizado do carrinho deve ser perpetuado no **localStorage** utilizando o método `setItem`.
    - [x] Se a quantidade do produto for menor ou igual a zero, sair da função **updateProductAmount** instantaneamente.
    - [x] Verificar se existe no estoque a quantidade desejada do produto. Caso contrário, utilizar o método `error` da **react-toastify** com a seguinte mensagem:

    ```jsx
    toast.error('Quantidade solicitada fora de estoque');
    ```

    - [x] Capturar utilizando `trycatch` os erros que ocorrerem ao longo do método e, no catch, utilizar o método `error` da **react-toastify** com a seguinte mensagem:

    ```jsx
    toast.error('Erro na alteração de quantidade do produto');
    ```


<hr>

Feito com 💜 por Rocketseat 👋 Participe da nossa [comunidade aberta!](https://discord.gg/pUU3CG4Z)