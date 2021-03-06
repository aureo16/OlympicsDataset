# Projeto "Olympics Dataset"

# Equipe "Liga Olímpica" - AJJLO
* Áureo Henrique e Silva Marques - 213374
* José Alexandre dos Santos Barros - 176566
* Lindon Jonathan Sanley dos Santos Pereira Monroe - 220407

## Resumo do Projeto
Este projeto tem como objetivo a construção de um banco de dados cujo tema é o histórico dos Jogos Olímpicos nos últimos anos.

Os Jogos Olímpicos, ou Olimpíadas, são o maior evento esportivo do mundo e, de 4 em 4 anos, reúnem milhares de atletas de vários países. Embora suas origens sejam da Grécia Antiga, as primeiras Olimpíadas ocorreram oficialmente em 1896, organizadas pelo Comitê Olímpico Internacional (COI) e, portanto, desse ano até hoje, tratam-se de mais de 30 edições dos jogos olímpicos.

Essa grande quantidade de jogos resulta em uma grande quantidade de informações sobre os atletas, os países participantes, os países sede, as medalhas, os esportes, os vencedores de cada modalidade, entre outros. No entanto, encontrar um banco de dados com todas essas informações de forma centralizada e bem organizada é difícil, pois os dados disponíveis hoje na internet, em geral, são bancos de dados de algum ano específico das Olimpíadas ou bancos que abordam sobre várias Olimpíadas, mas que não possuem um modelo lógico bem estruturado, dificultando certos tipos de análise.

Com isso, o objetivo desse projeto é, através dos diversos bancos de dados existentes e através de pesquisas na internet, construir um dataset sobre os Jogos Olímpicos dos últimos anos que seja organizado e bem estruturado, permitindo diversos tipos de análises sobre o tema.

## Slides da Apresentação
[Link para slides](slides/slides.pdf)

## Modelo Conceitual

![ER jogos olimpicos](assets/modeloConceitual.png)

## Modelos Lógicos

### Modelo Relacional

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

### Modelo Hierárquico

![hierarquico](assets/modeloHierarquico.png)

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

## Detalhamento do Projeto

Para criação do dataset, o grupo buscou primeiramente os dados disponíveis e acessíveis sobre o tema, de modo a selecionar os que poderiam servir de fonte e de inspiração para nosso objetivo.
As fontes que mais cumpriram os requisitos, foram dois datasets com arquivos em formato .csv, um contendo informações sobre as Olimpíadas de 1896 a 2016 e outro exclusivamente sobre as Olimpíadas de 2021 em Tokyo, além do site olympics.com, muito completo.
As três fontes estão devidamente elencadas na seção "Bases de dados".

Com essas fontes de dados em mãos, pudemos visualizar melhor o objetivo do dataset, que seria integrar e transformar os dados dessas 3 fontes, de modo a criar um dataset robusto e útil para responder grande parte das questões relacionadas aos Jogos. Os dois arquivos .csv poderiam ser trabalhados como principais fontes para o dataset, e o site olympics.com serviria de fonte para os dados adicionais que fossem necessários.
Com isso, criamos o modelo conceitual, que serviria depois de base para os modelos lógicos, relacional e de documentos.
Para a criação das 8 tabelas que compõem o modelo relacional do nosso dataset, utilizamos o Google Colab para trabalhar com a linguagem python e a biblioteca de manipulação de dados pandas.

Obtendo os dados para manipulação do .csv de 120 anos de Jogos [athlete_events(120anos).csv](./notebooks/athlete_events(120anos).csv):
~~~python
atletas_120 = pd.read_csv('athlete_events.csv')
atletas_120=atletas_120.loc[atletas_120["Season"] != 'Winter']
~~~

Para cada tabela, o padrão de construção seguiu, em geral, os seguintes passos:

1. Seleção das colunas desejadas que estão no dataset fonte;

2. Renomeação adequada das colunas;

3. Criação de novas colunas vazias;

4. Preenchimento de dados nas novas colunas através de combinação de informações de outras colunas ou de outras tabelas;

5. Preenchimento de dados nulos com hífen;

6. Exportação da tabela em formato "csv".

