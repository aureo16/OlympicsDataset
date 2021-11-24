# Projeto "Olympics Dataset"

# Equipe "Liga Olímpica" - AJJLO
* Áureo Henrique e Silva Marques - 213374
* José Alexandre dos Santos Barros - 176566
* Lindon Jonathan Sanley dos Santos Pereira Monroe - 220407

## Resumo do Projeto
Este projeto tem como objetivo a construção de um banco de dados cujo tema é o histórico dos Jogos Olímpicos nos últimos anos.

Os Jogos Olímpicos, ou Olimpíadas, são o maior evento esportivo do mundo e, de 4 em 4 anos, reúnem milhares de atletas de vários países. Embora suas origens sejam da Grécia Antiga, as primeiras Olimpíadas ocorreram oficialmente em 1896, organizadas pelo Comitê Olímpico Internacional (COI) e, portanto, desse ano até hoje, tratam-se de mais de 30 edições dos jogos olímpicos.

Essa grande quantidade de jogos resulta em uma grande quantidade de informações sobre os atletas, os países participantes, os países sede, as medalhas, os esportes, os vencedores de cada modalidade, entre outros. No entanto, encontrar um banco de dados com todas essas informações de forma centralizada e bem organizada é difícil, pois os dados disponíveis hoje na internet, em geral, são bancos de dados de algum ano específico das Olimpíadas ou bancos que abordam sobre várias Olimpíadas, mas que não possuem um modelo lógico bem estruturado, dificultando certos tipos de análise.

Com isso, o objetivo desse projeto é, através dos diversos bancos de dados existentes e através de pesquisas na internet, construir um dataset sobre os Jogos Olímpicos dos últimos anos que seja organizado e bem estruturado, permitindo diversos tipos de análises sobre o tema. Devido a possíveis limitações relacionadas ao grande número de edições dos Jogos, ainda vamos decidir exatamente quantos anos o dataset irá abordar, mas, inicialmente, pensamos em reunir os dados de, pelo menos, todos os jogos realizados no século XXI.


## Modelo Conceitual

![ER jogos olimpicos](assets/Modelo_Conceitual.png)

## Modelos Lógicos

~~~
EdicaoDosJogos (_Ano_, NumeroDaEdicao, CidadeSede, TotalDeAtletas, Mascote)

Atleta (_Id_, Nome, AnoDeNascimento, Sexo)

ComiteOlimpico(_Sigla_, País)

EsporteModalidade(_Id_, Nome, EsportePai)

ParticipacaoComites(_IdComite_, _AnoEdicao_,  QtdAtletas, QtdOuro , QtdPrata , QtdBronze, Classificacao)
  IdComite chave estrangeira -> ComiteOlimpico(Sigla)
  AnoEdicao chave estrangeira -> EdicaoDosJogos(Ano)

ParticipacaoAtletas(_IdAtleta_, _AnoEdicao_, _IdModalidade_, Altura, Peso, Medalha)
  IdAtleta chave estrangeira -> Atleta(Id) 
  AnoEdicao chave estrangeira -> EdicaoDosJogos(Ano)
  IdModalidade chave estrangeira -> EsporteModalidade(Id)

ComiteDosAtletas(_IdComite_,_IdAtleta_)
  IdComite chave estrangeira -> ComiteOlimpico(Sigla) 
  IdAtleta chave estrangeira -> Atleta(Id)

EsportesDasEdicoes(_AnoEdicao_, _IdModalidade_, Ouro, Prata, Bronze)
  AnoEdicao chave estrangeira -> EdicaoDosJogos(Ano)
  IdModalidade chave estrangeira -> EsporteModalidade(Id)
~~~

## Dataset Publicado

