Orquídeas+ — Guia para os editores
O Orquídeas+ é um site estático e gratuito de divulgação científica sobre orquídeas e botânica. Seu conteúdo é armazenado em arquivos de texto na pasta dados/, permitindo que os editores atualizem matérias, imagens e outras informações sem precisar modificar diretamente o código do site.

Após o envio das alterações ao repositório, o site pode ser reconstruído e publicado automaticamente pelo GitHub Actions.

1. Publicar o site
Opção A — GitHub Pages (recomendada)
O GitHub Pages permite hospedar gratuitamente o site diretamente a partir de um repositório.

Crie uma conta no GitHub.
Crie um repositório para o projeto, por exemplo, orquideas-mais.
Envie os arquivos do projeto para o repositório, mantendo a estrutura de pastas.
Acesse Settings → Pages.
Em Build and deployment → Source, selecione GitHub Actions.
Confira se o repositório contém o workflow de publicação necessário em .github/workflows/.
Acesse a aba Actions e acompanhe a execução da publicação.
Quando o processo terminar, acesse o endereço disponibilizado pelo GitHub Pages.
O endereço padrão será semelhante a:

https://SEU-USUARIO.github.io/orquideas-mais/

Substitua SEU-USUARIO pelo nome de usuário ou organização responsável pelo repositório.

Importante: selecionar GitHub Actions nas configurações não cria automaticamente um workflow. O repositório precisa conter um arquivo de configuração compatível com a construção e a publicação do site.

Após a configuração inicial, as alterações enviadas ao repositório poderão ser publicadas automaticamente, conforme as regras definidas no workflow.

Opção B — Netlify ou Cloudflare Pages
Também é possível utilizar plataformas gratuitas de hospedagem de sites estáticos.

Em uma configuração compatível com o projeto, os parâmetros de construção são:

Comando de build: python build.py
Diretório de publicação: public
A configuração pode variar conforme a plataforma e as dependências utilizadas pelo projeto.

Opção C — Netlify Drop
Para uma publicação simples, é possível utilizar o Netlify Drop.

Execute a construção do site, se necessário.
Envie a pasta public para a plataforma.
Aguarde a disponibilização do endereço.
Essa opção exige um novo envio dos arquivos gerados sempre que houver alterações no site.

2. Organizar os acessos
O site fica vinculado ao repositório, e não exclusivamente à conta de quem o criou.

Para facilitar a continuidade do projeto:

Mantenha o repositório sob uma conta ou organização institucional, quando possível.
Convide os estudantes e demais editores em Settings → Collaborators.
Conceda apenas as permissões necessárias para cada colaborador.
Registre quem é responsável pela manutenção técnica e pela revisão editorial.
Também é possível transferir o repositório para outra conta ou organização em Settings → General → Danger Zone → Transfer ownership, conforme as permissões disponíveis.

Recomendação: prefira contas individuais com permissões apropriadas, em vez de compartilhar uma única conta e sua senha entre todos os editores.

3. Estrutura do projeto
A estrutura do repositório organiza o conteúdo, os arquivos visuais e os recursos necessários para gerar o site.


Arquivo ou pasta	Função
dados/	Armazena os dados e conteúdos do site.
dados/artigos.json	Contém as matérias publicadas.
dados/config.json	Reúne configurações gerais, links e informações dos autores.
dados/quiz.json	Armazena as perguntas do quiz.
dados/glossario.json	Contém os termos e suas definições.
dados/linha-do-tempo.json	Armazena os eventos da linha do tempo.
imagens/	Reúne as imagens utilizadas no site.
assets/style.css	Define os estilos visuais do site.
build.py	Script responsável pela construção do site.
public/	Contém os arquivos gerados para publicação.
.github/workflows/	Pode conter os fluxos automatizados de construção e publicação.
README.md	Este guia de edição e manutenção.
Importante: edite os arquivos de origem, principalmente os da pasta dados/. Evite modificar manualmente os arquivos gerados em public/, pois as alterações podem ser sobrescritas na próxima construção.

4. Adicionar uma matéria
As matérias são cadastradas no arquivo dados/artigos.json.

