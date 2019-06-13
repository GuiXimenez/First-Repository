# Componente Feriados - IT Lab
Repositório para documentar o componente *IsHolliday* da IT Lab, biblioteca que retorna os feriados nacionais, móveis e opcionais no território brasileiro.
Projeto desenvolvido com base em TDD. 

# Útil para meu projeto?
&nbsp; &nbsp; &bull; Implemente todos os feriados nacionais fixos;

&nbsp; &nbsp; &bull; Implemente todos os feriados nacionais móveis;

&nbsp; &nbsp; &bull; Verifique qualquer data como feriado;

&nbsp; &nbsp; &bull; Pelas extensões você pode implementar os feriados do seu estado ou município;

&nbsp; &nbsp; &bull; Gere uma lista com todos os feriados, sendo eles móveis ou fixos;

&nbsp; &nbsp; &bull; Feriados do estado e da cidade de São Paulo disponíveis;

&nbsp; &nbsp; &bull; Este componente contempla emendas, com o uso de um método em específico.

# Como usar
Recomendamos o uso da IDE Visual Studio, na versão 2015 ou acima, você pode fazer o pull, ou clone, do repositório.

Compile a DLL, importante: note que a execução do projeto irá implementar o projeto de TDD, você pode apenas dar Build em todo projeto.

Na solução destino importe para as referências do projeto ao componente, que deve ser um arquivo .DLL.

# Tecnologias
&nbsp; &nbsp; &bull; C# 6.0

&nbsp; &nbsp; &bull;  .NET 4.5

# Ferramentas para desenvolvimento
&nbsp; &nbsp; &bull; Visual Studio 2015 (ou superior) - https://www.visualstudio.com/pt-br/downloads/

# Como o componente funciona
 Para implementar em seu projeto todos os feriados nacionais fixos, use o construtor de classe `Holidays()`. Faça a chamada do método `SetStaticHolidays()` para adicionar todos os feriados fixos do Brasil.

O construtor `Holidays(int[] Years)`, faz a chamada para o método `SetStaticHolidays()` para adicionar todos os feriados fixos e móveis baseado no ano passado como parâmetro. O ano pode ser um &#39;range&#39; de inteiro, para o cálculo de vários anos.

Para obter esses feriados, faça uma chamada para o método `GetHolidays()`, que retorna uma lista com todos os feriados adicionados no construtor, seja ele fixo, ou móvel. 

Esse componente também verifica apenas um único feriado, por exemplo, a aplicação precisa saber se o dia de vencimento de determinada ação é um feriado, como Corpus Christ, para aplicar-lhe uma regra a condição booleana.

**Atenção**: valores para essa lista só estão disponíveis após a instanciação da classe.

