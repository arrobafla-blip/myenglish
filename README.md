# study — English Quest (PWA)

Aplicação web estática para aprender inglês, com identidade visual Y2K scrapbook + videogame, com navy, rosa e laranja.

## O que já funciona
- Dashboard com estatísticas e checklist diário.
- 10 aulas iniciais com explicações, vocabulário, exemplos e exercícios com correção.
- Busca e filtro das aulas.
- Glossário pessoal com adicionar, pesquisar, filtrar e excluir.
- Modo cartões dentro do Glossário: cartões interativos que viram entre inglês e português.
- Quatro atividades diárias: revisão, aula, prática do dia e anotação; cada uma recebe ✓ quando concluída, e o botão principal abre a próxima pendente.
- Prática do dia com seis exercícios alternados entre ditado com voz sintetizada do aparelho e montagem de frases por toque. As frases vêm dos exemplos das aulas e variam diariamente. Respostas erradas viram cartões de revisão.
- Aba Notas com tema sugerido por dia e recursos para criar, editar e excluir anotações.
- Configurações de nome, meta, objetivo, tema claro/escuro e paletas.
- Salvamento local no navegador via localStorage.
- Exportação e importação de backup JSON.
- Manifest, service worker e estrutura PWA para instalação/offline após publicação HTTPS.

## Como abrir localmente
Para uma visualização simples, abra `index.html` no navegador. O curso e o armazenamento local funcionam, mas a instalação PWA e o service worker exigem servir por HTTP/HTTPS.

Para testar como PWA, na pasta do projeto execute um servidor estático local, por exemplo:

```bash
python -m http.server 8000
```

Depois acesse `http://localhost:8000`. Para instalar em um celular, publique os arquivos em uma hospedagem HTTPS compatível.

## Publicação gratuita
Você pode publicar os arquivos em um serviço de hospedagem estática com plano gratuito e HTTPS (por exemplo, GitHub Pages, Cloudflare Pages ou Netlify, conforme os limites vigentes). Os passos dependem da plataforma escolhida.

## Limitações desta primeira versão
- O teste de nivelamento adaptativo ainda não está implementado.
- O cronograma de repetição espaçada ainda é básico; os flashcards funcionam, mas não há agendamento SM-2 completo.
- Não há sincronização automática entre dispositivos; use exportar/importar backup.
- O ditado usa síntese de voz do navegador/aparelho; disponibilidade e vozes variam por dispositivo. Não há biblioteca externa de áudio gravado.
- Ainda não há avaliação automática de pronúncia; a prática oral pode ser feita com leitura em voz alta.
- O modo offline depende da publicação/servidor e do cache inicial. Conteúdos externos não são utilizados.
- Os dados ficam no navegador e podem ser apagados se os dados do site forem limpos. Exporte backups regularmente.

## Como adicionar novas aulas sem reconstruir o site
1. Abra My English e entre em **Configurações → Adicionar novas aulas**.
2. Clique em **Baixar modelo de aula** ou use o arquivo `modelo-de-novas-aulas.json` incluído nesta pasta.
3. Edite o JSON para criar uma ou mais aulas, seguindo a mesma estrutura (`id`, `level`, `title`, `subtitle`, `mins`, `objective`, `explain`, `vocab`, `examples`, `questions`).
4. Salve o arquivo JSON, selecione-o no site e clique em **Importar aulas**.
5. As novas aulas aparecem no curso sem alterar os arquivos do site. As aulas adicionais ficam salvas no armazenamento local do navegador junto do progresso.

Cada aula precisa ter um `id` exclusivo (letras, números, hífen ou underline). Para atualizar uma aula adicional já importada, mantenha o mesmo ID. Assim, o progresso associado àquele ID permanece. Não use IDs das 10 aulas originais (`lesson1` a `lesson10`).

**Importante:** as aulas adicionadas ficam no navegador em que foram importadas. Para usar em outro dispositivo, exporte um backup do My English e importe-o no outro dispositivo. Faça backups regularmente.
