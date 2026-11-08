# Publicação do site

## Antes de publicar

1. Crie a conta no Mercado Pago (CPF + documento + selfie).
2. Gere um link de pagamento de R$ 37,00 com a descrição "AutomateKit — 5 automações n8n".
3. Substitua o `href="#"` do botão "Comprar agora" em `index.html` pelo link.
4. Confira se `download/automatekit.zip` está presente.

## GitHub Pages

```bash
cd ~/Projects/automatekit/site
git init
git add .
git commit -m "AutomateKit: página de vendas e pacote"
gh repo create automatekit --public --source=. --remote=origin --push
gh api -X POST repos/{owner}/automatekit/pages -f source[branch]=main -f source[path]=/
```

O site fica em `https://<seu-usuario>.github.io/automatekit/`.

## Teste local

```bash
cd ~/Projects/automatekit/site
python3 -m http.server 8765
```

Abra `http://localhost:8765`.

## O que medir

- Visitas na página.
- Cliques no botão de compra.
- Vendas concluídas.
- Origem do tráfego (se usar UTM).

## O que não está incluído

- Entrega automática do arquivo após o pagamento. O comprador é redirecionado para `obrigado.html`, que tem o link do ZIP. Para entrega 100% automática e protegida, seria necessário um checkout com entrega (Kiwify, Payhip ou integração com webhook).
- Controle de acesso ao ZIP. Quem souber a URL consegue baixar.
