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
<li><a href="#Algoritmo de Euclides">Algoritmo de Euclides</a></li>
<li><a href="#Processo de criptografia">Processo de criptografia</a></li>
<ul>
<li><a href="#Método de Euclides">Método de Euclides</a></li>
<li><a href="#Definição dos possíveis caracteres">Definição dos possíveis caracteres</a></li>
<li><a href="#Primeira codificação do texto">Primeira codificação do texto</a></li>
<li><a href="#Encontrar os primos">Encontrar os primos</a></li>
<li><a href="#Ler o texto original e escrever o texto criptgrafado">Ler o texto original e escrever o texto criptgrafado</a></li>
<li><a href="#Definição da chave pública">Definição da chave pública</a></li>
</ul>  
</ul>


<h3 id="Introducao">Introdução</h3>
<div align="justify">
<p>O método de criptografia escolhido foi o RSA, nome esse que faz menção aos desenvolvedores (<i>Rivest – Shamir – Adelman</i>). Esse garante a segurança dos dados quando consegue elaborar boas chaves públicas, valores que serão utilizados nas operações necessárias para transformar cada caractere em um número a ser associado novamente com o seu caractere com outras operações e novas ótimas chaves, as privadas, posteriormente. Para conseguir as encontrar, é necessário obter os maiores números primos que o computador conseguir para realizar operações em um tempo hábil. Nesse sentido, os primeiros desafios foram pautados na elaboração de códigos que encontrasse números primos e, em segundo momento, os ajustes que fossem necessários para melhorar a eficiência.<br></p>

<h3 id="Crivo de Eratóstenes">Crivo de Eratóstenes</h3>
<div align="justify">
<p>Um dos teoremas matemáticos utilizados durante esse projeto foi o Crivo de Eratóstenes. Resumidamente, é um algoritmo matemático para identificar a quantidade de primos em um intervalo $\left[1,\ N\right]$, sendo $N$  o último número inteiro positivo. Inicialmente, é criada uma lista contendo os números de $2$ até $N$ , sem nenhum tipo de critério. Selecione, posteriormente, o primeiro número que não foi categorizado como composto, e defina-o como primo. Em seguida, marque todos os múltiplos desse número $n$  como compostos, dado que possuem mais de dois divisores. Por fim, repita esse processo até que todos os números do intervalo sejam classificados. Assim, esse algoritmo apresenta uma eficiência maior do que a iterar todos os elementos da lista, em que o teste de primalidade é feito para cada um dos elementos. Utilizando uma comparação a partir da notação Big O, tem-se o seguinte cenário: $O\left(N\bullet\sqrt n\right)$ para a análise tradicional e $O\left(N\bullet\log{\left(n\right)}\right)$ para crivo de Eratóstenes, ou seja, uma redução de complexidade polinomial para complexidade logarítmica. Por isso, esse foi o método utilizado para esse projeto.
</p>

<h3 id="Algoritmo de Euclides">Algoritmo de Euclides</h3>
<div align="justify">
Além disso, para encontrar o Máximo Divisor Comum (MDC), foi aplicado o algoritmo de Euclides: dado dos números inteiros A e B, verificamos se A ou B são iguais a 0. Caso A=0, tem-se que MDC (A, B) = B; se B=0, MDC (A, B) =A. Contudo, se ambos forem diferentes de zero, o processo é continuado, de modo que A é escrito como B\cdot Q\ +\ R\ , tal que Q\ e R\ são quociente e resto, respectivamente. Por fim, calcule o MDC (B, R) utilizando o mesmo procedimento, haja visto que MDC (B, R) = MDC (A, B). Isso é realizado até que o caso base (A ou B = 0) seja cumprido.</p>

<h3 id="Processo de criptografia">Processo de criptografia</h3>
<div align="justify">
<p>Primeramente, após importar as bibliotecas, foi utilizado o método “sys.set_int_max_str_digits(0)” para corrigir o erro do limite de conversão (4300) de string para inteiros. Além disso, foi definida a variável “tempo_inicio”, que recebeu o valor, em segundos, do tempo de execução do código. Nas próximas etapas, pode-se dividir o procedimento em seis partes:
</p>

<ul>
  <h4 id="Método de Euclides">Método de Euclides</h4>
  <div align="justify">
  <p>Para determinar o Máximo Divisor Comum (MDC), foi definida a função “mdc”, a qual comporta dois argumentos: “valor_1” e “valor_2”. Caso a divisão do “valor_1” pelo 
  “valor_2” tenha um resto igual a zero, “valor_2” é retornado; se não, atualiza-se os argumentos para “valor_2” e o “resto”, de modo que o algoritmo é continuado até que o 
  caso-base seja atendido.  Assim, pode-se definir como um algoritmo de recursão.
  </p>
  
  <h4 id="Definição dos possíveis caracteres">Definição dos possíveis caracteres</h4>
  <div align="justify">
  <p>
   aqui algo
  </p>

  <h4 id="Primeira codificação do texto">Primeira codificação do texto</h4>
  <div align="justify">
  <p>
   Nessa etapa ocorre a codificação de cada um dos caracteres do texto. O código funciona a partir de uma lista de números com o range de 0 até a quantidade de caracteres 
   possíveis, como são 373 caracteres a lista vai de 0 até 372 e relaciona todos os caracteres ao seu respectivo número. Após isso a função “codifica_parte_um” percorre 
   todos os caracteres presentes no arquivo .txt e para cada caractere ela pega os números e soma 100 para que todos os valores tenham três algarismos e retoma uma lista 
   chamada criptografia. 
  </p>

  <h4 id="Encontrar os primos">Encontrar os primos</h4>
  <div align="justify">
  <p>
   Para encontrar os primos o código usado foi o código chamado Crivo de Eratóstenes, que encontra o enésimo valor primo desejado pelo usuário, esse código foi o mais 
   eficiente encontrado pois ele funciona a partir da criação de uma lista até o enésimo termo e pega o primeiro valor primo, no caso o 2, após isso ele desconsidera todos 
   os múltiplos desse número na lista e passa para o próximo não eliminado, no caso o 3 e repete esse processo, como resultado ele consegue todos os números primos até o 
   limite estabelecido. A próxima etapa é pegar o segundo valor primo que também usa o Crivo de Eratóstenes. 
  </p>

  <h4 id="Ler o texto original e escrever o texto criptgrafado">Ler o texto original e escrever o texto criptgrafado</h4>
  <div align="justify">
  <p>
  Essas funções têm o objetivo de trabalhar com os arquivos em formato .txt para etapas posteriores em que o texto criptografado será escrito em um arquivo. 
  </p>

  <h4 id="Definição da chave pública">Definição da chave pública</h4>
  <div align="justify">
  <p>
  Essa etapa se inicia definindo dois enésimos termos para o Crivo de Euclídes, os valores aleatórios são definidos em um intervalo à escolha do usuário, por exemplo, o 
  usuário pode colocar um intervalo entre o 100.000° e 1.000.000° primo e o algoritmo será capaz de pegar, por exemplo, o 500.000° número primo. Depois disso cada um dos 
  dois valores é armazenado em uma variável. A chave pública é a multiplicação dos dois primos gerados. 
  </p>

  <h4 id="Codificação final do texto">Codificação final do texto</h4>
  <div align="justify">
  <p>
  Para a codificação real do texto o número primo usado é a chave pública, como esse valor é muito grande a codificação do texto é muito mais segura. 
  </p>
    
</div></ul>

<p align="center">
<img loading="lazy" src="http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge"/>
</p>


<blockquote> teste para citações </blockquote>
