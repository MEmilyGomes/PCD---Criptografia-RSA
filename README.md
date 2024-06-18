![Logotipo: Ilum- Escola de Ciências, Centro nacional de Pesquisa em Energia e Materiais(CNPEM), Misnistério da Educação, MCTI, Governo Federal: Brasil](https://github.com/MEmilyGomes/PCD---Criptografia-RSA/assets/172424897/8ab16e3d-9b90-4e14-b4ae-af54178c31fd) 

<h1> Criptografia - RSA </h1> 
<h2> Práticas Básicas de Ciência de Dados </h2>

<div align="justify">
<p>Esse arquivo se propõe a descrever as etapas para construir o projeto final da matéria de Práticas Básicas de Laboratório, ministrada pelo docente Doutor Leandro Nascimento Lemos, na instituição Ilum – Escola de Ciência em que optamos para usar as habilidades desenvolvidas para recriar a criptografia de RSA, usando a linguagem de Python e criando o código para teoremas essenciais para a otimização do processo de codificar e decodificar. O debate proposto é apresentado para mostrar como foi desenvolvido ferramentas para proteger dados sensíveis e confidencias, cenário comum no âmbito da pesquisa. Além disso, levanta-se a importância da otimização do código, da base teórica matemática e como é possível desenvolver metas audaciosas com o uso de HPC – computação de alto desempenho.

<blockquote>
  <i>Uma criptografia robusta é capaz de resistir a uma aplicação ilimitada de violência. Nenhuma força repressora poderá resolver uma equação matemática.
  Julian Assange</i>
</blockquote>
  
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
<li><a href="#Segunda codificação do texto">Segunda codificação do texto</a></li>
<li><a href="#Função totiente de Euler">Função totiente de Euler</a></li>
<li><a href="#Encontrar o expoente público">Encontrar o expoente público</a></li>
<li><a href="#Encontrar o expoente privado">Encontrar o expoente privado</a></li>
<li><a href="#Codificação do RSA">Codificação do RSA</a></li>
<li><a href="#Teste de eficiência">Teste de eficiência</a></li>
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
<p>Primeramente, após importar as bibliotecas, foi utilizado o método <code>sys.set_int_max_str_digits(0)</code> para corrigir o erro do limite de conversão (4300) de string para inteiros. Além disso, foi definida a variável tempo_inicio, que recebeu o valor, em segundos, do tempo de execução do código. Nas próximas etapas, pode-se dividir o procedimento em seis partes:
</p>

<ul>
  <h4 id="Método de Euclides">Método de Euclides</h4>
  <div align="justify">
  <p>Para determinar o Máximo Divisor Comum (MDC), foi definida a função <code>mdc</code>, a qual comporta dois argumentos: <code>valor_1</code> e <code>valor_2</code>. Caso a divisão do       
  <code>valor_1</code> pelo <code>valor_2</code> tenha um resto igual a zero, <code>valor_2</code> é retornado; se não, atualiza-se os argumentos para <code>valor_2</code> e o “resto”, de modo que o algoritmo é continuado até que o caso-base seja atendido.  Assim, pode-se definir como um algoritmo de recursão.
    
![carbon](https://github.com/MEmilyGomes/PCD---Criptografia-RSA/assets/172424921/ea2c75e9-f8b2-4d90-a0ce-efe01abe3d0f)
 
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
   possíveis, como são 373 caracteres a lista vai de 0 até 372 e relaciona todos os caracteres ao seu respectivo número. Após isso a função <code>codifica_parte_um</code> percorre 
   todos os caracteres presentes no arquivo .txt e para cada caractere ela pega os números e soma 100 para que todos os valores tenham três algarismos e retoma uma lista 
   chamada criptografia. 
  </p>

  ![carbon (2)](https://github.com/MEmilyGomes/PCD---Criptografia-RSA/assets/172424921/023cb498-d5d9-486d-aa6c-96eabba205f0)
  
  <h4 id="Encontrar os primos">Encontrar os primos</h4>
  <div align="justify">
  <p>
   Para encontrar os primos o código usado foi o código chamado Crivo de Eratóstenes, que encontra o enésimo valor primo desejado pelo usuário, esse código foi o mais 
   eficiente encontrado pois ele funciona a partir da criação de uma lista até o enésimo termo e pega o primeiro valor primo, no caso o 2, após isso ele desconsidera todos 
   os múltiplos desse número na lista e passa para o próximo não eliminado, no caso o 3 e repete esse processo, como resultado ele consegue todos os números primos até o 
   limite estabelecido. A próxima etapa é pegar o segundo valor primo que também usa o Crivo de Eratóstenes. 
  </p>

![carbon (7)](https://github.com/MEmilyGomes/PCD---Criptografia-RSA/assets/172424921/b57805c7-1a36-45c5-8709-de410dd40ae7)

<blockquote>
  <i>Fonte: ChatGPT 3.4 (fins educacionais/acadêmicos)</i>
</blockquote>


  <h4 id="Ler o texto original e escrever o texto criptgrafado">Ler o texto original e escrever o texto criptgrafado</h4>
  <div align="justify">
  <p>
  Essas funções têm o objetivo de trabalhar com os arquivos em formato .txt para etapas posteriores em que o texto criptografado será escrito em um arquivo.
  </p>
    
![carbon (8)](https://github.com/MEmilyGomes/PCD---Criptografia-RSA/assets/172424921/eb2d9b18-7d03-4912-a0a2-afa27fd06f53)

  
  <h4 id="Definição da chave pública">Definição da chave pública</h4>
  <div align="justify">
  <p>
  Essa etapa se inicia definindo dois enésimos termos para o Crivo de Euclídes, os valores aleatórios são definidos em um intervalo à escolha do usuário, por exemplo, o 
  usuário pode colocar um intervalo entre o 100.000° e 1.000.000° primo e o algoritmo será capaz de pegar, por exemplo, o 500.000° número primo. Depois disso cada um dos 
  dois valores é armazenado em uma variável. A chave pública é a multiplicação dos dois primos gerados. 
  </p>

![carbon (9)](https://github.com/MEmilyGomes/PCD---Criptografia-RSA/assets/172424921/46c3b645-47c3-4c64-ac4a-965751ff4cd3)

  
  <h4 id="Segunda codificação do texto">Segunda codificação do texto</h4>
  <div align="justify">
  <p>
  Para a codificação real do texto o número primo usado é a chave pública, como esse valor é muito grande a codificação do texto é muito mais segura. 
  </p>
  
  <h4 id="Função totiente de Euler ">Função totiente de Euler</h4>
  <div align="justify">
  <p>
    Essa função tem o intuito de achar um número que tem o mdc entre os dois primos de 1, para isso a função é definida como a multiplicação entre os antecessores dos dois primos. 
  </p>


  <h4 id="Encontrar o expoente público">Encontrar o expoente público</h4>
  <div align="justify">
  <p>
   Inicialmente, a função <code>acha_coprimos</code> é definida para achar o número que tem mdc igual a 1 com o <code>valor_z</code> escolhido e os valores no range de 3 ao <code>valor_z</code>. Após isso o expoente público é definido como <code>acha_coprimos(z)</code> para procurar qual é o valor de e para o qual o mdc com o valor 5 tem resultado de 1.

  ![carbon (12)](https://github.com/MEmilyGomes/PCD---Criptografia-RSA/assets/172424921/20e2b32f-6292-4334-985e-1e48df2f3ac3)

    
  </p>

  <h4 id="Encontrar o expoente privado ">Encontrar o expoente privado</h4>
  <div align="justify">
  <p>
   O conceito de inverso modular diz respeito ao resto da multiplicação entre dois números a e b, se esse resto for 1 eles são inversos modulares entre si, a função <code>achar_d</code> faz isso. Após isso, definimos d como a função <code>achar_d</code> aplicada aos valores do toriente de Euler (z) e o expoente público (e).

  ![carbon (13)](https://github.com/MEmilyGomes/PCD---Criptografia-RSA/assets/172424921/7943bdaa-437f-4572-9251-70601b12022e)

    
  </p>

  <h4 id="Codificação do RSA">Codificação do RSA</h4>
  <div align="justify">
  <p>
   Após isso ocorre a codificação do texto a partir da multiplicação de cada número da lista codificada usando a chave pública pelo expoente público e pela chave pública. Feito isso o algoritmo escreve um arquivo .txt com os valores codificados a partir da codificação RSA e com o auxílio de uma função que escreve os valores da lista no formato de string. 
  
  ![carbon (14)](https://github.com/MEmilyGomes/PCD---Criptografia-RSA/assets/172424921/24c14300-91b1-43c2-a8b9-add44bd556b2)


  </p>

  <h4 id="Teste de Eficiência">Teste de Eficiência</h4>
  <div align="justify">
  <p>
   A biblioteca timeit foi usada para testar quanto tempo o computador demora para rodar o código para facilitar com que o usuário consiga criptografar suas mensagens da maneira mais conveniente e para que testes pudessem ser feitos pelos membros do grupo sobre quanto tempo demora para um HPC rodar o código com diferentes quantidades de algarismos. 

  </p>

<h3 id="Descriptografia">Descriptografia</h3>
<div align="justify">
<p>
<br></p>

  <h4 id="Definição das Funções">Definição das Funções</h4>
  <div align="justify">
  <p>
    A função <code>lista_codifica</code> realiza a descriptografia de uma lista de valores numéricos
 codificados usando o algoritmo RSA. Foram colocados três parâmetros: <code>codificada</code>, que é a lista de valores numéricos codificados que serão descriptografados; <code>valor_d</code> e <code>valor_n</code> que são os valores da chave pública <code>d</code> e privada <code>n</code>, respectivamente. 

 Além disso, a função <code>decodifica_parte_um</code> converte os valores numéricos descriptografados de volta para caracteres, assumindo que <code>combined_characteres</code> contém os caracteres correspondentes à codificação original. Como parâmetro, temos <code>lista_decodificada</code>, que é a lista de valores numéricos descriptografados. É retornada uma string com o texto codificado correspondente. 

![carbon (15)](https://github.com/MEmilyGomes/PCD---Criptografia-RSA/assets/172424921/3de7a475-4a61-4deb-84a3-8c083aaabd57)

  </p>
  <h4 id="Entrada do usuário">Entrada do usuário</h4>
  <div align="justify">
  <p>
   Esse trecho do código solicita ao usuário o nome do arquivo criptografado, o valor da chave privada <code>d</code> e da chave pública <code>n</code>
  </p>

  <h4 id="Leitura do texto criptografado">Leitura do texto criptografado</h4>
  <div align="justify">
  <p>
   A função <code>ler_texto_arquivo(nome_arquivo_criptografado)</code> para ler o texto criptografado do arquivo especificado pelo usuário. Após isso, o texto é convertido em uma lista de inteiros <code>(codificada)</code> utilizando <code>split()</code> para separar os números e <code>map(int, ...)</code> para converter em inteiros.
  </p>

  <h4 id="Decodificar a Lista">Decodificar a Lista</h4>
  <div align="justify">
  <p>
   A variável “decodificada” recebe o valor da <code>lista_decodificada</code>, que possui os argumentos <code>codificada</code>, <code>d</code>, <code>n</code>. Em seguida, ocorre a impressão desses valores numéricos desencriptados.
  </p>

  <h4 id="Converter a lista decodificada de volta para o texto original">Converter a lista decodificada de volta para o texto original</h4>
  <div align="justify">
  <p>
   Cada número é associado a uma letra específica. Assim, esse texto decodificado é impresso
  </p>

  <h4 id="Escrever o texto decodificado">Escrever o texto decodificado</h4>
  <div align="justify">
  <p>
   O texto decodificado é impresso e salvo em um arquivo “.txt”.
  </p>


    
</div></ul>

<p align="center">
<img loading="lazy" src="http://img.shields.io/static/v1?label=STATUS&message=EM%20DESENVOLVIMENTO&color=GREEN&style=for-the-badge"/>
</p>

