Colocar no readme pra garantir 



# provanabor2

version: '3.8'

services:
  product-page:
    image: product-page-image
    ports:
      - "8080:8080"
  reviews-v1:
    image: reviews-v1-image
    volumes:
      - www:/ex/ex/ex/volume
  reviews-v2:
    image: reviews-v2-image
    volumes:
      - www:/ex/ex/ex/volume
  reviews-v3:
    image: reviews-v3-image
    volumes:
      - www:/ex/ex/ex/volume
  ratings:
    image: ratings-image
  details:
    image: details-image
  locust:
    image: locustio/locust
    ports:
      - "8089:8089"
    environment:
      - TARGET_URL=http://product-page-service-name



Incluir a ferramente de geração de carga(Locust) diretamente nos serviços iniciados pelo docker pode ser eficaz para avaliar o funcionamento num ambiente mais proximo do que seria um ambiente de produção real(possivel avaliar como a aplicação se comporta sob condições de carga semelhantes às que encontrará em produção), tambem uma vantagem seria  a automatização, ou seja tornando mais fácil executar testes de desempenho regularmente, tambem a questão de que cada serviço do docker e executado em seu propio conteiner oque ajuda a isolar os serviços

Em contra partida ira ter um consumo maior de recursos ,que querendo ou não ira afetar o desempenho da aplicação e possivelmente distorcer algum resultado de teste.Tambem ao adicionar uma ferramente de geração de carga diretamente no docker aumenta a complexidade da configuração.

De forma geral  a inclusão de uma ferramenta de geração de carga(como o locust) no Docker  pode ser útil para testes de desempenho, porem é importante considerar o equilíbrio entre a precisão dos testes e o uso eficiente dos recursos.