> Todas as operações realizadas para criação dessas tabelas relacionadas aos Jogos de 1896 a 2016, através da **transformação** dos dados do arquivo .csv, podem ser observadas no notebook a seguir:
>[Dataset_120anos.ipynb](./notebooks/Dataset_120anos.ipynb)

Para o banco de dados dos Jogos Olímpicos de Tóquio, foram realizadas operações parecidas com as elencadas acima, para a criação de cada tabela do modelo relacional.
Porém, muitos dados eram disponibilizados com formatações e organização diferentes do arquivo anterior. Haviam até mesmo dados faltantes, como a ano de nascimento. Nesse ponto, utilizamos a técnica de **extração** para obter dados, requisitando-os do site olympics.com, utilizando xpath para identificar os elementos no html.  

Obtendo anos de nascimento dos atletas por **extração**:
~~~python
r = requests.get("https://olympics.com/en/athletes/"+nomeUrl)
tree = html.fromstring(r.content)

details = tree.xpath('//ul[@class="detail__list"]/li/div/text()')
b = details.index("Year of Birth")
year = details[b+1]
atletas.loc[i,"Ano"] = year

tabela_part = tree.xpath('//table[@class="sm-mb6 has-header"]/tbody/tr')
~~~

Os dados obtidos através dessa técnica, podem ser vistos no .csv:
[atletas_idades.csv](./notebooks/atletas_idades.csv)

Obtendo modalidades em que os atletas participaram por **extração**:
~~~python
if nomeOlimp[0] == "Tokyo 2020":
    for tr in tabela_part:
        td = tr.xpath('.//td')
        medalha = td[1].xpath('.//div')[0].text_content().replace('"','').replace("\n","").replace("\r","").replace(" ","")
        modalidade = td[2].text_content()
        esporte = td[3].text_content()
        atletasEsportes.loc[len(atletasEsportes)] = [nomeReal, nomeUrl, esporte, modalidade, medalha]
~~~

Os dados obtidos através dessa técnica, podem ser vistos no arquivo .csv:
[atletasEsportes.csv](./notebooks/atletasEsportes.csv)

Os dados foram então **integrados** aos dos obtidos no arquivo .csv dos Jogos de Tóquio.
Outro dado faltante **tratado** foi o sexo dos atletas, obtido analisando-se o nome das modalidades esportivas das quais participaram.

~~~python
if "Women" in esportesAtleta.loc[j,"Modalidade"]:
    atletas.loc[i,"Sexo"]="F"
    break;
elif "Men" in esportesAtleta.loc[j,"Modalidade"]:
    atletas.loc[i,"Sexo"]="M"
    break;
~~~

Mais um tratamento foi em relação ao nome dos atletas, que aparecia invertido no arquivo original.
~~~python
  atleta = atletas.loc[i]
  nome=atleta.Nome.replace(".","").replace("'"," ")
  nomeSplit = nome.split()

  index = 0
  for j in range(len(nomeSplit)-1,-1,-1):
    if nomeSplit[j].upper() == nomeSplit[j] and j!=len(nomeSplit)-1:
      index = j+1
      break;
  nomeOrd = nomeSplit[index:]+nomeSplit[:index]
  for j in range(len(nomeOrd)):
    nomeOrd[j] = nomeOrd[j].lower()

  nomeReal = " ".join(nomeOrd).title()
  atletas.loc[i,"Nome"] = nomeReal
~~~

> Todas as operações realizadas para criação dessas tabelas em relação às Olimpíadas de Tóquio, através da **transformação** dos dados do arquivo .csv, podem ser observadas no notebook a seguir:
>[Dataset_Tokyo_2021.ipynb](./notebooks/Dataset_Tokyo_2021.ipynb)

Nesse ponto, seria realizada a maior **integração** da criação do dataset, juntando os tabelas criadas a partir da fonte de 120 anos de Olimpíadas e da fonte da edição de Tóquio. Porém, os dados se mostraram de difícil **integração**, e, por se tratar de apenas mais uma edição, além das outras 29 analisadas, acreditamos que seria mais produtivo focar nas análises e no aperfeiçoamento dos dados que obtivemos da fonte de 120 anos. Mas ainda assim, os dados de Tóquio estão disponíveis e foram trabalhosos, apenas não foram integrados.

