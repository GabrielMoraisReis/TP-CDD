# Ensino Superior no Brasil
Alunos: Gabriel Morais (3497), Arthur Sales (3501), Mateus Coelho(3488)

O tema escolhido pelo grupo foi o ensino superior no Brasil no ano 2019. Os dados utilizados são os da tabela Microdados Censo da Educação Superior 2019 disponível em: https://download.inep.gov.br/microdados/microdados_educacao_superior_2019.zip

## Perguntas
1. Quantos homens e quantas mulheres cada área possui?
1. Qual a distribuição de alunos matriculados por faixa etária?
1. Qual a distribuição de docentes em exercício por faixa etária?
1. Quantos campus ofertam determinado curso? (Aqui o pensamento é o usuário entrar com o nome do curso que deseja)
1. QuaL a relação entre o índice de desistência e idade para os 3 cursos de maior nivel de desistência? 
1. Qual o grau de formação mais comum dos docentes? Comparação entre IES particulares e públicas.
1. Quantos candidatos se candidatam para uma vaga em IES em cada Estado do pais?
1. Há algum aluno que repete na tabela(fazendo dois cursos por exemplo)? Se sim, qual o máximo de repetições, e quantos alunos repetem?
1. Qual o curso com maior desvio padrão em relação às idades dos matriculados? 
1. Qual curso tem a idade média mais baixa? E a mais alta?
1. Qual a probabilidade de um aluno matriculado em curso da área de computação ter algum tipo de deficiência e não desistir do curso? Compare com a probabilidade disso ocorrer no curso com menor índice de desistência.
1. Dado um número x de cursos ofertados em uma IES, essa IES se encontra em uma capital?
1. Qual o curso com mais alunos que fazem projeto de extensão? Ponderado de acordo com número de alunos no curso e número de IES que ofertam o curso
1. Qual a distribuição das cores dos candidatos por meio de ingresso na instituição?
1. Comparação da relação entre estudantes branco x não brancos nas instituições públicas e privadas
1. Qual a concentração de docentes por região? A concentração em capitais é, proporcionalmente, maior?
1. Qual o top 5 cursos mais concorridos? Em quais faculdades a concorrência por esses cursos é maior?
1. Qual a relação de matrículas de alunos portadores de necessidades especiais por subarea?
1. Qual a relação do número de concluintes de cursos de graduação presencial x à distância, por região?
1. Dado um conjunto de características de um indivíduo, qual área é a mais provável desse indivíduo pertencer?

## Tratamento de Dados

Para realizarmos o tratamento de dados, inicialmente realizamos um tratamento inicial, pois o tamanho total dos datasets excedia o limite suportado pelas memórias RAMs dos nossos computadores quando os carregávamos. Neste tratamento inicial derrubamos todas as colunas que não iríamos utilizar para responder às perguntas definidas na parte anterior do trabalho e, também, executamos o comando drop_duplicates em todos datasets, para excluir potenciais linhas duplicadas nos dados. Com isso, conseguimos reduzir consideravelmente o tamanho dos dados e, para conseguir carregá-los de maneira mais eficiente posteriormente, geramos novos arquivos csv com esses tratamentos aplicados.

As colunas que foram retiradas de cada base de dados podem ser encontradas nos arquivos “drop.txt”, que estão na branch main, na pasta “RawToStaged”, a qual também contêm os códigos executados para esse tratamento inicial. É possível encontrar também as colunas que serão utilizadas, ou seja, todas as colunas de uma determinada tabela menos as colunas que foram removidas, nos arquivos “used.txt”, na pasta “UsedColumns”. Após a transformação inicial analisamos as linhas e colunas restantes que poderiam nos causar problemas e, então, utilizamos os códigos encontrados na pasta “StagedToCurated” para realizar um drop nessas linhas, para evitar fazermos um estudo com dados que poderiam gerar ruídos na análise. Para todas as tabelas dropamos todas as linhas que correspondiam a um ano anterior a 2011, pois há algumas colunas com valores nulos para objetos criados antes de 2011 que causariam problemas nas nossas análises.

Para a tabela de alunos, retiramos também as linhas nas quais as informações referentes à cor de pele e deficiência do aluno não estavam presentes, ou que estivessem presentes, mas como “aluno não quis declarar”, também foram removidas as linhas referentes a alunos já falecidos. Na tabela de cursos, as linhas com tipo de grau acadêmico vazio foram removidas, pois indicam cursos com nível acadêmico sequencial ou de formação específica, portanto não são interessantes para a nossa análise. Para a tabela de docentes, excluímos as linhas referentes a docentes falecidos.

<p align="center">
  Comparativo do Tamanho das Tabela Antes e Após os Tratamentos
  
![image](https://user-images.githubusercontent.com/49825001/133352002-4768c6b1-c8b3-41aa-9c4c-944dad604515.png)
  </p>
