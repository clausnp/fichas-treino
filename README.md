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
- Tocar no número da série marca/desmarca. "Concluir treino" limpa as marcações e avança a fila (A→B→C→D→A).
- Marcações e próximo treino ficam no `localStorage` do navegador (chaves `ficha.*` no Claus, `ana.*` na Ana). Ficam só naquele celular/navegador.
- Campo "Carga (kg)" em cada exercício: salva sozinho ao digitar (borda verde rápida confirma), no `localStorage` (`ficha.cargas` / `ana.cargas`), pelo **nome do exercício**. Não é apagado por "Limpar" nem "Concluir". Renomear um exercício perde a carga salva dele.
- "Ver no YouTube": abre uma busca no YouTube pelo exercício (`YQ` ajusta o termo de busca). Se o navegador bloquear nova aba, abre na mesma.
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
- Trocar de navegador ou limpar dados do site apaga as marcações (só elas; a ficha não).

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

## 11. Como trabalhar
1. Editar `claus.html`/`ana.html` (objeto `T` para os treinos).
2. Testar no navegador do PC.
3. Commit e push na `main`; esperar o Pages publicar.
4. No celular: abrir o link no Chrome/Safari e usar "Adicionar à tela inicial".

## Histórico de ajustes nas fichas
- 19/11/2026, Claus (revisão leve): C troca crucifixo inverso por elevação lateral no cabo (ombro lateral só tinha 3 séries/semana; posterior de ombro já trabalha nas remadas e puxadas); D troca flexor deitado (repetia a mesa flexora do B) por cadeira flexora sentada; regra de progressão no topo.
- 19/11/2026, Ana: pernas (A e C) refeitas — veja "Decisões".
- 19/11/2026, Claus: supino reto e supino inclinado (A e C) na máquina; agachamento na máquina (B); serrote virou remada unilateral na máquina (C); afundo saiu e entrou elevação pélvica (D).