Passo a passo
Abra dados/artigos.json no GitHub.
Clique no ícone de lápis para editar o arquivo.
Copie um objeto de matéria existente, incluindo as chaves {}.
Cole o objeto na posição desejada, respeitando a estrutura da lista.
Substitua os valores pelos dados da nova matéria.
Revise a sintaxe do JSON.
Clique em Commit changes para salvar as alterações.
Campos da matéria

Campo	Descrição
slug	Identificador utilizado no endereço da matéria. Use letras minúsculas, números e hífens, sem espaços ou acentos.
titulo	Título da matéria.
categoria	Categoria temática.
emoji	Emoji associado à matéria.
resumo	Texto breve de apresentação.
paragrafos	Lista de parágrafos que compõem o texto.
fato	Curiosidade ou informação de destaque.
fonte	Referência científica, incluindo autores, periódico e link, quando disponíveis.
autor	Nome do responsável pela matéria.
data	Data de publicação no formato AAAA-MM-DD.
leo	Valor booleano: true para exibir em "Pesquisa do LEO" e false para não exibir.
imagem	Nome do arquivo de imagem, quando houver.
credito_imagem	Crédito da imagem, quando aplicável.
Os campos devem seguir o formato esperado pelo código do site. Confira os objetos existentes antes de adicionar uma nova matéria.

Regras importantes do JSON
Utilize aspas duplas nas chaves e nos textos.
Separe os campos com vírgulas.
Não coloque vírgula após o último campo de um objeto.
Não adicione comentários dentro do JSON.
Utilize true e false sem aspas.
Evite slug duplicado.
Preserve os colchetes [] que delimitam a lista de matérias.
Exemplo de matéria

{
  "slug": "exemplo-de-materia",
  "titulo": "Título da matéria",
  "categoria": "Botânica",
  "emoji": "🌱",
  "resumo": "Uma breve apresentação do assunto.",
  "paragrafos": [
    "Primeiro parágrafo da matéria.",
    "Segundo parágrafo da matéria."
  ],
  "fato": "Uma curiosidade científica relacionada ao tema.",
  "fonte": "Autores. Título do estudo. Periódico, ano. DOI ou URL.",
  "autor": "Nome do autor",
  "data": "2026-10-19",
  "leo": false,
  "imagem": "exemplo.jpg",
  "credito_imagem": "Nome do fotógrafo"
}
O exemplo é ilustrativo. Caso a implementação utilize campos adicionais ou obrigatórios, siga o formato das matérias existentes no projeto.

Após salvar as alterações, aguarde a conclusão da construção e da publicação do site.

5. Trocar e adicionar imagens
As imagens utilizadas nas matérias devem ser armazenadas na pasta imagens/.

Passo a passo
Prepare a imagem que será utilizada.
Acesse a pasta imagens/ no GitHub.
Clique em Add file → Upload files.
Envie a imagem.
Abra dados/artigos.json.
No objeto da matéria, informe o nome exato do arquivo no campo imagem.
Preencha o campo credito_imagem, quando aplicável.
Salve as alterações.
Exemplo:


"imagem": "orquidea-exemplo.jpg",
"credito_imagem": "Nome do fotógrafo"
Recomendações
Prefira imagens próprias ou com licença compatível com o uso pretendido.
Informe os créditos exigidos pela licença.
Utilize nomes de arquivos simples, preferencialmente sem espaços ou caracteres especiais.
Otimize as imagens para reduzir o tempo de carregamento.
Como referência, procure manter os arquivos abaixo de 300 KB sempre que a qualidade visual permitir.
Confira se a extensão e o nome do arquivo correspondem exatamente aos valores cadastrados.
Quando uma imagem for informativa, considere também a inclusão de texto alternativo, caso o sistema ofereça suporte a esse recurso.

6. Editar outras seções
Além das matérias, o site contém arquivos específicos para diferentes funcionalidades.


Arquivo	O que pode ser editado
dados/config.json	Nome do projeto, slogan, Instagram, mini-biografias dos autores, endereço do site e configurações da newsletter.
dados/quiz.json	Perguntas, alternativas e demais informações do quiz.
dados/glossario.json	Termos técnicos e respectivas definições.
dados/linha-do-tempo.json	Eventos, datas e descrições da linha do tempo.
assets/style.css	Cores, fontes, espaçamentos, responsividade e outros aspectos visuais.
Antes de adicionar itens aos arquivos JSON, observe a estrutura dos registros existentes e mantenha o mesmo padrão.

