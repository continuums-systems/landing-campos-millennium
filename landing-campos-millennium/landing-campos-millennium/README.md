<div align="center">

# Campos Millennium · Landing Page

**Site institucional para a Campos Millennium — Assessoria Contábil**, Osasco/SP.

[![Deploy](https://img.shields.io/badge/deploy-GitHub%20Pages-2A88C8?style=flat-square)](https://continuums-systems.github.io/landing-campos-millennium/)
![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=flat-square&logo=html5&logoColor=white)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=flat-square&logo=css3&logoColor=white)
![JavaScript](https://img.shields.io/badge/JavaScript-vanilla-F7DF1E?style=flat-square&logo=javascript&logoColor=black)
![No build step](https://img.shields.io/badge/build%20step-none-success?style=flat-square)

[**🔗 Ver site no ar**](https://continuums-systems.github.io/landing-campos-millennium/) · [Reportar problema](../../issues)

</div>

---

## Sobre o projeto

Landing page de conversão construída a partir do site institucional original
([contabilidadecampos.com.br](https://contabilidadecampos.com.br/)), condensando
13 serviços contábeis numa página única orientada a captar contato via WhatsApp.

Direção de design: nada de template genérico de IA — paleta ancorada nos azuis
reais da marca, tipografia serifada (eco do logo), estrutura em seções numeradas
inspirada na lógica de um relatório contábil, e o motivo da esfera do logo
reaproveitado como elemento visual recorrente.

| | |
|---|---|
| **Stack** | HTML5 + CSS3 + JavaScript vanilla — zero dependências, zero build |
| **Arquivo único** | Todo o CSS, JS e as imagens (Base64) vivem dentro do `index.html` |
| **Deploy** | GitHub Pages, manual ou via GitHub Actions |
| **Performance** | ~170KB totais, sem requisições externas além das fontes do Google Fonts |

---

## Estrutura do repositório

```
landing-campos-millennium/
├── index.html                  # página inteira — HTML, CSS, JS e imagens embutidas
├── .github/
│   └── workflows/
│       └── deploy.yml          # deploy automático via GitHub Actions (opcional)
├── .nojekyll                   # impede o GitHub de processar o site como Jekyll
├── .gitignore
└── README.md
```

> **Por que arquivo único?** Para uma landing page de uma seção só, manter tudo
> em `index.html` elimina qualquer dependência de caminho relativo — o arquivo
> funciona idêntico se aberto direto no navegador, hospedado em qualquer pasta,
> ou movido de lugar. O custo é que trocar uma imagem exige regenerar o Base64
> dela (veja [Customização](#customização)).

---

## Como rodar localmente

Não precisa de servidor, Node, nem instalação de nada:

```bash
git clone https://github.com/continuums-systems/landing-campos-millennium.git
cd landing-campos-millennium
open index.html        # macOS
# ou: xdg-open index.html   (Linux)
# ou simplesmente dê duplo clique no arquivo
```

---

## Deploy no GitHub Pages

### Opção recomendada — Deploy from a branch

1. Faça push deste repositório para o GitHub (branch `main`).
2. **Settings → Pages → Build and deployment → Source** → `Deploy from a branch`.
3. Branch `main`, pasta `/ (root)` → **Save**.
4. Em ~1 minuto o site sobe em:
   `https://<seu-usuário-ou-org>.github.io/<nome-do-repo>/`

A cada `git push` na `main`, o Pages republica automaticamente.

### Alternativa — GitHub Actions

Este repo já inclui `.github/workflows/deploy.yml`. Para usá-lo, em
**Settings → Pages → Source**, escolha `GitHub Actions` em vez de `Deploy from a branch`.
Use **uma das duas opções**, nunca as duas ao mesmo tempo.

---

## Customização

| O que mudar | Onde |
|---|---|
| Telefone / WhatsApp | buscar por `wa.me` e `tel:` no `index.html` |
| E-mail | buscar por `mailto:` |
| Endereço | buscar por `maps.app.goo.gl` |
| Cores da marca | variáveis `--ink`, `--navy`, `--blue`, `--cyan` no `:root` do `<style>` |
| Textos das seções | diretamente no HTML — cada seção é comentada (`<!-- HERO -->`, `<!-- SERVICES INDEX -->` etc.) |
| Fotos | veja abaixo |

**Trocando uma foto:** as imagens estão embutidas como `data:image/webp;base64,...`.
Para substituir:

```bash
# gera o Base64 de uma nova imagem já otimizada em WebP
python3 -c "
import base64
print('data:image/webp;base64,' + base64.b64encode(open('nova-foto.webp','rb').read()).decode())
"
```

Copie a saída e substitua a string `data:image/webp;base64,...` correspondente
no `index.html`. Se a substituição de fotos for frequente, considere migrar para
imagens em arquivos separados (`img/`) com caminhos relativos — mais prático
para manutenção, ao custo de depender da pasta estar sempre junto do HTML.

---

## Roadmap / próximos passos

- [ ] Substituir fotos de stock por fotos reais da equipe e do escritório
- [ ] Adicionar depoimentos / prova social verificável
- [ ] Formulário de contato com captura real de lead (hoje abre o WhatsApp)
- [ ] Favicon e Open Graph image para compartilhamento em redes sociais

---

<div align="center">

Desenvolvido por **[Continuums Systems](https://github.com/continuums-systems)**

</div>