Saiba mais sobre todos os métodos implementados nesse componente, [clique aqui](http://google.com.br "aqui").

Cada um dos métodos a seguir pode ser usado como `Static` e retornam booleano para o objeto `DateTime` fornecido.

## Método para o cálculo da Páscoa
+ ***CalculoPascoa(int year)*** <br>
Esse método retorna o domingo de Páscoa do ano, ou &quot;range&quot;, recebido como parâmetro. As verificações dos feriados móveis ocorrem por métodos estáticos, usando como base o dia da Páscoa.
>No Brasil, e em outros países ocidentais cristãos, é seguido o decreto de Concilio de Nicéia, que data do ano 325, determinando que o dia de Páscoa deve ser celebrado no primeiro domingo depois da lua cheia que segue o equinócio de outono.” <br>Fonte: MIRANDA, Paulo, IME-USP.

## Métodos de feriados móveis
+ ***CalculoCarnaval(int year)*** <br>
O método que calcula o dia do carnaval, recebe uma data obtida pelo método `CalculoPascoa(int year)` do mesmo ano fornecido como parâmetro. Para sua utilização é necessário fornecer um objeto DateTime como resultado.
<br>O Carnaval é um festival do cristianismo ocidental, que não integra o calendário oficial de feriados brasileiros, ou seja, os municípios que optam por decretar como ponto facultativo.
<br>Para saber mais do cálculo da Páscoa veja: `CalculoPascoa(int year)`

+ ***IsCarnaval(DateTime date)*** <br>
Método chamado para relacionar as datas e fazer a verificação da data fornecida como parâmetro para o ponto facultativo de Carnaval.

+ ***IsCorpusChristi(DateTime date)*** <br>
Esse método chama o `CalculoPascoa(int year)` para verificar o feriado de Pascoa, e a partir desse resultado é acrescido 60 dias, que é a data em que é celebrado o feriado de Corpus Christi.

+ ***IsGoodFriday(DateTime date)*** <br>
Esse método chama o `CalculoPascoa(int year)` para verificar o feriado de Pascoa, e a partir desse resultado é subtraído dois dias, que é a data em que é celebrada a Sexta-feira Santa.

## Métodos de feriados fixos
+ ***IsNewYear(DateTime date)*** <br>
Método que verifica se a data recebida é o feriado do Ano Novo, que é comemorado todo dia 01 de Janeiro.

+ ***IsTiradentes(DateTime date)*** <br>
Método que verifica se a data recebida é o feriado de Tiradentes, que é comemorado todo dia 21 de Abril.

+ ***IsWorkDay(DateTime date)*** <br>
Método que verifica se a data recebida é o feriado do Dia do Trabalho, que é comemorado todo dia 01 de Maio.

+ ***IsIndependenceDay(DateTime date)*** <br>
Método que verifica se a data recebida é o feriado da Independência do Brasil, que é comemorado todo dia 7 de Setembro.

+ ***IsChildrensDay(DateTime date)*** <br>
Método que verifica se a data recebida é o feriado da padroeira do Brasil, Nossa Senhora Aparecida, popularmente conhecido como Dia das Crianças, que ocorre todo dia 12 de Outubro.

+ ***IsAllSoulsDay(DateTime date)*** <br>
Método que verifica se a data recebida é o feriado de Finados, ou dia de Todas as Almas, que ocorre todo dia 2 de Novembro.

+ ***IsRepublicProclamation(DateTime date)*** <br>
Método que verifica se a data recebida é o feriado de Proclamação da República, que ocorre todo dia 15 de Novembro.

+ ***IsBlackConsciousnessDay(DateTime date)*** <br>
Método que verifica se a data recebida é o feriado da Consciência Negra, que ocorre todo dia 20 de Novembro. É necessário consultar a cidade, ou estado, em que será aplicado esse método, já que esse feriado alguns estados e cidades do Brasil não o adotam.

+ ***IsChristmasDay(DateTime date)*** <br>
Método verifica se a data fornecida como parâmetro coincide com a data fixa para o Natal, em 25 de dezembro.

## Método de emendas de feriado
Para adicionar emendas, pertinentes as regras de negócio do seu projeto, use o método `IsOptionalDate(DateTime date)`.

+ ***IsOptionalDate(DateTime date)*** <br>
Esse método retorna verdadeiro para todas as emendas comuns de feriados.

## Adicionar Novo Feriado
+ ***Holiday()*** <br>
Para cobrir a necessidade da adição de feriados regionais, essa classe foi construída. O objeto dessa classe associa uma data a um novo feriado, de acordo com a regra de negócio aplicada a seu projeto.

+ ***Add(Holiday holiday)*** <br>
Usando o `Add(Holiday holiday)`, é permitido o acrescimento de outras datas como feriados.

Através da classe `Holidays()`, esse novo feriado terá as propriedades de todos os outros, existentes neste componente, sendo assim o método `GetHolidays()`, retorna essa nova adição dentro de todos os feriados, já contemplados nesse componente.

## Adicionar Feriados do Estado de São Paulo
Neste componente, somente os feriados do estado de São Paulo estão disponíveis. Para isso, use o método `AddHolidaySP()`. 
Por padrão, faça a chamada antes da instância do &#39;componente&#39; Holiday.

## Métodos dos Feriados de São Paulo
+ ***IsSaoPauloBirthday(DateTime date)*** <br>
Método que verifica se a data recebida é o feriado do Aniversário de São Paulo, que é comemorado todo dia 25 de janeiro.

+ ***IsRevolutionDay(DateTime date)*** <br>
Método que verifica se a data recebida é o feriado da Revolução Constitucionalista, que é comemorado todo dia 09 de Julho.

+ ***IsBlackConsciousnessDay(DateTime date)*** <br>
Método que verifica se a data recebida é o feriado da Consciência Negra, que ocorre todo dia 20 de Novembro.

# Limites e restrições
+ O componente não consegue definir emendas de feriados, para isso, você precisa usar o método `IsOptionalDate(DateTime date)`;
+ O componente traz apenas feriados em âmbito nacional;