Ao editar o CSS, faça pequenas alterações por vez e confira o resultado em telas de diferentes tamanhos.

7. Configurar a newsletter e o RSS
O site pode utilizar um serviço externo para permitir que leitores recebam atualizações por e-mail.

Configurar a newsletter
Crie uma conta em um serviço de newsletter, como Buttondown, MailerLite ou Brevo.
Configure o formulário de inscrição conforme as instruções do serviço.
Obtenha o endereço de envio (action) e o nome do campo de e-mail exigidos pelo formulário.
Abra dados/config.json.
Preencha newsletter_action e newsletter_campo_email com os valores fornecidos pelo serviço.
Teste a inscrição antes de divulgar o formulário.
Os nomes e os formatos dos campos devem corresponder à implementação atual do site e às exigências do serviço escolhido.

Configurar o RSS
O site gera o arquivo feed.xml, que pode ser utilizado por leitores de RSS e por serviços de distribuição de conteúdo.

Abra dados/config.json.
Preencha url_do_site com o endereço público definitivo.
Reconstrua e publique o site.
Verifique se o arquivo feed.xml está acessível no endereço publicado.
Confira se os links das matérias apontam para as páginas corretas.
Alguns serviços de newsletter permitem enviar e-mails automaticamente quando há novas publicações no RSS. Verifique se essa funcionalidade está disponível no plano contratado.

Se o envio automático não estiver disponível, as mensagens poderão precisar ser preparadas e enviadas manualmente.

8. Testar alterações antes de publicar
Sempre que possível, revise as alterações antes de disponibilizá-las ao público.

Checklist de revisão
O arquivo JSON continua válido.
Os campos obrigatórios estão preenchidos.
Não existem identificadores slug duplicados.
Os nomes e caminhos das imagens estão corretos.
As referências científicas e os links foram conferidos.
A ortografia e a formatação foram revisadas.
As páginas e os recursos visuais continuam funcionando.
A publicação foi concluída sem erros.
Testar localmente
Se estiver trabalhando em um computador com Python instalado, abra um terminal na pasta do projeto e execute:


python build.py
Esse comando executa o script de construção do site. Caso existam dependências adicionais, instale-as conforme a documentação do projeto.

Depois da execução, confira se os arquivos esperados foram gerados em public/ e verifique o resultado no ambiente local, se houver um procedimento de pré-visualização configurado.

O comando de construção, sozinho, não garante que o site tenha sido publicado. A publicação depende da configuração de hospedagem.

9. Solução de problemas
O site não atualizou
Acesse a aba Actions do repositório.
Verifique se a execução mais recente terminou com sucesso.
Confira se as alterações foram salvas e enviadas ao repositório.
Aguarde a conclusão da publicação.
Se necessário, atualize o navegador ou verifique se há conteúdo antigo em cache.
Uma matéria não aparece
Confira se a matéria foi adicionada ao arquivo correto.
Verifique se o JSON continua válido.
Confira o slug e procure possíveis duplicatas.
Verifique se os campos seguem o formato esperado pelo site.
Uma imagem não aparece
Confira se o arquivo foi enviado para imagens/.
Verifique a grafia do nome, a extensão e o caminho.
Confirme se o campo imagem corresponde ao arquivo existente.
Verifique se a construção do site está copiando as imagens corretamente.
A publicação falhou
Consulte os registros da execução na aba Actions.
Verifique a configuração do workflow em .github/workflows/.
Confira se o script de construção terminou sem erros.
Revise as permissões e as configurações do GitHub Pages.
O RSS apresenta links incorretos
Confira o valor de url_do_site em dados/config.json.
Reconstrua e publique o site.
Verifique os links gerados no arquivo feed.xml.
Se o problema persistir, registre a mensagem de erro e as alterações realizadas antes de tentar corrigi-lo.

10. Boas práticas editoriais
O Orquídeas+ tem como objetivo divulgar informações sobre orquídeas e botânica de maneira acessível e cientificamente responsável.