O último a ser criado foi o modelo hierárquico. Para tal, foram utilizados os 8 arquivos .csv obtidos na criação das 8 tabelas em relação aos jogos de 1896 a 2016, que compõem o modelo relacional.

~~~python
atletas = pd.read_csv("atletas.csv")
edicoes = pd.read_csv("edicoes.csv")
paises = pd.read_csv("comites.csv")
esportesModalidades = pd.read_csv("esportes.csv")
participacaoComites = pd.read_csv("participacaoComites.csv")
participacaoAtletas = pd.read_csv("participacaoAtletas.csv")
comiteDosAtletas = pd.read_csv("comiteDosAtletas.csv")
esportesDasEdicoes = pd.read_csv("esportesDasEdicoes.csv")
~~~

As tabelas foram percorridas e os dados foram inclusos em cada camada do modelo hierárquico, fazendo-se uma **transformação** de dados.
> Todas as operações realizadas para criação do modelo hierárquico podem ser observadas no notebook a seguir:
>[hierarquico.ipynb](./notebooks/hierarquico.ipynb)

## Evolução do Projeto
O projeto se iniciou com os membros do grupo concordando que Jogos Olímpicos seria um tema interessante, lúdico, e que teria grande abundância de dados. 

As três coisas se provaram verdadeiras, porém, a parte da abundância de dados se mostrou contraditória.

Começamos abordando apenas as edições a partir de 2000, dos jogos de verão, por acreditar que seria muito trabalhoso lidar com um volume tão grande de 120 anos de jogos, mas, no decorrer do desenvolvimento do projeto, e com o feedback do professor de que precisávamos fazer perguntas mais elaboradas, resolvemos adicionar todas as edições dos Jogos ao nosso dataset. Assim, pudemos fazer consultas com respostas mais assertivas, abrangentes e com mais possibilidades.

Outro ponto em relação ao volume de dados, é que, apesar de realmente haverem muitos dados sobre as Olimpíadas na internet, como o nosso dataset lida com uma quantidade muito grande de atletas e informações sobre os mesmos, era de se esperar que não conseguiríamos preencher 100% dos campos das tabelas. Isso especialmente em relação à edição de Tóquio. Mesmo **extraindo** dados que necessitávamos direto do site oficial do Comitê Olímpico Internacional, como essa é a edição mais recente, há uma menor disponibilização dos dados. Além disso, outros sites têm estruturas menos amigáveis para **extração** dos dados, o que não tornou esse procedimento tão prático.

Apesar das dificuldades e mudança de rumo em relação aos dados abrangidos, o modelo conceitual do nosso dataset não mudou muito desde sua primeira versão, o que consideramos ser pois já havíamos pensado nele muito bem desde o início, o que facilitou a criação do modelo lógico relacional. O que mudamos no modelo conceitual foi apenas a relação entre um esporte e suas respectivas modalidades.

Consideramos que o projeto evoluiu num ritmo linear, sem muitos altos e baixos, mas que ainda assim foi bastante trabalhoso, exigindo muito tempo de dedicação.

O que tiramos de lição ao desenvolver esse dataset é que tratar e integrar dados é um pouco mais complicado do que parece. Uma simples formatação diferente, ou disponibilização de dados de forma diferente, pode dificultar uma integração. Extrações podem ser difíceis, devido à forma como os sites disponibilizam os dados, e também demoradas. O tratamento para otimizar as consultas e utilidade dos dados pode não ser trivial, necessitando uma boa modelagem conceitual e lógica para atingir um bom resultado.

## Perguntas de Pesquisa/Análise Combinadas e Respectivas Análises

### Perguntas/Análise com Resposta Implementada

#### Pergunta/Análise 1

* Para um determinado esporte, existe algum país que constantemente é medalha de ouro?

  * **Uso do modelo relacional**

  * Para essa análise, serão selecionados os comites ganhadores de medalha de ouro para uma determinada modalidade, em todas as olimpíadas, e agrupados pelo próprio comite, de forma a contar quantas medalhas de ouro cada um teve.

  * Query SQL:

    ~~~sql
    SELECT E.Ouro, COUNT(*) QtdOuro 
      FROM EsportesDasEdicoes E, EsporteModalidade M
        WHERE M.Id=E.IdModalidade AND M.Nome='Athletics''s 100 meters'
        GROUP BY E.Ouro; 
    ~~~

  * Resultado:

    ![pergunta1resultado](assets/pergunta1resultado.png)

    Vemos que os Estados Unidos é o país com mais medalhas de ouro para a modalidade de 100m no atletismo.


