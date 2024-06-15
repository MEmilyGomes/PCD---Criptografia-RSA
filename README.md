![Logotipo: Ilum- Escola de Ciências, Centro nacional de Pesquisa em Energia e Materiais(CNPEM), Misnistério da Educação, MCTI, Governo Federal: Brasil](https://github.com/MEmilyGomes/PCD---Criptografia-RSA/assets/172424897/8ab16e3d-9b90-4e14-b4ae-af54178c31fd) 

<h1> Criptografia - RSA </h1> 
<h2> Práticas Básicas de Ciência de Dados </h2>

<div align="justify">
<p>Esse arquivo se propõe a descrever as etapas para construir o projeto final da matéria de Práticas Básicas de Laboratório, ministrada pelo docente Doutor Leandro Nascimento Lemos, na instituição Ilum – Escola de Ciência em que optamos para usar as habilidades desenvolvidas para recriar a criptografia de RSA, usando a linguagem de Python e criando o código para teoremas essenciais para a otimização do processo de codificar e decodificar. O debate proposto é apresentado para mostrar como foi desenvolvido ferramentas para proteger dados sensíveis e confidencias, cenário comum no âmbito da pesquisa. Além disso, levanta-se a importância da otimização do código, da base teórica matemática e como é possível desenvolver metas audaciosas com o uso de HPC – computação de alto desempenho.
<br></p>

<h3>Sumário</h3>
<ul>
  <li><a href="#Introdução">Introdução</a></li>
  <li><a href="#Crivo de Eratóstenes">Crivo de Eratóstenes</a></li>
</ul>


<h3>Introdução</h3>
<div align="justify">
<p>O método de criptografia escolhido foi o RSA, nome esse que faz menção aos desenvolvedores (<i>Rivest – Shamir – Adelman</i>). Esse garante a segurança dos dados quando consegue elaborar boas chaves públicas, valores que serão utilizados nas operações necessárias para transformar cada caractere em um número a ser associado novamente com o seu caractere com outras operações e novas ótimas chaves, as privadas, posteriormente. Para conseguir as encontrar, é necessário obter os maiores números primos que o computador conseguir para realizar operações em um tempo hábil. Nesse sentido, os primeiros desafios foram pautados na elaboração de códigos que encontrasse números primos e, em segundo momento, os ajustes que fossem necessários para melhorar a eficiência.<br></p>

<h3>Crivo de Eratóstenes</h3>
<div align="justify">
Um dos teoremas matemáticos utilizados durante esse projeto foi o Crivo de Eratóstenes. Resumidamente, é um algoritmo matemático para identificar a quantidade de primos em um intervalo $\left[1,\ N\right]$, sendo $N\$  o último número inteiro positivo. Inicialmente, é criada uma lista contendo os números de $2$ até $N\$ , sem nenhum tipo de critério. Selecione, posteriormente, o primeiro número que não foi categorizado como composto, e defina-o como primo. Em seguida, marque todos os múltiplos desse número $n\$  como compostos, dado que possuem mais de dois divisores. Por fim, repita esse processo até que todos os números do intervalo sejam classificados. Assim, esse algoritmo apresenta uma eficiência maior do que a iterar todos os elementos da lista, em que o teste de primalidade é feito para cada um dos elementos. Utilizando uma comparação a partir da notação Big O, tem-se o seguinte cenário: $O\left(N\bullet\sqrt n\right)$ para a análise tradicional e $O\left(N\bullet\log{\left(n\right)}\right)$ para crivo de Eratóstenes, ou seja, uma redução de complexidade polinomial para complexidade logarítmica. Por isso, esse foi o método utilizado para esse projeto.
</p>





<p align="center">
<img loading="lazy" src="http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge"/>
</p>

<blockquote> teste para citações </blockquote>
