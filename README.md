```                
                            Yellow Cloaker  
    _            __     __  _ _             __          __  _     
   | |           \ \   / / | | |            \ \        / / | |    
   | |__  _   _   \ \_/ /__| | | _____      _\ \  /\  / /__| |__  
   | '_ \| | | |   \   / _ \ | |/ _ \ \ /\ / /\ \/  \/ / _ \ '_ \ 
   | |_) | |_| |    | |  __/ | | (_) \ V  V /  \  /\  /  __/ |_) |
   |_.__/ \__, |    |_|\___|_|_|\___/ \_/\_/    \/  \/ \___|_.__/ 
           __/ |                                                  
          |___/             https://yellowweb.top                 

Se você gosta deste script, POR FAVOR, DOE!
USDT TRC20: TKeNEVndhPSKXuYmpEwF4fVtWUvfCnWmra
Bitcoin: bc1qqv99jasckntqnk0pkjnrjtpwu0yurm0qd0gnqv
Ethereum: 0xBC118D3FDE78eE393A154C29A4545c575506ad6B
```

# Yellow Cloaker por [Yellow Web](https://yellowweb.top)
A versão em inglês desta ajuda está abaixo 👇 Aviso: esta ajuda está desatualizada! Agora todas as configurações são feitas usando a UI: */admin?password=12345*
**Use PHP versão 7.2 ou superior e crie certificados HTTPS para todos os seus domínios!**
# Apoiar
Se você deseja que este projeto continue a se desenvolver, [**apoie o autor com cem ou dois**!](https://t.me/yellowwebdonate_bot)

# Descrição
Um script de camuflagem modificado para arbitragem de tráfego, originalmente encontrado na vastidão do [Black Hat World](http://blackhatworld.com).
# Materiais de referência
- [ÚLTIMA stream em que TODA a interface gráfica do clo é desmontada](https://youtu.be/-ikmpq-L8ZE)
- [Stream em que o clo é analisado detalhadamente com todas as funções](https://www.youtube.com/watch?v=XMua15r2dwg&feature=youtu.be)
- [Vídeo com uma visão geral dos novos recursos aqui.](https://www.youtube.com/watch?v=x-Z2Y4lEOc0&t=656s)
- [Descrição das configurações para as primeiras versões aqui!](https://yellowweb.top/%d0%ba%d0%bb%d0%be%d0%b0%d0%ba%d0%b8%d0%bd%d0%b3-%d0%b4%d0%bb%d1%8f-%d0%b1%d0%b5%d0%b4%d0%bd%d0%be%d0%b3%d0%be-%d0%bd%d0%be-%d1%83%d0%bc%d0%bd%d0%be%d0%b3%d0%be-%d0%b0%d1%80%d0%b1%d0%b8%d1%82%d1%80/)

# Instalação
Baixe a versão mais recente de todos os arquivos deste repositório e carregue-os em sua hospedagem. Sua hospedagem deve ter **PHP versão 7.2 ou superior** habilitado e você deve **criar um certificado HTTPS para seu domínio. Sem HTTPS o clo não funcionará corretamente e a opção de simplesmente habilitar HTTPS no CloudFlare não funciona! Sim, se você usa CloudFlare, depois de ter recebido um certificado normal, habilite HTTPS no modo Full!** Posso [recomendar que você Beget hosting for clo](https://yellowweb.top/beget), é simples e conveniente e lá você pode emitir um certificado HTTPS com apenas alguns cliques.

Se você tiver procls e landings locais, crie uma pasta para cada um deles na pasta raiz clo e copie os arquivos, cada um para sua própria pasta.
*Por exemplo:*
Se você tiver 2 procls e 2 landings, crie 2 pastas para procls: p1 e p2. E duas pastas para pousos: land1, land2.

# Contexto
Para configurar o clo foi criada uma interface de usuário, disponível em: https://seu.domínio/admin?password=12345 Não se esqueça de alterar sua senha de acesso!
## Configurando o branco
Branco é uma página que é mostrada a um visitante que não passou pelos filtros clo. Estes são visitantes indesejados.

Primeiro, você precisa decidir que tipo de branco deseja usar. Clo pode:
- mostrar brancos locais
- redirecionar para qualquer outro site
- carregue o conteúdo de qualquer outro site via CURL
- retornar qualquer código HTTP (por exemplo, erro 404 ou apenas 200)

Depois de decidir, altere o valor para um dos seguintes:

### Página em branco local de uma pasta
Isto é para os brancos locais. Você deve criar uma pasta na raiz do clo, por exemplo *white* e copiar todos os arquivos brancos lá. Em seguida, escreva o nome da pasta no campo apropriado
### Redirecionar
Isso redireciona todo o tráfego branco para outro site. Digite o endereço do site e selecione o tipo de redirecionamento. Pode ser: 301.302.303 ou 307. Pesquise no Google a diferença se for importante para você.
###Enrolar
Isto serve para carregar conteúdo de qualquer outro site. Escrevemos o endereço do site no campo apropriado.
### Retorna o código HTTP
Você pode retornar qualquer erro HTTP para tráfego branco. Por exemplo: *404*. Ou codifique *200* para mostrar uma página em branco.

## Brancos individuais para diferentes domínios
Se você tiver vários domínios (ou subdomínios) vinculados à sua hospedagem e enviar tráfego para eles, poderá garantir que diferentes brancos sejam mostrados para domínios diferentes, alterando a configuração apropriada.

Em seguida, preencha os campos. O formato é:
`seu.domínio => whiteaction:value`
Por exemplo:
`https://meudominio.com => curl:https://ya.ru`
Todos os valores possíveis de ação branca: *pasta, curl, redirecionamento, erro*


## Configurando um funil
Clo pode trabalhar com os seguintes funis:
- pouso local (ou vários pousos)
- prokla local (prokly) -> desembarques locais
- golpes locais + redirecionamento para uma página de destino em outro site
- redirecionar imediatamente para outro site

Vejamos todas essas configurações.
### Desembarques locais
Você pode usar uma ou mais páginas de destino. O tráfego será dividido igualmente entre eles. Digamos que para dois pousos seja 50/50. Cada pouso deve estar em sua própria pasta. Definimos **"Não usar pré-aterrissagem"**, e o método de carregamento da página de destino é **"Destino local da pasta"** Se houver várias páginas de destino, use uma vírgula como separador. Por exemplo:
`terreno1,terreno2`

### Procls locais - Desembarques locais
Faça o mesmo que no parágrafo sobre **Desembarques locais** mas preencha também o campo **"Pastas onde estão localizados os pré-pousos"**. Por exemplo, para dois procl:
`p1,p2`
### Golpes locais + redirecionamento
Preencha os nomes das pastas. Por exemplo, para dois procl:
`p1,p2`
Em seguida, substitua **"Método de carregamento de destino"** por *Redirect*. Última etapa: preencha o endereço de redirecionamento.
### Redirecionamento imediato
Se você deseja apenas redirecionar todo o tráfego que passa pelos filtros clo, use **$black_action = *'redirect'*** e preencha o endereço de redirecionamento **$black_redirect_url**. Selecione também o tipo de redirecionamento: 301.302.303 ou 307. Pesquise no Google a diferença se isso for importante para você. Insira o tipo de redirecionamento em **$black_redirect_type**.
### Configurando um script de conversão de destino local
Cada landing tem a capacidade de enviar leads para PP (cap!). E cada PP tem sua própria mecânica de envio desses mesmos leads.
Por padrão, clo procura o arquivo *order.php* localizado na pasta inicial. Se o seu script de software tiver um nome diferente, renomeie o valor na variável **$black_land_conversion_script**. Para entender como é chamado o script de envio, abra o arquivo de índice de destino e procure qualquer formulário - *<formulário*. Observe o atributo *action* do formulário. O roteiro está escrito nele. Se não houver nenhum atributo *action*, então o lead está enviando um arquivo de índice!
Se o script estiver localizado em uma pasta, insira o caminho relativo para o script, por exemplo:
`$black_land_conversion_script='pasta/conversion.php';`
Depois de ter tudo configurado, envie um líder de teste. Se o lead não estiver na estatística PP, abra o script de envio do lead e procure a linha
`sair();`
Se houver, exclua ou comente essas linhas (levando em consideração a sintaxe da linguagem!!!).
### Configuração da página Obrigado.
O visitante chega à página de agradecimento depois de enviar seus dados em preto *ou branco*! O conteúdo da página é carregado da pasta *obrigado* clo. Se você olhar, ele contém vários arquivos html denominados códigos de idioma de duas letras. Insira o idioma desejado da página de agradecimento em **$thankyou_page_language**.

Se não houver uma página de agradecimento para o seu idioma, crie uma. É simples: carregue a versão em inglês da página de agradecimento no navegador Chrome e use o tradutor integrado para traduzi-la para o idioma desejado. Em seguida, salve a tradução com o nome desejado, por exemplo *IT.html*.
**Atenção**: Abra a página traduzida em um editor de texto e certifique-se de que as 2 macros *{NAME}* e *{PHONE}* NÃO foram traduzidas. Se houvesse, devolva-os ao seu lugar!

Se você quiser usar sua própria página de agradecimento, renomeie-a com um código de idioma de duas letras e coloque todos os arquivos necessários na pasta *obrigado*.
#### Coletando correspondência na página de agradecimento
Na página de agradecimento por padrão existe um formulário para coleta de endereços de e-mail. Caso não precise, basta removê-lo no código da página. Mas se necessário, então você precisa criar outra página: aquela para a qual o usuário irá DEPOIS de deixar seu e-mail. Deve ser nomeado como o nome de duas letras do idioma + email.html. Por exemplo: *SKemail.html*. Há um exemplo de tal página na pasta *obrigado*.

## Configurações de pixels
Você pode adicionar vários pixels aos seus anúncios e páginas de destino. Aqui está a lista completa:
- Yandex Métrica
- Gerenciador de tags do Google
- Pixel do Facebook

### Yandex Métrica
Para adicionar o script Yandex Metrics às suas pré-landing pages e landing pages, basta preencher o ID da métrica em **$ya_id**.
### Gerenciador de tags do Google
Para adicionar o script do Gerenciador de tags do Google às suas pré-landing pages e landing pages, basta preencher o ID do GTM em **$gtm_id**.
### Pixel do Facebook
FB clo obtém o ID do pixel do link. Deve estar no formato: *px=1234567890*. Por exemplo:
`https://seu.domínio?px=5499284990`
Se o endereço contiver o parâmetro *px*, clo adicionará o código Javascript completo do pixel fb à página de agradecimento. Você pode definir o evento de pixel desejado na variável **$fb_thankyou_event**. Por padrão é *Lead*, mas você pode alterá-lo para *Purchase* ou qualquer outra coisa.
Você também pode usar o evento *PageView*. Para habilitá-lo, altere **$fb_use_pageview** para *true*. Depois disso, o código do pixel será adicionado a todas as páginas principais e landing pages e essas páginas enviarão um evento *PageView* ao Facebook para cada visitante.
**Observação:** Use o plug-in *Facebook Pixel Helper* para Google Chrome para verificar se os eventos são enviados corretamente!
## Configurando filtros clo
Klo pode filtrar o tráfego usando os seguintes critérios:
- Base IP integrada
- sistema operacional do visitante
- País do visitante
- Agente de usuário visitante (navegador)
- ISP (provedor) do visitante
- Disponibilidade de referenciador
- Para qualquer parte do link que foi seguido

*Nota:* Sempre que você quiser usar vários parâmetros, use uma vírgula como separador!
Primeiro, adicione todos os sistemas operacionais permitidos a **$os_white**. Aqui está a lista dos disponíveis:
-Android
-iOS
-Windows
-Linux
- OS X
- e outros não muito populares...

Selecione os que você precisa.
Em seguida, preencha todos os códigos de país de duas letras permitidos em **$country_white**. Por exemplo: *RU,RS,IT,ES*.

Agora livre-se de todos os ISPs desnecessários. Adicione-os a **$isp_black**. Por exemplo: *google,facebook,yandex*. Se você deseja proteger seu pacote de serviços espiões, adicione todos os provedores de nuvem aqui, como: *amazon, azure*, etc.

Adicione palavras à lista de User Agents proibidos **$ua_black** pelos quais serão filtrados.
Por exemplo: *facebook,Facebot,curl,gce-spider*

Adicione uma lista de palavras que podem estar no link que o visitante seguiu que sinalizam que ele precisa mostrar branco em **$tokens_black** ou deixe esta variável vazia - ''.

Se você tiver adicional lista de endereços IP dos quais você deseja se livrar - adicione-os a **$ip_black**.

E finalmente: se você deseja bloquear visitantes *diretos*, altere **$block_without_referer** para *true*. **Atenção**: Alguns sistemas operacionais e navegadores não transferem o referenciador corretamente ou nem o transferem. Portanto, se você quiser usar esse truque, teste-o primeiro em uma pequena quantidade de tráfego, caso contrário, você poderá perder $$.

## Configurando distribuição de tráfego
Você pode desligar temporariamente todos os filtros clo e enviar todo o tráfego para branco. Por exemplo, durante a moderação. Para fazer isso, altere **$full_cloak_on** para *true*.
Você também pode desligar todos os filtros clo e enviar todo o tráfego para preto. Por exemplo, para testar o preto. Para fazer isso, altere **$disable_tds** para *true*.
Você pode salvar o “caminho” do usuário (ou seja, aqueles pré-landes e landing pages para os quais ele chega no funil). Então ele sempre verá, não importa quantas vezes faça login, as mesmas páginas. Para fazer isso, altere **$save_user_flow** para *true*.
## Configurando estatísticas e postback
A visualização das estatísticas é protegida por senha. Defina-o na variável **$log_password**.
Se você sempre nomear seus criativos da mesma forma e transferir seus nomes para clo de sua origem de tráfego, na página de estatísticas você poderá ver quantos cliques houve de um determinado criativo. Para isso, defina o nome do parâmetro no qual são passados ​​os nomes dos creos na variável **$creative_sub_name**. Por exemplo, se o link na origem do tráfego for assim:
`https://seu.domínio?meunome=greatcreo`
então você precisa alterar a variável assim:
`$creative_sub_name = 'meunome';`
depois disso você verá no artigo:
*ótimocreo - 154 cliques*
### Configurando postback
Klo pode receber postbacks do PP e mostrar o status dos leads nas estatísticas. Primeiro, você precisa transferir o ID exclusivo do visitante – subid – para o PP. O Subid é criado automaticamente para cada visitante e armazenado em cookies. Você deve perguntar ao seu gerente como passar o subid para o PP (eles geralmente conhecem esse parâmetro sob o nome clickid). Deixe-os dizer em qual subtag você precisa transferi-lo, porque PPs diferentes têm subtags diferentes. Para alguns eles são chamados de *sub1* *sub2*, etc., e em algum lugar *subacc*, em algum outro lugar. Por exemplo, vamos imaginar que o sub-rótulo se chama *sub1*. O array **$sub_ids** é responsável por passar parâmetros para o PP. Vamos mudar o nome à direita de *subid* para *sub1*:
`$sub_ids = array("subid"=> "sub1", .....);`
É assim que configuramos o clo para pegar o valor do cookie *subid* e passá-lo para o rótulo *sub1*. Se, digamos, *subid* for *12uion34i2* o resultado será:
- se houve um pouso local, um campo de entrada oculto será adicionado a todos os formulários de pouso
`<tipo de entrada = "nome oculto" = "sub1" valor = "12uion34i2"`
- se tivermos um redirecionamento, será: `http://redirect.link?sub1=12uion34i2`

A seguir, precisamos indicar no PP para onde enviar o postback. Em clo, o arquivo *postback.php* é responsável por processar postbacks. Precisamos obter 2 parâmetros do PP: *subid* e status do lead. Usando essas duas coisas, clo altera o status do lead em seus logs e exibe a alteração nas estatísticas.
Consulte a ajuda do PP ou pergunte ao seu gerente qual macro o PP usa para transferir o status do lead. Geralmente é chamado *{status}*. Voltando ao nosso exemplo: como enviamos *subid* no sub-rótulo *sub1*, a macro para obter *subid* do PP seria *{sub1}*. Vamos criar um endereço de postback completo. Você deve colá-lo no campo Postback Url do seu PP. Por exemplo:
`https://seu.domínio/postback.php?subid={sub1}&status={status}`
E por fim, descubra você mesmo ou pergunte ao gerente quais status o PP envia no postback. Geralmente isso é:
-Liderar
- Comprar
-Rejeitar
- Lixo

Caso o seu PP envie status de forma diferente, então corrija os valores das seguintes variáveis ​​de acordo com as configurações do PP:
- **$lead_status_name**
- **$purchase_status_name**
- **$reject_status_name**
- **$trash_status_name**

Após a configuração, envie um lead de teste e na página Leads nas estatísticas observe como o lead muda seu status para Lixo.

## Configurando scripts adicionais
### Desativando o botão Voltar
Você pode desativar o botão Voltar no navegador do visitante para evitar que ele saia da sua página. Para fazer isso, altere **$$disable_back_button** para *true*.
### Substituindo o botão "Voltar"
Você pode alterar o endereço para onde o visitante será direcionado clicando no botão “Voltar”. Este recurso pode ser usado para pré-monetização e para direcionar o visitante para outra oferta. Altere **$replace_back_button** para *true* e insira o endereço em **$replace_back_address**.
**Atenção:** Não use este script junto com o script **Desativar botão Voltar**!!!
### Proibição do menu de contexto, seleção de texto e salvamento usando Ctlr+S
Você pode desativar a capacidade de selecionar texto em seus pré-aterrissagens e landings, desativar a capacidade de salvar a página usando as teclas Ctrl+S e também desativar o menu de contexto do navegador. Para fazer isso basta alterar **$disable_text_copy** para *true*.
### Substituindo a pré-landing page por outro site
Você pode ativar essa configuração para que a página de destino seja aberta em uma nova guia do navegador e o site seja substituído por outro site. Isso pode ser usado para pré-monetizar o tráfego. Para ativar, altere **$replace_prelanding** para *true* e insira o endereço em **$replace_prelanding_address**.
### Máscaras de telefone
Você pode configurar o clone para aplicar determinadas máscaras aos campos de entrada de números de telefone. Ao ativar esse recurso, o visitante não poderá inserir letras no número e não poderá inserir mais ou menos números do que o necessário. A máscara especifica prefixos telefônicos, número de dígitos e separadores. Para ativar máscaras, altere **$black_land_use_phone_mask** para *true* e edite a própria máscara em **$black_land_phone_mask**.
# Exame
Adicione o código do seu país à lista de permitidos para poder mudar para preto. Analise todos os elementos do funil. Verifique o pixel e toque de leads no PP, postback.
# Veja tráfego e estatísticas
Depois de começar a despejar, você pode visualizar as estatísticas de tráfego na página Estatísticas:
`https://seu.domínio/logs?password=suasenha`
onde *yourpassword* é o valor da variável **$log_password** do arquivo *settings.php*.
# Integração JS de clo com construtores
`<script src = 'https://seu.domínio/js/index.php'></script>`
# Contatos
Para qualquer dúvida, escreva Issues no GitHub ou na página pública http://vk.com/yellowweb

# Descrição
Script de cloaking modificado para marketing de afiliados encontrado em algum lugar no [Black Hat World](http://blackhatworld.com).
Se você gosta deste software, [doe alguns dólares usando este bot do Telegram!](https://t.me/yellowwebdonate_bot)
# Instalação
Basta baixar a cópia mais recente de todos os arquivos deste repositório e carregá-los em sua hospedagem. Sua hospedagem deve permitir a execução de scripts PHP e você DEVE criar um certificado HTTPS para o seu domínio. **Sem HTTPS o cloaker não funcionará corretamente!** Definitivamente posso [recomendar Beget Hosting para o cloaker](https://yellowweb.top/beget). É barato e conveniente.

Se você tiver pré-desembarques ou desembarques locais, crie uma pasta para cada um deles na pasta raiz do cloaker e copie todos os arquivos lá de acordo.
*Por exemplo:*
Se você tiver 2 pré-desembarques e 2 desembarques, crie 2 pastas para pré-desembarques: p1 e p2. E 2 pastas para pousos: land1, land2.

#Configurar
No momento, o cloaker não possui nenhuma interface de usuário para as configurações. Então, basta abrir o arquivo settings.php em qualquer editor de texto. Eu recomendo o Notepad++ para isso, pois ele possui destaque de sintaxe PHP e será mais fácil de ler e editar.

## Configuração da página em branco
White Page é uma página que é mostrada ao visitante, que não passa por nenhum filtro do cloaker. Então é para visitantes que a gente não quer.

Primeiro, você precisa decidir que tipo de ação de página branca você quer usar. O cloaker pode usar páginas brancas locais, pode mostrar qualquer outro site como uma página branca (sem redirecionamentos), pode redirecionar tráfego branco para qualquer site e também pode mostrar um erro para esses visitantes.

Quando você decidir, altere o valor **$white_action** para um dos seguintes:
### site
Isto é para páginas brancas locais. Você precisa criar uma pasta no diretório raiz do cloaker, por exemplo: *white* e copiar todos os arquivos da sua página branca para lá. Então escreva o nome da pasta no valor **$white_folder_name**.
### redirect
Escolha isto, se você quiser redirecionar todo o tráfego branco. Basta digitar a URL completa do site em **$white_redirect_url** e também escolher um tipo de redirecionamento. Pode ser 301,302,303 ou 307. Pesquise a diferença no Google se precisar. Insira o valor em **$white_redirect_type**.
### curl
Use-o se quiser carregar o conteúdo de qualquer outro site em seu domínio sem redirecionamentos. Insira a URL completa do site em **$white_curl_url**.
### error
Você pode retornar qualquer tipo de erro HTTP para todo o tráfego branco. Por exemplo: *404*. Basta inserir o código de erro em **$white_error_code**.

## Páginas brancas específicas de domínio
Se você tiver VÁRIOS domínios (ou subdomínios) estacionados em sua hospedagem e executar tráfego para todos eles, poderá escolher usar diferentes ações brancas para diferentes domínios. Para fazer isso, primeiro altere **$white_use_domain_specific** para *true*.

Em seguida, preencha o array **$white_domain_specific**. O formato é assim
`"your.domain" => "whiteaction:value"`
Um exemplo é fornecido no arquivo settings.php padrão.
## Configuração da página Money
A página Money (chamada de Black page aqui) pode ser uma das seguintes:
- landing page(s) local(ais)
- prelanding(s) local(ais) + landing(s) local(ais)
- prelanding(s) local(ais) + redirecionamento para a landing da rede aff
- redirecionamento

Vamos mergulhar em cada uma dessas configurações.
### Landing page(s) local(ais)
Você pode usar uma ou várias landing pages se precisar. O tráfego será distribuído proporcionalmente. Por exemplo, 50-50 para 2 landings. Cada landing deve estar em uma pasta separada. Faça **$black_action = *'site'*** e coloque o nome da pasta em **$black_land_folder_name**. No caso de landings múltiplos, use vírgula como separador. Por exemplo:
`$black_land_folder_name = 'land1,land2';`
*Observação:* certifique-se de verificar se você não tem nada em **$black_preland_folder_name**. Deve ser:
`$black_preland_folder_name = ''; `
### Pré-aterrissagem(ões) local(ais) + aterrissagem(ões) local(ais)
Faça tudo igual à descrição para **Página de aterrissagem local**, mas também preencha o **$black_preland_folder_name**. Por exemplo, para duas aterrissagens:
`$black_preland_folder_name = 'p1,p2';`
### Pré-aterrissagem(ões) local(ais) + redirecionamento
Preencha o **$black_preland_folder_name**. Por exemplo, para duas aterrissagens:
`$black_preland_folder_name = 'p1,p2';`
Então altere **$black_land_use_url** para *true*. Última etapa: coloque a URL de redirecionamento completa int **$black_land_url**
### Redirecionar
Se você quiser apenas redirecionar todo o seu tráfego preto, use **$black_action = *'redirect'*** e coloque a URL completa do site para onde você quer redirecionar as pessoas **$black_redirect_url**. Escolha também um tipo de redirecionamento. Pode ser 301,302,303 ou 307. Pesquise a diferença no Google se precisar. Insira o valor em **$black_redirect_type**.
### Configurando o script de conversão da landing page local
Cada landing page tem a capacidade de enviar leads para sua rede de afiliados. E cada rede de afiliados que fornece essas landing pages tem seu próprio script e mecânica para enviar essas informações.
Por padrão, o cloaker procurará o arquivo *order.php*, que deve estar localizado na pasta da landing. Mas se seu script tiver um nome diferente, você deve renomear o valor de **$black_land_conversion_script**. Se o seu script estiver em alguma pasta, coloque o nome desta pasta antes do nome do script assim:
`$black_land_conversion_script='folder/conversion.php';`
Após configurar isso, envie um lead de teste para sua rede aff. Se você não conseguir ver o lead nas estatísticas da sua rede, abra seu script de conversão e procure por este tipo de linha:
`exit();`
Remova ou comente todas elas. Em seguida, envie um lead de teste novamente.
### Configurando a página "Obrigado"
A página de agradecimento é uma página para onde o visitante é redirecionado após preencher o formulário de lead em sua black landing OU em sua whitepage (se você tiver uma lá). O conteúdo da página de agradecimento é carregado da pasta *thankyou* do cloaker. Ela tem vários arquivos html lá, nomeados após o código de idioma de 2 símbolos. Coloque o nome do idioma necessário em **$thankyou_page_language**.

Se não houver uma página de agradecimento para seu idioma - crie uma! É tão fácil quanto carregar, por exemplo, *EN.html* em seu navegador Chrome, traduzi-lo usando o Google Translate integrado e salvá-lo usando seu código de idioma. Por exemplo: *IT.html*.
**Aviso**: certifique-se de que duas macros: *{NAME}* e *{PHONE}* não foram traduzidas pelo Google. Se foram, basta alterá-las de volta.

Se você quiser usar sua própria página de agradecimento, basta renomeá-la usando o mesmo código de idioma de 2 símbolos para o idioma necessário e colocar todos os seus arquivos na pasta *thankyou*.
#### Coletando e-mails na página "Obrigado"
A página de agradecimento padrão tem um formulário de coleta de e-mail integrado. Se você não precisar dele, basta excluí-lo do código. Mas se precisar, você precisa criar mais uma página: aquela para a qual o visitante será redirecionado DEPOIS de enviar o formulário de e-mail. Ela deve ser chamada usando o mesmo código de idioma de 2 símbolos + e-mail no final. Por exemplo: *SKemail.html*.

## Configuração de pixels
Você pode adicionar vários pixels em seus prelandings e landings. A lista completa inclui:
- Yandex Metrika
- Google Tag Manager
- Facebook Pixel

### Yandex Metrika
Para adicionar o script do Yandex Metrika aos seus prelandings e landings, basta preencher seu ID do Yandex Metrika. Coloque-o em **$ya_id**.
### Gerenciador de tags do Google
Para adicionar o script do Gerenciador de tags do Google aos seus prelandings e landings, basta preencher seu ID do GTM. Coloque-o em **$gtm_id**.
### Pixel do Facebook
O ID do Pixel do Facebook é obtido do link que você colocou na sua fonte de tráfego. Ele deve estar no formato *px=1234567890*. Por exemplo:
`https://seu.domínio?px=5499284990`
Se a URL tiver este parâmetro *px*, o código javascript completo do Pixel do Facebook será adicionado à página de agradecimento. Você pode definir o evento do Pixel do Facebook na variável **$fb_thankyou_event**. Por padrão, é *Lead*, mas você pode alterá-lo para *Purchase* ou qualquer coisa que precisar.
Você também pode usar o evento *PageView* do pixel. Para fazer isso, altere **$fb_use_pageview** para *true*. Se você fizer isso, o código do pixel será adicionado a todos os seus prelandings e landings locais e eles enviarão o evento *PageView* para cada visitante do Facebook.
Use o plugin Facebook Pixel Helper para Google Chrome para verificar se o evento do pixel dispara corretamente!
## Configuração dos filtros do Cloaker
O cloaker pode filtrar o tráfego com base em:
- Banco de dados de IP integrado
- SO do visitante
- País do visitante
- Agente do usuário do visitante
- ISP do visitante
- Referente do visitante
- Qualquer token na URL

*Observação:* a vírgula deve ser usada em todos os lugares onde vários valores são necessários.
Primeiro, coloque todos os sistemas operacionais que devem ter permissão para visualizar a página preta em **$os_white**. A lista completa é:
- Android
- iOS
- Windows
- Linux
- OS X
- e alguns outros não significativos

Escolha qualquer um que você precisar.
Em seguida, coloque todos os códigos de país que são permitidos em **$country_white**. Por exemplo: *RU,RS,IT,ES*.

Agora livre-se de todos os provedores de serviços de Internet dos quais você não precisa. Coloque-os em **$isp_black**. Por exemplo: *google,facebook,yandex*. Se você quiser proteger seus landings de serviços Spy, use *amazon,azure* e outros provedores de nuvem aqui.

Coloque todos os User Agents desnecessários em **$ua_black**.
Por exemplo: *facebook,Facebot,curl,gce-spider*

Coloque todas as palavras que podem ser encontradas na URL que sinalizam que este visitante deve ver a página branca em **$tokens_black** ou deixe-a vazia.

Se você tiver algum endereço IP adicional do qual deseja se livrar, coloque-o em **$ip_black**.

E por último, mas não menos importante: se você quiser bloquear visitantes *diretos* de ver sua página preta, altere **$block_without_referer** para *true*. **Aviso**: alguns sistemas operacionais e navegadores não passam o referenciador corretamente, então teste isso primeiro em uma pequena quantidade de tráfego ou você perderá dinheiro.

## Configuração de Distribuição de Tráfego
Você pode desabilitar temporariamente todos os seus filtros e enviar todo o tráfego para a página branca. Por exemplo, você pode usá-lo para moderação. Para fazer isso, altere **$full_cloak_on** para *true*.
Você também pode desabilitar os filtros e sempre mostrar a página preta. Por exemplo, para fins de teste. Para fazer isso, altere **$disable_tds** para *true*.
Você pode salvar o fluxo do usuário (os prelandings e os landgins que serão mostrados ao visitante) para que ele sempre veja as mesmas páginas quando visitar o site pela segunda vez ou até mesmo atualizar a página. Para fazer isso, altere **$save_user_flow** para *true*.
## Configuração de Estatísticas e Postback
Suas estatísticas são protegidas com uma senha, para defini-la, preencha a variável **$log_password**.
Se você nomear seus criativos corretamente e passar seus nomes da fonte de tráfego, você pode ver o número de cliques para cada um dos criativos nas Estatísticas. Para fazer isso, coloque o nome do parâmetro no qual você passa o nome criativo na variável **$creative_sub_name**. Por exemplo, se seu link se parece com isso:
`https://your.domain?mycreoname=greatcreo`
então você precisa fazer assim:
`$creative_sub_name = 'mycreoname';`
### Configuração de postback
O cloaker é capaz de receber postbacks da sua rede aff. Para fazer isso, primeiro você precisa passar o id do visitante único (chamado de subid aqui) para sua rede. O subid é criado para cada visitante e é armazenado em um cookie. Você deve perguntar ao seu gerente aff, como você deve passar esse id (eles o conhecem como "clickid") e qual subparâmetro você deve usar. Normalmente, isso é feito usando subparâmetros como *sub1* ou *subacc*. Vamos ficar com *sub1* para este exemplo. Então, devemos editar o array **$sub_ids**, a parte que tem *subid* no lado esquerdo para ficar assim:
`$sub_ids = array("subid"=> "sub1", .....);`
Dessa forma, dizemos ao cloaker para pegar o valor de *subid* e adicioná-lo a todos os formulários na landing na forma de *sub1* (ou adicioná-lo ao seu link de redirecionamento, se você não tiver uma landing local). Então, se o *subid* fosse *12uion34i2*, teríamos:
- no caso de landing local
`<input type="hidden" name="sub1" value="12uion34i2"`
- no caso de redirecionamento `http://redirect.link?sub1=12uion34i2`

Agora precisamos dizer à rede aff para onde enviar as informações de postback. O cloaker tem o arquivo *postback.php* em sua pasta raiz. É o arquivo que recebe e processa postbacks. Precisamos receber 2 parâmetros da rede aff: *subid* e status do lead. Usando essas duas coisas, podemos alterar o status do lead em nossos logs e mostrar essa alteração nas estatísticas.
Procure na ajuda ou pergunte ao seu gerente: quais macros sua rede usa para enviar *status*, geralmente é chamado da mesma forma: *{status}*. Então, voltando ao nosso exemplo: enviamos *subid* em *sub1*, então as macros para receber de volta nosso *subid* serão *{sub1}*. Vamos criar uma URL de postback completa. Você deve colocar essa URL no campo Postback da sua rede Aff. Por exemplo:
`https://your.domain/postback.php?subid={sub1}&status={status}`
Agora, pergunte ao seu gerente aff ou procure na seção de ajuda deles, quais são os status que eles nos enviam no postback. Geralmente eles são:
- Lead
- Purchase
- Reject
- Trash

Se sua rede aff usa outros status, então altere esses valores de variáveis ​​de acordo:
- **$lead_status_name**
- **$purchase_status_name**
- **$reject_status_name**
- **$trash_status_name**

Depois de configurar isso, envie um lead de teste e observe na página Leads como o status muda para *Trash* depois de um tempo.


## Configuração de scripts adicionais
### Desabilitar botão Voltar
Você pode desabilitar o botão Voltar no navegador do visitante, para que ele não possa sair da sua página. Para fazer isso, altere **$$disable_back_button** para *true*.
### Substituir botão Voltar
Você pode substituir a URL do botão Voltar no navegador do visitante. Assim, depois que ele clicar nele, ele será redirecionado para outro lugar, por exemplo, para outra oferta. Para fazer isso, altere **$replace_back_button** para *true* e coloque a URL que você deseja em **$replace_back_address**.
**Aviso:** Não use este script com o script **Desabilitar botão Voltar**!!!
### Desabilitar seleção de texto, Ctrl+S e menu de contexto
Você pode desabilitar a capacidade de selecionar texto em suas pré-aterrissagens e aterrissagens, desabilitar a capacidade de salvar a página usando as teclas Ctrl+S e também desabilitar o menu de contexto do navegador. Para fazer isso, basta alterar **$disable_text_copy** para *true*.
### Substituindo Prelanding
Você pode fazer o cloaker abrir a landing page em uma aba separada do navegador e então redirecionar a aba com o prelanding para outra url. Depois que o usuário fechar sua aba de landing page, ele verá a aba com essa url. Use-a para mostrar outra oferta ao usuário. Para fazer isso, altere **$replace_prelanding** para *true* e coloque sua url em **$replace_prelanding_address**.
### Máscaras de telefone
Você pode dizer ao cloaker para usar máscaras para o campo de telefone em suas landings locais. Quando você fizer isso, o visitante não poderá adicionar nenhuma letra no campo de telefone, apenas números. A máscara define a contagem de números e delimitadores. Para habilitar máscaras, basta alterar **$black_land_use_phone_mask** para *true* e editar sua máscara em **$black_land_phone_mask**.
# Check Up
Adicione seu próprio país aos filtros do cloaker para poder ver a página negra. Em seguida, passe por todos os componentes do funil. Envie um lead de teste, verifique se ele chegou à sua rede aff.
# Tráfego em execução e estatísticas
Depois de começar a executar o tráfego, você pode monitorá-lo e também olhar as estatísticas. Para fazer isso, basta acessar um link como este:
`https://your.domain/logs?password=yourpassword`
onde *yourpassword* é um valor de **$log_password** do arquivo settings.php.

# Integração Javascript
Você pode conectar este cloaker a qualquer site ou construtor de sites que permita adicionar Javascript. Por exemplo: *GitHub, Wix, Shopify* e assim por diante.
Quando você faz isso, você executa o tráfego para o construtor de sites e depois que o visitante chega a este site, um pequeno script verifica se ele tem permissão para visualizar a página negra. Se (ele) estiver, então 2 coisas podem acontecer:
- Um redirecionamento para sua blackpage
- O conteúdo do construtor de sites é substituído pela blackpage

## Redirecionamento
Basta adicionar este script ao seu construtor de sites:
`<script src="https://your.domain/js/indexr.php"></script>`

## Conteúdo substituindo
Basta adicionar este script ao seu construtor de sites:
`<script src="https://your.domain/js"></script>`
Não use este método se você tiver apenas landings sem prelandings!
# Detalhes técnicos
## Componentes usados
Este cloaker usa:
- Bancos de dados MaxMind para detecção de ISP, país e cidade
- Faixas de IP de bot de várias fontes coletadas de toda a Internet em formato CIDR
- Sinergi BrowserDetector para (surpresa!) detecção de navegador
- IP Utils do Symphony para verificar se o endereço IP está em um intervalo selecionado
- Ícones de https://www.flaticon.com/free-icons/question

## Fluxo de tráfego
Depois que o visitante passa pelos filtros do cloaker, ele geralmente vê o prelanding (se você tiver um). No prelanding, todos os links estão sendo substituídos pelo link para o script *landing.php*. Depois que o visitante clica no link, o script *landing.php* obtém o conteúdo do landing, substitui a ação de todos os formulários para *send.php*, adiciona todos os scripts adicionais e mostra o conteúdo ao visitante. Quando o visitante preenche o formulário e o envia, *send.php* chama o script de envio original e então remove todos os redirecionamentos dele. Depois disso, *send.php* redireciona para *thankyou.php* que mostra a página de agradecimento conforme descrito nas seções acima.