Confiabilidade científica
Priorize artigos científicos, periódicos revisados por pares, universidades e instituições de pesquisa reconhecidas.
Sempre que possível, consulte a publicação original em vez de depender exclusivamente de notícias ou textos de divulgação.
Inclua autores, título do estudo, periódico, ano e DOI ou URL, quando disponíveis.
Diferencie resultados de estudos, hipóteses científicas e curiosidades.
Evite afirmações que extrapolem as evidências disponíveis.
Confira nomes científicos, datas e demais informações técnicas.
Clareza e acessibilidade
Escreva para leitores que não necessariamente possuem formação científica.
Explique termos técnicos na primeira ocorrência.
Utilize parágrafos claros e objetivos.
Evite títulos excessivamente longos.
Utilize textos alternativos para imagens informativas quando houver suporte.
Confira se os links possuem descrições compreensíveis.
Direitos autorais
Não copie integralmente textos de artigos, livros ou outros sites sem autorização ou fundamento legal.
Parafraseie as informações com suas próprias palavras e cite as fontes.
Utilize imagens próprias, licenciadas ou de uso permitido.
Respeite as condições de atribuição e reutilização de cada material.
Revisão antes da publicação
Sempre que possível, peça a outra pessoa para revisar a matéria antes de publicá-la. A revisão por pares dentro da equipe ajuda a identificar erros científicos, problemas de escrita e referências incompletas.

11. Contribuições e manutenção
O projeto pode ser mantido por diferentes estudantes e colaboradores ao longo do tempo.

Para facilitar a continuidade:

Mantenha os arquivos organizados e siga os formatos existentes.
Descreva claramente cada alteração ao registrar um commit.
Evite mudanças desnecessárias em arquivos que não estejam relacionados à tarefa.
Sempre que possível, solicite a revisão de outra pessoa antes de publicar alterações importantes.
Utilize pull requests para propor e revisar mudanças quando o fluxo de trabalho do grupo permitir.
Registre decisões importantes sobre a estrutura do site e os procedimentos de publicação.
Não compartilhe senhas, tokens ou credenciais no repositório.
Revise periodicamente os acessos dos colaboradores.
Sugestão de fluxo editorial
O colaborador prepara ou atualiza a matéria.
As referências e o conteúdo são revisados.
Os arquivos são conferidos e as alterações são propostas no GitHub.
A equipe verifica se a construção do site foi concluída sem erros.
Após a aprovação, a alteração é publicada.
Esse fluxo pode ser adaptado à quantidade de editores e às necessidades do projeto.

12. Privacidade e proteção de dados
Caso o site utilize uma newsletter ou outro recurso que colete dados pessoais, a equipe deve considerar as obrigações aplicáveis da Lei Geral de Proteção de Dados Pessoais (LGPD).

Recomendações:

Informe aos leitores quais dados são coletados e para qual finalidade.
Utilize um serviço confiável para gerenciar inscrições e descadastros.
Colete apenas os dados necessários.
Não publique endereços de e-mail ou outras informações pessoais nos arquivos do repositório.
Não armazene senhas, tokens ou credenciais em arquivos públicos.
Confira as políticas e as configurações de privacidade do serviço de newsletter escolhido.
O uso de um serviço externo não elimina a responsabilidade de avaliar as práticas de tratamento de dados adotadas pelo projeto.

13. Créditos e licença
Projeto: Orquídeas+

Objetivo: divulgação científica e educação sobre orquídeas e botânica.

Equipe responsável: [nome do grupo, laboratório ou instituição].

Instituição: [nome da instituição, se aplicável].

Contato: [e-mail institucional ou canal de contato].

Licença
A licença do código e a autorização de reutilização do conteúdo devem ser definidas pela equipe responsável.

Se o projeto utilizar uma licença de código aberto, adicione o arquivo LICENSE ao repositório e informe aqui a licença escolhida.

Textos, fotografias e outros materiais podem ter direitos autorais e condições de reutilização diferentes das aplicáveis ao código. A licença do repositório não deve ser presumida como autorização para reutilizar materiais de terceiros.

Manutenção do guia
Este documento deve ser atualizado sempre que houver mudanças importantes na estrutura do projeto, nos procedimentos de publicação ou nos arquivos utilizados pelos editores.

Última atualização: [AAAA-MM-DD]