título do arquivo/base | link | breve descrição
----- | ----- | -----
Edicoes | [edicoes.csv](./data/processed/edicoes.csv) | Arquivo csv contendo tabela EdicaoDosJogos referente ao modelo lógico relacional
Atletas | [atletas.csv](./data/processed/atletas.csv) | Arquivo csv contendo tabela Atleta referente ao modelo lógico relacional
Comites | [comites.csv](./data/processed/comites.csv) | Arquivo csv contendo tabela ComiteOlimpico referente ao modelo lógico relacional
EsporteModalidade | [esportes.csv](./data/processed/esportes.csv) | Arquivo csv contendo tabela EsporteModalidade referente ao modelo lógico relacional
ParticipacaoComites | [participacaoComites.csv](./data/processed/participacaoComites.csv) | Arquivo csv contendo tabela ParticipacaoComites referente ao modelo lógico relacional
ParticipacaoAtletas | [participacaoAtletas.csv](./data/processed/participacaoAtletas.csv) | Arquivo csv contendo tabela ParticipacaoAtletas referente ao modelo lógico relacional
ComiteDosAtletas | [comiteDosAtletas.csv](./data/processed/comiteDosAtletas.csv) | Arquivo csv contendo tabela ComiteDosAtletas referente ao modelo lógico relacional
EsportesDasEdicoes | [esportesDasEdicoes.csv](./data/processed/esportesDasEdicoes.csv) | Arquivo csv contendo tabela EsportesDasEdicoes referente ao modelo lógico relacional
Edicoes-Tokyo | [edicoes-Tokyo.csv](./data/processed/edicoes-Tokyo.csv) | Arquivo csv contendo tabela EdicaoDosJogos referente ao modelo lógico relacional. Dados exclusivos da Olimpíada de Tokyo
Atletas-Tokyo | [atletas-Tokyo.csv](./data/processed/atletas-Tokyo.csv) | Arquivo csv contendo tabela Atleta referente ao modelo lógico relacional. Dados exclusivos da Olimpíada de Tokyo
Comites-Tokyo | [comites-Tokyo.csv](./data/processed/comites-Tokyo.csv) | Arquivo csv contendo tabela ComiteOlimpico referente ao modelo lógico relacional. Dados exclusivos da Olimpíada de Tokyo
EsporteModalidade-Tokyo | [esporteModalidade-Tokyo.csv](./data/processed/esporteModalidade-Tokyo.csv) | Arquivo csv contendo tabela EsporteModalidade referente ao modelo lógico relacional. Dados exclusivos da Olimpíada de Tokyo
ParticipacaoComites-Tokyo | [participacaoComites-Tokyo.csv](./data/processed/participacaoComites-Tokyo.csv) | Arquivo csv contendo tabela ParticipacaoComites referente ao modelo lógico relacional. Dados exclusivos da Olimpíada de Tokyo
ParticipacaoAtletas-Tokyo | [participacaoAtletas-Tokyo.csv](./data/processed/participacaoAtletas-Tokyo.csv) | Arquivo csv contendo tabela ParticipacaoAtletas referente ao modelo lógico relacional. Dados exclusivos da Olimpíada de Tokyo
ComiteDosAtletas-Tokyo | [comiteDosAtletas-Tokyo.csv](./data/processed/comiteDosAtletas-Tokyo.csv) | Arquivo csv contendo tabela ComiteDosAtletas referente ao modelo lógico relacional. Dados exclusivos da Olimpíada de Tokyo
EsportesDasEdicoes-Tokyo | [esportesDasEdicoes-Tokyo.csv](./data/processed/esportesDasEdicoes-Tokyo.csv) | Arquivo csv contendo tabela EsportesDasEdicoes referente ao modelo lógico relacional. Dados exclusivos da Olimpíada de Tokyo
Olimpiadas | [olimpiadas.json](./data/processed/olimpiadas.json) | Arquivo json contendo dados referentes ao modelo lógico hierárquico
OlimpiadasTokyo | [olimpiadasTokyo.json](./data/processed/olimpiadasTokyo.json) | Arquivo json contendo dados referentes ao modelo lógico hierárquico. Dados exclusivos da Olimpíada de Tokyo


## Bases de Dados

