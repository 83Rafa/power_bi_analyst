<div text-align="justify">
    <figure>
    <img src="https://hermes.dio.me/tracks/b9b2973e-b2be-4bf0-b6b2-57a6c8354a95.png" class="logo" width="80" align="right">
  </figure>
    <h1>Processando e Transformando Dados com Power BI</h1>
</div>
<div align="center">
  <img src="images/Power-BI.jpg" width="1000" height="280">
</div>
<div>
    <p>Acesse o arquivo <a href="https://github.com/83Rafa/power_bi_analyst/blob/main/desafio_de_projeto_3/azure_company.pbix">Azure Company</a>.pbix</p>
</div>
<div>
    <h3>DIO - Desafio de Projeto</h3>
    <p><strong>Objetivo Geral:</strong></p>
    <ul>
        <li>Configurar o setup de banco de dados na Azure</li>
        <li>Popular o servidor com script fornecido</li>
        <li>Integrar o MySQL com Power BI</li>
        <li>Realizar as transformações indicadas</li>
    </ul>
    <hr>
    <h3>Na visualização prévia foi possível encontra algumas mudaças necessárias:</h3>
    <ol>
        <li>Os funcionários <i>James E Borg</i> e <i></i>Franklin T Wong</i> possuiam valores nulos para <i>Super_ssn</i>. Observando seus respectivos departamentos foi possível idenfificar que os dados não foram preenchidos porque os mesmos são os gerentes.</li>
        <li><i>John B Smith</i> também não possuia dados sobre seu gerente. Ele trabalha no departamento <i>Research</i>, cujo gerente é <i>Franklin T Wong</i>. Sendo assim, o dado faltante foi corrigido.</li>
        <li>Também já na pré-visualização foi possivel encontrar mais um ponto em que uma atualização foi requisitada. A junção de colunas para que os nomes dos funcionários ficassem em uma única coluna. Através da função <i>Mesclar Colunas</i> foi possível juntar Fname, Minit e Last name em uma coluna <i>Employee_name</i>.</li>
    </ol>
    <h3>Analisando os dados mais profundamente foi possível realizar as seguintes mudanças:</h3>
    <ul>
        <li>Todos os funcionários com seus respectivos departamentos e gerentes.</li>
        <li>Todos os dados nulos foram tratados.</li>
        <li>Todas colunas desnecessárias foram removidas</li>
        <li>Todo departamento tem seu gerente designado.</li>
    </ul>
    
<p>Os tipos dos dados foram atualizados, e.x. <i>Salary</i> de Números Inteiros agora possui Número Decimal Fixo.</p>
<p>À partir das colunas "Datas", com a função <i>Data</i> foi possível separar e criar colunas para dia, mês e ano. O mesmo para as colunas de endereço. Através da função <i>Dividir Colunas por Delimitador</i>. Endereço e UF foram separados em colunas.</p>
    <p>A tabela <strong>Employee/Department</strong> foi criada através da mescla das respectivas tabelas. As colunas redundantes foram removidas. </p>
    <p>A tabela, a <strong>Department/Location</strong> foi gerada à partir da mescla das tabelas <i>Department</i> e <i>Dept_location</i>. A utilização da função de <i>"Mescla"</i> para essa situação se deu pela diferença de propósito em relação a função <i>"Atribuir"</i>. A grande diferenca entre as duas é que a função Mesclar no Power BI é usada para combinar duas ou mais tabelas com base em colunas relacionadas. É semelhante a um JOIN em SQL. Enquanto a função Atribuir permite que se atribua usuários a funções (neste caso: departamento à localizações), seja individualmente ou em grupo.</p>
    <p>Também foi possível a criação de uma terceira tabela <strong>Project Working Hours</strong> à partir da junção das tabelas <i>Project</i> com as tabelas <i>works_on</i> e <i>Employee</i> para facilitar a análise de horas trabalhadas por funcionário em cada projeto.</p>
</div>

<div align="center">
    <h3>Relatório Web</h3>
  <img src="images/relatorio.png">
    <h3>Relatório Mobile</h3>
  <img src="images/relatorio_mobile_full.png">
    <h3>Publicação do Relatório</h3>
  <img src="images/relatorio_publicado.png">
</div>

<div>
    <h3>Diferença entre Combinar e Mesclar consultas</h3>
    <p>No Power BI, existem duas maneiras de combinar consultas: <strong>Acrescentar Consultas</strong> e <strong>Mesclar Consultas</strong>.</p>
    <p>A operação de <i>Acrescentar Consultas</i>  consiste em pegar os resultados de duas ou mais consultas e transformá-los em uma só consulta contendo todos os resultados de cada uma das tabelas/consultas utilizadas no processo . Por exemplo, se uma consulta tiver 50 linhas e a outra consulta tiver 100 linhas, a operação criará uma nova consulta com 150 linhas.</p>
    <p>Já a operação de <i>Mesclar Consultas</i> une duas tabelas existentes com base em valores correspondentes de uma ou várias colunas. Você pode optar por usar diferentes tipos de junções, dependendo da saída desejada.</p>
    <h3>Funcionários organizados por gerentes:</h3>
    <p>No relatório foram criados gráficos de barras e de àrea para demonstrar a proporção de funcionários por gerente e cartões com suas respectivas contagem. Também há a seguinte query para uma pesquisa no banco de dados: </p>
</div>

```
SELECT m.Fname AS Manager, CONCAT(e.Fname, ' ', e.Minit, ' ', e.Lname) AS Employee, e.Salary, e.Dno
            FROM employee e 
            LEFT OUTER JOIN employee m
            ON e.Super_ssn = m.Ssn
            ORDER BY Manager;
```

<footer>
  <div class="logotipo" align="right">
    <figure>
      <img src="https://hermes.digitalinnovation.one/assets/diome/logo-minimized.png" alt="logo dio minimizada" class="sc-TRNrF kCkrow" width="80">
    </figure>
  </div>
  <div class="small-subtitle" align="right">
    <p><small><i>Formação DIO.</i></small></p>
  </div>
</footer>
