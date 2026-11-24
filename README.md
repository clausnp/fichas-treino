# Fichas de Treino

## 0. Visão geral
Fichas de treino (Claus e Ana) para abrir no celular durante o treino. Páginas HTML estáticas, sem servidor nem banco, publicadas pelo **GitHub Pages** deste repositório.

- Link: `https://clausnp.github.io/fichas-treino/` (índice) → `claus.html` e `ana.html`
- Pasta local: `D:\laragon\www\claus_fichas-treino`

## 1. Estrutura
- `index.html`: tela inicial com um cartão por pessoa, mostrando o próximo treino da fila (lê `ficha.proximo` / `ana.proximo` do `localStorage`). Os nomes dos treinos ficam repetidos no objeto `FICHAS` dela: **ao renomear um treino numa ficha, atualizar aqui também**
- `claus.html`, `ana.html`: uma ficha cada (HTML, CSS e JS num arquivo só)

## 2. Como a ficha funciona
- Abas A, B, C, D no topo; cada treino tem a lista de exercícios em cartões (grupos musculares, séries × reps, observações).
- Bi-set/tri-set: exercícios com o mesmo prefixo em `bi` ("Dupla 1", "Trio 2"…) aparecem agrupados.
- Tocar no número da série marca ela **e as anteriores** (tocar na última fecha o exercício todo); tocar numa marcada desmarca ela e as seguintes. "Concluir treino" grava o treino no histórico, limpa as marcações e avança a fila (A→B→C→D→A).
- Marcações e próximo treino ficam no `localStorage` do navegador (chaves `ficha.*` no Claus, `ana.*` na Ana). Ficam só naquele celular/navegador.
- Campo "Carga (kg)" em cada exercício: salva sozinho ao digitar (borda verde rápida confirma), no `localStorage` (`ficha.cargas` / `ana.cargas`), pelo **nome do exercício**. Não é apagado por "Limpar" nem "Concluir". Renomear um exercício perde a carga salva dele.
- "Ver no YouTube": link comum (sem `target="_blank"` nem `window.open`) para uma busca no YouTube pelo exercício (`YQ` ajusta o termo de busca). Assim o celular passa direto para o app do YouTube; com nova aba ficava uma aba em branco aberta antes.
- **Histórico** (bloco no fim da ficha):
  - Ficha em uso: constante `FICHA` (`versao`, `inicio`, `trocaSem` = janela de troca em semanas, hoje 8 a 12). Mostra a semana atual, quantos treinos foram feitos nesta ficha e quando trocar; passou da 8ª semana, o aviso fica laranja.
  - Fichas anteriores: array `ANTERIORES` (`versao`, `inicio`, `fim`, `resumo`). A lista completa de exercícios de cada ficha antiga fica na seção "Histórico de fichas" deste README.
  - Treinos concluídos: cada "Concluir treino" grava `{d: data, t: treino, f: versão da ficha, s: séries feitas, tot: total, c: cargas do dia}` em `ficha.historico` / `ana.historico` (`localStorage`). Mostra os últimos 40, tocando abre as cargas daquele dia.
- Os treinos ficam no objeto `T` dentro do `<script>` de cada ficha. Para mudar a ficha, editar ali.

## 3. Rotas/permissões
Não há. Site público estático; páginas com `noindex` para não aparecer no Google.

## 4. Deploy
Push na `main` publica sozinho pelo GitHub Pages (raiz do repositório), em 1 ou 2 minutos.

## 5. Serviços externos
- Google Fonts (Barlow Condensed, Inter)
- YouTube (só link de busca)

## 6. Front-end
HTML/CSS/JS puro, sem build. Tema claro/escuro segue o celular.

## 7. Testes
Abrir os arquivos no navegador do PC (modo celular do DevTools) e conferir abas, marcação de séries, concluir treino e o botão do YouTube.

## 8. Gotchas
- **Não mandar o .html pelo WhatsApp**: o visualizador interno do WhatsApp não abre links externos (YouTube não funciona) nem deixa passar para o navegador. Mandar sempre o **link**.
- Repositório público (Pages grátis exige): não colocar dados pessoais sensíveis aqui.
- Trocar de navegador ou limpar dados do site apaga marcações, cargas e o histórico de treinos concluídos (a ficha e o histórico de fichas, que estão no código, não).

## 9. Configuração
Não há `.env`.

## 10. Decisões
- GitHub Pages pessoal em vez de servidor da Voope: projeto pessoal, fora da empresa.
- Um arquivo por pessoa, autocontido, para ser fácil de copiar e editar.
- Ficha da Ana (foco glúteo), revisada em 19/11/2026 com base em estudos:
  - Glúteo 2×/semana com variações diferentes em cada dia (nada repetido igual): agachamento fundo e leg press pés altos (glúteo alongado), elevação pélvica (glúteo contraído), búlgaro e stiff (alongado), abdutora e coice (glúteo médio/acessório).
  - Agachamento fundo cresce mais glúteo e adutores que o raso (Kubo 2019); elevação pélvica e agachamento crescem glúteo parecido (Plotkin 2023), por isso entram os dois.
  - Flexora sentada no lugar da deitada: mais crescimento do posterior (Maeo 2021, músculo trabalhando alongado).
  - Cadeira adutora no C em vez de repetir a abdutora do A.
  - Rosca inclinada (bíceps alongado) no lugar da alternada; regra de progressão no topo da ficha (1-2 reps sobrando, bateu o topo das reps → sobe carga).