#### Pergunta/Análise 2

* Existe alguma relação entre altura do atleta e esporte praticado por ele? E em relação ao peso?

  * **Uso do modelo relacional**

  * Para essa análise, calculamos a media de altura dos atletas em cada modalidade, além da media geral da olímpiada. Com isso, podemos ver que modalidades tem maior e menor média tanto de altura como de peso.

  * Query SQL:

    ~~~sql
    /*Altura*/
    SELECT AnoEdicao, ROUND(AVG(CAST (Altura as float)),1) Media_altura
    FROM ParticipacaoAtletas
    WHERE AnoEdicao =2016 and Altura<>'-'
    GROUP BY AnoEdicao;

    SELECT * 
      FROM (
          SELECT E.EsportePai, E.Nome, ROUND(AVG(CAST (Altura as float)),1) Media_Altura
          FROM ParticipacaoAtletas P, EsporteModalidade E
          WHERE P.IdModalidade=E.Id and AnoEdicao=2016 and Altura<>'-'
          GROUP BY IdModalidade
          )
      ORDER BY MEDIA_ALTURA DESC
    ~~~
    ~~~sql
    /*Peso*/
    SELECT AnoEdicao, ROUND(AVG(CAST (Peso as float)),1) Media_peso
    FROM ParticipacaoAtletas
    WHERE AnoEdicao =2016 and Peso<>'-'
    GROUP BY AnoEdicao;

    SELECT * 
      FROM (
          SELECT E.EsportePai, E.Nome, ROUND(AVG(CAST (Peso as float)),1) Media_peso
          FROM ParticipacaoAtletas P, EsporteModalidade E
          WHERE P.IdModalidade=E.Id and AnoEdicao=2016 and Peso<>'-'
          GROUP BY IdModalidade
          )
      ORDER BY MEDIA_peso DESC
    ~~~

  * Resultado:

    Altura

    ![pergunta2resultado1](assets/pergunta2resultado1.png)
    ![pergunta2resultado2](assets/pergunta2resultado2.png)

    Peso

    ![pergunta2resultado3](assets/pergunta2resultado3.png)
    ![pergunta2resultado4](assets/pergunta2resultado4.png)

    Vemos que os atletas mais altos participam de esportes como basquete, volei, lançamento de disco e taekwondo, nas modalidades masculinas, enquanto que atletas mais baixos participam da ginástica e levantamento de peso, nas modalidades femininas. Já atletas de maior peso participam de esportes como levantamento de peso, lançamento de peso, judo e luta, nas modalidades masculinas, enquanto que os de menor peso participam de ginástica e ginástica rítmica, além de levantamento de peso, nas modalidades femininas.
    
#### Pergunta/Análise 3

* Qual a média de idade dos atletas nas primeiras Olimpíadas? E nas últimas?

  * **Uso do modelo relacional**

  * Para essa análise, a idade dos atletas é calculada com base no seu ano de nascimento e a edição em que participa. Em seguida, calculamos a média de idade por edição.

  * Query SQL:

    ~~~sql
    CREATE VIEW Idade AS
    SELECT P.IdAtleta, P.AnoEdicao, (P.AnoEdicao-cast (A.AnoDeNascimento as float)) AS idade
        FROM Atleta A, ParticipacaoAtletas P
        WHERE A.Id=P.IdAtleta and A.AnoDeNascimento<>'-';

    SELECT AnoEdicao, ROUND(AVG(idade),0) Media_Idade
        FROM Idade
        GROUP BY AnoEdicao
        ORDER BY AnoEdicao
    ~~~

  * Resultado:

    ![pergunta3resultado1](assets/pergunta3resultado1.png)
    ![pergunta3resultado2](assets/pergunta3resultado2.png)

    É possível ver que as médias permaneceram relativamente as mesmas, na faixa dos 20 a 30 anos.
      
#### Pergunta/Análise 4
 
