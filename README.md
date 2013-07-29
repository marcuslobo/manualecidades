#1 - Licença deste Documento

Para a utilização deste documento é necessário seguir as regras da licença Creative Commons pela mesma Licença 2.0 Brasil [](http://creativecommons.org/licenses/by-nc-sa/2.0/br/deed.pt_BR). 

Você tem a liberdade de:

![](https://raw.github.com/marcuslobo/manualecidades/master/imagens/1b.png) &nbsp; Compartilhar — copiar, distribuir e transmitir a obra.

![](https://raw.github.com/marcuslobo/manualecidades/master/imagens/2.png) &nbsp; Remixar — criar obras derivadas.

Sob as seguintes condições:

![](https://raw.github.com/marcuslobo/manualecidades/master/imagens/3.png) &nbsp;Atribuição — Você deve creditar a obra da forma especificada pelo autor ou licenciante (mas não de maneira que sugira que estes concedem qualquer aval a você ou ao seu uso da obra). 

![](https://raw.github.com/marcuslobo/manualecidades/master/imagens/4.png) &nbsp;Compartilhamento pela mesma licença — Se você alterar, transformar ou criar em cima desta obra, você poderá distribuir a obra resultante apenas sob a mesma licença, ou sob uma licença similar à presente. 

Ficando claro que:
Renúncia — Qualquer das condições acima pode ser [renunciada](http://creativecommons.org/licenses/by-nc-sa/2.5/br/deed.pt_BR#) se você obtiver permissão do titular dos direitos autorais. 
Domínio Público — Onde a obra ou qualquer de seus elementos estiver em [domínio público](http://wiki.creativecommons.org/Public_domain) sob o direito aplicável, esta condição não é, de maneira alguma, afetada pela licença. 
Outros Direitos — Os seguintes direitos não são, de maneira alguma, afetados pela licença: 
Limitações e exceções aos direitos autorais ou quaisquer [usos livres](http://wiki.creativecommons.org/Frequently_Asked_Questions#Do_Creative_Commons_licenses_affect_fair_use.2C_fair_dealing_or_other_exceptions_to_copyright.3F) aplicáveis; 
Os [direitos morais](http://wiki.creativecommons.org/Frequently_Asked_Questions#I_don.E2.80.99t_like_the_way_a_person_has_used_my_work_in_a_derivative_work_or_included_it_in_a_collective_work.3B_what_can_I_do.3F) do autor; 
Direitos que outras pessoas podem ter sobre a obra ou sobre a utilização da obra, tais como [direitos de imagem](http://wiki.creativecommons.org/Frequently_Asked_Questions#When_are_publicity_rights_relevant.3F) ou privacidade. 
Aviso — Para qualquer reutilização ou distribuição, você deve deixar claro a terceiros os termos da licença a que se encontra submetida esta obra. A melhor maneira de fazer isso é com um link para esta página. 


#2 - Introdução ao Sistema e-cidade

O e-cidade destina-se a informatizar a gestão dos Municípios Brasileiros de forma integrada. Essa informatização contempla a integração entre os entes municipais: Prefeitura Municipal, Câmara Municipal, Autarquias, Fundações e outros.
A economia de recursos é somente uma das vantagens na adoção do e-cidade. Há liberdade de escolha dos fornecedores e garantia de continuidade do sistema, uma vez que é apoiado pelo Ministério do Planejamento. 
## 2.1 - Características 
O código fonte está disponível para ser baixado livremente no Portal do Software Público Brasileiro: www.softwarepublico.gov.br. 
O sistema possui a seguinte plataforma tecnológica:

LINUX
<br>APACHE – PHP</br>
<br>POSTGRESQL – PSQL</br>
<br>FPDF</br>
<br>AGATA – API</br>
<br>FIREFOX</br>
<br>HTML / CSS / JAVASCRIPT</br>
JAVA TOMCAT</br>
<br>ECLIPSE<br>

![](https://raw.github.com/marcuslobo/manualecidades/master/imagens/5.png) &nbsp;


#3 - Instalação do Sistema

##3.1 - Informações gerais para instalação

É recomendado que este guia seja executado por um usuário com experiência em instalação de pacotes no Linux e configuração básica de Apache, PHP e PostgreSQL. 
Este roteiro está baseado no Sistema Operacional GNU/Linux Ubuntu 10.04 LTS. Cabe lembrar que em outras distribuições Linux o processo de instalação pode variar.
Este manual pressupõe que o servidor de aplicação Web e o banco de dados estarão instalados no mesmo servidor. 
Neste guia, sempre que necessário editar algum arquivo, será usado o editor de texto GEDIT. Mas cabe lembrar que é apenas uma opção, existem outros editores como o VIM.
  
#4 - Passo-a-passo da Instalação

##4.1 - Instalando e configurando o Servidor WEB Apache2

Para instalar o Apache2, execute o seguinte comando:
<br>`sudo apt-get install apache2`</br>

Agora é necessário alterar o arquivo /etc/apache2/apache2.conf. Usando o gedit, é possível editar as informações desse arquivo executando o comando:
<br>`sudo gedit /etc/apache2/apache2.conf`</br>

Altere o valor do parâmetro Timeout:
<br>`Timeout 12000`</br>

Além disso, adicione as seguintes linhas ao final desse arquivo:
<br>`# linhas adicionadas para o e-cidade`</br>
<br>`LimitRequestLine 16382`</br>
<br>`LimitRequestFieldSize 16382`</br>

Agora, altere o arquivo /etc/apache2/conf.d/charset. Usando o gedit faça assim:
<br>`sudo gedit /etc/apache2/conf.d/charset`</br>

Altere o valor do parâmetro AddDefaultCharset:
<br>`AddDefaultCharset ISO-8859-1`</br>

Caso a linha desse parâmetro esteja comentada, ou seja, iniciando com o caractere '#', remova este.

Deverá ser criada uma pasta de arquivos temporários. Crie a pasta “tmp” no DOCUMENT_ROOT do Apache (/var/www), da seguinte maneira:
<br>`sudo mkdir /var/www/tmp`</br>
<br>`sudo chown -R www-data.www-data /var/www/tmp`</br>
<br>`sudo chmod -R 777 /var/www/tmp`</br>

Adicione o usuário que irá administrar o e-cidade no grupo “www-data”. Esse usuário varia de acordo com sua instalação. No caso desse manual foi criado um usuário chamado “usuario1”. Deve-se editar o seguinte arquivo:
<br>`sudo gedit /etc/group`</br>

Adicione a seguinte linha (onde “usuario1” deve ser trocado pelo seu usuário criado na instalação do Ubuntu):
<br>`www-data:x:33:usuario1`</br>