- Histórico de treinos no próprio celular (sem servidor): o projeto é estático e público, e cada um usa a sua ficha no seu celular.
- Troca de ficha a cada 8 a 12 semanas: tempo para progredir carga nos mesmos exercícios antes de variar.

## 11. Como trabalhar
1. Editar `claus.html`/`ana.html` (objeto `T` para os treinos).
2. Testar no navegador do PC.
3. Commit e push na `main`; esperar o Pages publicar.
4. No celular: abrir o link no Chrome/Safari e usar "Adicionar à tela inicial".

### Ao trocar a ficha (a cada 8 a 12 semanas)
1. Na ficha (`claus.html`/`ana.html`): copiar `FICHA` para dentro de `ANTERIORES` com `fim` (data da troca) e `resumo` (uma linha do que era), subir `FICHA.versao` e pôr o novo `inicio`.
2. Editar o objeto `T` com os treinos novos (e os nomes no `index.html`, se mudarem).
3. Aqui no README: fechar a ficha antiga em "Histórico de fichas" (data de fim) e abrir a nova com a lista completa de exercícios e o porquê das mudanças.
4. O histórico de treinos concluídos continua (cada registro guarda a versão da ficha).

## Histórico de fichas

### Claus
- **Ficha 1** · desde 19/11/2026 · troca prevista entre 14/01/2027 e 11/02/2027
  - **A · Superior · pesado**: Supino reto máquina 3×6-8; Puxada frontal aberta pronada 3×8-10; Supino inclinado máquina 3×8-10; Remada curvada pronada 3×8-10; Elevação lateral 3×10-12; Rosca direta W 3×10-12; Tríceps corda 3×10-12
  - **B · Inferior · quadríceps**: Agachamento na máquina 3×6-8; Leg press 45° 3×10-12; Cadeira extensora 3×10-12; Mesa flexora 3×10-12; Panturrilha em pé 3×10-12; Abdominal infra 3×12-15
  - **C · Superior · volume**: Puxada triângulo 3×10-12; Supino inclinado máquina 3×10-12; Remada unilateral na máquina 3×10-12; Crossover / crucifixo no cabo 3×10-12; Elevação lateral no cabo 3×12-15; Rosca martelo 3×10-12; Tríceps francês na corda 3×10-12
  - **D · Inferior · posterior**: Stiff 3×8-10; Elevação pélvica 3×8-10; Cadeira flexora sentada 3×10-12; Cadeira abdutora 3×10-12; Panturrilha sentada 3×10-12; Abdominal remador 3×12-15

### Ana
- **Ficha 1** · desde 19/11/2026 · troca prevista entre 14/01/2027 e 11/02/2027
  - **A · Inferior · glúteo e quadríceps**: Agachamento Smith profundo 3×8-10; Elevação pélvica 4×8-12; Leg press 45° pés altos 3×10-12; Cadeira abdutora 3×15-20; Cadeira extensora 3×12-15; Abdominal infra 3×12-15
  - **B · Superior · costas e ombro**: Puxada frontal aberta 3×10-12; Supino inclinado halter 3×10-12; Remada baixa triângulo 3×10-12; Desenvolvimento halter 3×10-12; Elevação lateral 3×12-15; Rosca inclinada halter 3×10-12; Tríceps corda 3×10-12
  - **C · Inferior · glúteo e posterior**: Stiff 3×8-10; Agachamento búlgaro 3×8-10; Cadeira flexora sentada 3×10-12; Glúteo no cabo (coice) 3×12-15; Cadeira adutora 3×12-15; Panturrilha em pé 3×12-15
  - **D · Superior · costas e abdômen**: Puxada triângulo 3×10-12; Supino máquina 3×10-12; Serrote 3×10-12; Crucifixo inverso 3×12-15; Tríceps francês na corda 3×10-12; Prancha 3×30-40s; Abdominal remador 3×12-15

## Histórico de ajustes nas fichas
- 24/11/2026, app: botão do YouTube sem aba nova; tocar na última série marca todas; bloco "Histórico" (ficha em uso, troca prevista, fichas anteriores, treinos concluídos com cargas).
- 19/11/2026, Claus (revisão leve): C troca crucifixo inverso por elevação lateral no cabo (ombro lateral só tinha 3 séries/semana; posterior de ombro já trabalha nas remadas e puxadas); D troca flexor deitado (repetia a mesa flexora do B) por cadeira flexora sentada; regra de progressão no topo.
- 19/11/2026, Ana: pernas (A e C) refeitas — veja "Decisões".
- 19/11/2026, Claus: supino reto e supino inclinado (A e C) na máquina; agachamento na máquina (B); serrote virou remada unilateral na máquina (C); afundo saiu e entrou elevação pélvica (D).