* No período da Guerra Fria, é possível ver o predomínio das duas grandes potências nos pódios das Olímpiadas?

  * **Uso do modelo relacional**

  * Para essa análise, buscamos a classificação dos Estados Unidos e da União Soviética no periodo entre 1947 e 1989 (periodo da Guerra Fria).

  * Query SQL:

    ~~~sql
    SELECT AnoEdicao, IdComite, Classificacao
      FROM ParticipacaoComites
      WHERE (IdComite='USA' OR IdComite='URS') AND AnoEdicao>1947 AND AnoEdicao< 1989;
    ~~~

  * Resultado:

    ![pergunta4resultado](assets/pergunta4resultado.png)

    Vemos que, realmente, EUA e URSS estão constantemente na liderança.
      
#### Pergunta/Análise 5
 
* Qual a proporção de atletas do sexo masculino e do sexo feminino participando nos Jogos Olímpicos?

  * **Uso do modelo relacional**

  * Para essa análise, selecionamos o sexo dos atletas e agrupamos os dados de forma a encontrar o total de atletas do sexo masculino ou feminino em uma determinada edição.

  * Query SQL:

    ~~~sql
    SELECT P.ANOEDICAO, A.SEXO, COUNT(*) TOTAL
      FROM ATLETA A, PARTICIPACAOATLETAS P
      WHERE A.ID=P.IDATLETA
      GROUP BY P.ANOEDICAO, A.SEXO
      ORDER BY P.ANOEDICAO
    ~~~

  * Resultado:

    ![pergunta5resultado1](assets/pergunta5resultado1.png)
    ![pergunta5resultado2](assets/pergunta5resultado2.png)

    Vemos que a proporção entre os sexos é bem discrepante nas primeiras olimpíadas e que essa diferença vem diminuindo nos jogos mais recentes.

#### Pergunta/Análise 6

* Quais foram os países ganhadores de medalha de ouro no esporte X nas últimas 5 Olimpíadas?

  * **Uso do modelo hierárquico**

  * Para essa análise, percorremos o documento procurando os ganhadores de medalha de ouro do esporte desejado para as olimpíadas de 2000 a 2016.

  * Código python:

    ~~~python
    esporte="Judo"
    modalidade="Judo Women's Heavyweight"
    edicoes=["2016", "2012", "2008", "2004", "2000"]

    for i in range (5):
      ano=edicoes[i]
      for j in range (len(dados["edicoes"])-1, -1, -1):
        if (dados["edicoes"][j]["ano"]==ano):
          for k in range (len(dados["edicoes"][j]["esportesParticipantes"])):
            if (dados["edicoes"][j]["esportesParticipantes"][k]["nome"]==esporte):
              for l in range (len(dados["edicoes"][j]["esportesParticipantes"][k]["modalidades"])):
                if (dados["edicoes"][j]["esportesParticipantes"][k]["modalidades"][l]["nome"]==modalidade):
                  print(dados["edicoes"][j]["ano"]+": "+dados["edicoes"][j]["esportesParticipantes"][k]["modalidades"][l]["ouro"])
                  break   
    ~~~

  * Resultado:

    ![pergunta6resultado](assets/pergunta6resultado.png)

    Ganhadores de medalha de ouro na modalidade "Judo Women's Heavyweight"

#### Pergunta/Análise 7

* Quais as modalidades realizadas pelo atleta X na Olimpíada X?

  * **Uso do modelo hierárquico**

  * Para essa análise, percorremos o documento procurando as modalidades realizadas pelo atleta desejado em uma olimpíada específica.

  * Código python:

    ~~~python
    #Selecionando a olimpíada (Através do ano):
    ano="2004"
    #Selecionando o atleta (Através do nome):
    atleta="Daiane Garcia dos Santos"

    for j in range (len(dados["edicoes"])):
      if (dados["edicoes"][j]["ano"]==ano):
        numero=j
        break

    for k in range (len(dados["edicoes"][numero]["atletasParticipantes"])):
      if (dados["edicoes"][numero]["atletasParticipantes"][k]["nome"]==atleta):
        for l in range (len(dados["edicoes"][numero]["atletasParticipantes"][k]["esportes"])):
          print(dados["edicoes"][numero]["atletasParticipantes"][k]["esportes"][l]["nomeModalidade"]) 
    ~~~

  * Resultado:

    ![pergunta7resultado](assets/pergunta7resultado.png)

    Modalidades realizadas por Daiane dos Santos em 2004

