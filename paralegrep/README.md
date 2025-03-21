###### paralegrep (C) — o programa é uma implementação multithread que realiza a busca de um termo em arquivos txt dentro do diretório `fileset` por meio das seguintes threads:

1. despachante:
    - monitora `fileset` a cada 5s para detectar alterações ou inclusões de arquivos e, caso encontre, passa o processamento às threads operárias;

2. operárias:  
    - recebem um arquivo, contam o número de ocorrências do termo definido pelo usuário e retornam esse valor à thread de ranking;

3. de ranking:
    - atualiza e exibe o ranking dos 10 arquivos com mais ocorrências do termo pesquisado, a cada 5s ou sempre que novos dados forem processados.

#### estrutura (código único — com as funções das threads, a manipulação do ranking e o monitoramento dos arquivos)

1. `ranking`: armazena os 10 arquivos com +ocorrências do termo;

2. `file_mod_times`: rastreia os tempos de modificação dos arquivos para detectar alterações.

#### how to run

- gcc -pthread -o paralegrep paralegrep.c && ./paralegrep + <palavra> (parâmetro)
    
    - e.g.: ...+ sistemas