título da base | link | breve descrição
----- | ----- | -----
120 years of Olympic history: athletes and results | [Link](https://www.kaggle.com/heesoo37/120-years-of-olympic-history-athletes-and-results/discussion/69221) | Dataset histórico, uma tabela com dados das olimpíadas de 1896 a 2016
2021 Olympics in Tokyo | [Link](https://www.kaggle.com/arjunprasadsarkhel/2021-olympics-in-tokyo) |Dataset que consiste em uma tabela com dados específicos das olimpíadas de Tóquio em 2021. 
Olympics.com | [Link](https://olympics.com) |Site oficial do Comitê Olímpico Internacional (IOC) contendo uma base extensa de dados, notícias e informações sobre os Jogos Olímpicos e seus envolvidos, em geral.

## Perguntas/Análise com Resposta Implementada

### Pergunta/Análise 1

* Para um determinado esporte, existe algum país que constantemente é medalha de ouro?
 SELECT E.Ouro, COUNT(*) QtdOuro 
   FROM EsportesDasEdicoes E, EsporteModalidadeM
     WHERE M.Id=E.IdModalidade AND M.Nome='Athletics''s 100 meters'
     GROUP BY E.Ouro; 

### Pergunta/Análise 2

* Existe alguma relação entre altura do atleta e esporte praticado por ele? E em relação ao peso?
  A análise mostra que jogadores de basquete tendem a ser mais altos, enquanto que atletas de ginástica tendem a ser mais baixos. Calcula-se a média geral e depois as   médias da modalidade
  SELECT AnoEdicao, ROUND(AVG(CAST(Altura as float)),1) Media_altura 
    FROM ParticipacaoAtltetas
      WHERE AnoEdicao=2016 AND Altura <> '-'
      GROUP BY AnoEdicao;
      
    SELECT *
      FROM (
            SELECT E.EsportePai, E. EsporteNome,ROUND(AVG(CAST(Altura as float)),1) Media_altura
             FROM ParticipacaoAtletas P, EsporteModalidade E
              WHERE P.IdModalidade=E.Id AND AnoEdico=2016 AND Altura<> '-'
              GROUP BY IdModalidade
              ORDER BY MEDIA_ALTURA Desc
    
### Pergunta/Análise 3

* Qual a média de idade dos atletas nas primeiras Olimpíadas? E nas últimas?
  As médias permanecem relativamente as mesmas.
  CREATE VIEW Idade as SELECT P.IdAtleta, P.AnoEdicao, (P.AnoEdicao-cast( A.AnoDeNascimento as float) AS idade
    FROM Atleta A, ParticipacaoAtletas P
    WHERE A.Id=P.IdAtleta AND A.AnoDeNascimento <> '-';
    
    SELECT AnoEdicao, ROUND(AVG(idade),0) Media_Idade
      FROM Idade
      GROUP BY AnoEdicao
      ORDER BY AnoEdicao
      
 ### Pergunta/Análise 4
 
 * No período da Guerra Fria, é possível ver o predomínio das duas grandes potências nos pódios das Olímpiadas?
   EUA e URSS estão constantemente na liderança
   
   SELECT AnoEdicao, IdComite,Classificacao
    FROM ParticipacaoComites
      WHERE(IdComite='USA' OR IdComite='URS') AND AnoEdicao>1947 AND AnoEdicao<1989
      
 ### Pergunta/Análise 5
 
 * Qual a proporção de atletas do sexo masculino e do sexo feminino participando nos Jogos Olímpicos?
   SELECT P.ANOEDICAO,A.SEXO,, COUNT (*) TOTAL
    FROM ATLETA A,PARTICIPACAOATELTAS P
     WHERE A.ID=P.IDATLETA
     GROUP BY P.ANOEDICAO, A.SEXO
     ORDER BY P.ANOEDICAO

## Perguntas/Análise propostas mas não  implementada

### Pergunta/Análise 1

* Quais os países que mais ganharam medalhas e os países que menos ganharam medalhas em uma determinada Olimpíada?

### Pergunta/Análise 2

* Qual o número médio de medalhas de um país nas Olimpíadas que ele participou?

### Pergunta/Análise 3

* Em quantas Olimpíadas um determinado atleta participou e quantas medalhas ele ganhou?

### Pergunta/Análise 4

* Quais países que mais trazem atletas para os Jogos Olímpicos nas últimas edições?

### Pergunta/Análise 5

* Para um determinado país, há uma tendência de piora ou melhora no desempenho, nas Olimpíadas em que participou?

### Pergunta/Análise 6

* Na Olímpiada de 1936, como foi o desempenho da Alemanha Nazista?