### Perguntas/Análise Propostas mas Não Implementadas

#### Pergunta/Análise 1

* Quais os países que mais ganharam medalhas e os países que menos ganharam medalhas em uma determinada Olimpíada?

  * **Uso do modelo relacional**

  * Podemos selecionar os comites de maior e menor classificação em uma edição específica e até mesmo comparar entre diversas edições para analisar se os países alto classificados mantém sua posição e se os países de baixa classificação tem alguma evolução.

#### Pergunta/Análise 2

* Qual o número médio de medalhas de um país nas Olimpíadas que ele participou?

  * **Uso do modelo relacional**

  * Podemos calcular essa média para analisar que países conseguem manter um alto número de medalhas nas edições. Para isso, deve-se somar a quantidade de medalhas de ouro, prata e bronze de um comite para cada edição e, por fim, realizar a média.

#### Pergunta/Análise 3

* Em quantas Olimpíadas um determinado atleta participou e quantas medalhas ele ganhou?

  * **Uso do modelo relacional**

  * Trata-se de uma pergunta que busca saber o histórico de um atleta nas edições. Através da tabela de "participação dos atletas" podemos somar suas paticipações em jogos e as medalhas que conquistou.

#### Pergunta/Análise 4

* Quais países que mais trazem atletas para os Jogos Olímpicos nas últimas edições?

  * **Uso do modelo relacional**

  * Através da tabela de "participação dos comites", podemos obter facilmente essa informação e comparar entre os diversos anos para inferir quais países trazem mais atletas e, até mesmo, ver se isso tem uma relação com seu desempenho nos jogos.

#### Pergunta/Análise 5

* Para um determinado país, há uma tendência de piora ou de melhora no desempenho, nas Olimpíadas em que participou?

  * **Uso do modelo relacional**

  * Através da tabela de "participação dos comites", podemos ver se um país apresenta queda ou subida no número de medalhas e em sua classificação.

#### Pergunta/Análise 6

* Na Olímpiada de 1936, como foi o desempenho da Alemanha Nazista?

  * **Uso do modelo relacional ou hierárquico**

  * Pergunta voltada para um contexto histórico de pré Segunda Guerra Mundial e que busca saber qual foi o desempenho da Alemanha nos jogos sediados em seu próprio país. Podemos analisar seu número de medalhas, classificação e modalidades em que ficou no pódio. 

#### Pergunta/Análise 7

* Qual o número de atletas por país em uma determinada Olimpíada?

  * **Uso do modelo hierárquico**

  * Podemos procurar a edição desejada no json e percorrer o vetor de comites participantes, analisando a quantidade de atletas deles.

#### Pergunta/Análise 8

* Quais os atletas participantes de uma determinada Olimpíada e suas respectivas informações?

  * **Uso do modelo hierárquico**

  * Pergunta voltada para obter um conjunto de informações encapsuladas, o que é característico do modelo hierárquico. Para isso, podemos procurar a edição desejada no json e retornar o vetor de atletas participantes.

#### Pergunta/Análise 9

* Quais os comitês participantes de uma determinada Olimpíada e seus respectivos desempenhos?

  * **Uso do modelo hierárquico**

  * Pergunta voltada para obter um conjunto de informações encapsuladas, o que é característico do modelo hierárquico. Para isso, podemos procurar a edição desejada no json e retornar o vetor de comites participantes.

#### Pergunta/Análise 10

* Quais os esportes de uma determinada Olimpíada e os resultados de pódio?

  * **Uso do modelo relacional ou hierárquico**

  * Pergunta voltada para obter um conjunto de informações encapsuladas, o que é característico do modelo hierárquico. Para isso, podemos procurar a edição desejada no json e retornar o vetor de esportes participantes.

> O arquivo do notebook que executa o conjunto de queries sql pode ser acessado pelo link [queriesPerguntasModeloRelacional.ipynb](./notebooks/queriesPerguntasModeloRelacional.ipynb).

> O arquivo do notebook que executa os códigos em python para o modelo hierárquico pode ser acessado pelo link [queriesPerguntasModeloHierarquico.ipynb](./notebooks/queriesPerguntasModeloHierarquico.ipynb)


