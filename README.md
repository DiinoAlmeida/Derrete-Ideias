# Derrete Ideias

Catálogo estático de produtos impressos em 3D. Os produtos estão em `products.json` e as fotos em `img/<NomeProduto>/`.

## Standard de imagens

| Regra | Valor |
|---|---|
| Tamanho | **1200×1500 px** (proporção 4:5, vertical) |
| Formato | JPEG, qualidade ~85 |
| Peso | até ~300 KB por imagem |
| Nome | `<NomeProduto><N>.jpeg`, por exemplo `ForestTray1.jpeg` |
| Pasta | `img/<NomeProduto>/` |
| Fundo | liso e claro (branco ou neutro) |
| Enquadramento | objeto centrado, com margem de ~5% à volta |

### Porquê 4:5

As caixas do site (cartão e detalhe) têm proporção 4:5 e usam `object-fit:cover`. Uma imagem 4:5 enche a caixa sem cortes nem faixas. Imagens horizontais ou quase quadradas são cortadas nos lados.

### Adicionar um produto

1. Prepara as fotos em 1200×1500 JPEG.
2. Coloca-as em `img/<NomeProduto>/`.
3. Acrescenta uma entrada em `products.json` com `name`, `category`, `image` (a primeira foto), `images` (todas) e `description`.

### Converter uma imagem (macOS)

Imagem quase quadrada: completar com branco até 4:5 e redimensionar. Ajusta `H` e `W` à imagem de origem, com `H = W × 1,25`:

```sh
sips -s format jpeg -s formatOptions 85 --padToHeightWidth H W --padColor FFFFFF foto.png --out foto.jpeg
sips -z 1500 1200 foto.jpeg
```

Imagem já vertical (por exemplo 3:4): basta `sips -z 1500 1200 foto.jpeg`.

## Servidor local

```sh
python3 -m http.server 8000
```

Abre http://localhost:8000.
