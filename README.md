# DataSUS

Análise exploratória considerando a notícia: https://www.saude.go.gov.br/noticias/16950-governo-de-goias-mantem-leitos-instalados-no-periodo-critico-da-pandemia

Sabe-se que:
* Os leitos são cadastrados no subsistema LT do sistema CNES (Cadastro Nacional de Estabelecimentos de Saúde);
* Os dados do CNES.LT estão disponíveis publicamente no servidor FTP do DataSUS conforme exposto no endereço https://datasus.saude.gov.br/transferencia-de-arquivos/
* O dicionário de dados está disponível em ftp://ftp.datasus.gov.br/dissemin/publicos/CNES/200508_/doc/IT_CNES_1706.pdf
---
* Obs: A principal biblioteca utilizada para coleta dos dados foi o PySUS, que pode ser lida sua documentação em: https://github.com/AlertaDengue/PySUS
* Para coleta dos dados:
```
>>> import pysus.online_data.CNES as CNES # Cadastro Nacional de Estabelecimento de Saúde
>>> help(CNES.download)

Help on function download in module pysus.online_data.CNES:

download(group: str, state: str, year: int, month: int, cache: bool = True) -> pandas.core.frame.DataFrame
    Download CNES records for group, state, year and month and returns dataframe
    :param group:
        LT – Leitos - A partir de Out/2005
        ST – Estabelecimentos - A partir de Ago/2005
        DC - Dados Complementares - A partir de Ago/2005
        EQ – Equipamentos - A partir de Ago/2005
        SR - Serviço Especializado - A partir de Ago/2005
        HB – Habilitação - A partir de Mar/2007
        PF – Profissional - A partir de Ago/2005
        EP – Equipes - A partir de Abr/2007
        IN – Incentivos - A partir de Nov/2007
        RC - Regra Contratual - A partir de Mar/2007
        EE - Estabelecimento de Ensino - A partir de Mar/2007
        EF - Estabelecimento Filantrópico - A partir de Mar/2007
        GM - Gestão e Metas - A partir de Jun/2007
    :param month: 1 to 12
    :param state: 2 letter state code
    :param year: 4 digit integer

>>> df = CNES.download('LT','GO',2021,12) # Base de dados dos leitos para o estado de Goiás, em dez/21
```
