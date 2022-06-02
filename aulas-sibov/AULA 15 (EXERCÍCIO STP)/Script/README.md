# REDE LA PASSIONE(exemplo)

## 1º Identificar qual o switch é o root primário usando "show sppanning-tree (no modo enable no switch, no meu caso vou uasr o SW3"

![SW3-STP](https://github.com/raulrsoares/aulas-sibov/blob/main/AULA%2015%20(EXERC%C3%8DCIO%20STP)/Imagens/SW3%20-%20sh%20sp.png)

## 2º Preparar o script.

## 3º Após Script Pronto vamos usalo para deixa o SW4 como root primário para todos.

SW4
![SW4-Script](https://github.com/raulrsoares/aulas-sibov/blob/main/AULA%2015%20(EXERC%C3%8DCIO%20STP)/Imagens/SW4-CONFIG.png)

3.1º E colocar as configurações nos outros sw!

SW3
![SW3-Script](https://github.com/raulrsoares/aulas-sibov/blob/main/AULA%2015%20(EXERC%C3%8DCIO%20STP)/Imagens/SW3-CONFIG.png)

SW2
![SW2-Script](https://github.com/raulrsoares/aulas-sibov/blob/main/AULA%2015%20(EXERC%C3%8DCIO%20STP)/Imagens/SW2-CONFIG.png)

SW1
![SW1-Script](https://github.com/raulrsoares/aulas-sibov/blob/main/AULA%2015%20(EXERC%C3%8DCIO%20STP)/Imagens/SW1-CONFIG.png)


## 4º Executar Ping entre o PC-Gerenciamento para os SW's

SW1
![SW1-Ping](https://github.com/raulrsoares/aulas-sibov/blob/main/AULA%2015%20(EXERC%C3%8DCIO%20STP)/Imagens/SW1-PING.png)

SW2
![SW2-Ping](https://github.com/raulrsoares/aulas-sibov/blob/main/AULA%2015%20(EXERC%C3%8DCIO%20STP)/Imagens/SW2-PING.png)

SW3
![SW3-Ping](https://github.com/raulrsoares/aulas-sibov/blob/main/AULA%2015%20(EXERC%C3%8DCIO%20STP)/Imagens/SW3-PING.png)

SW4
![SW4-Ping](https://github.com/raulrsoares/aulas-sibov/blob/main/AULA%2015%20(EXERC%C3%8DCIO%20STP)/Imagens/SW4-PING.png)


## 5º Ver a tabela do STP nos switches

SW1
![SW1 Tabela STP](https://github.com/raulrsoares/aulas-sibov/blob/main/AULA%2015%20(EXERC%C3%8DCIO%20STP)/Imagens/SW1%20-%20sh%20sp%20-%205pas.png)

SW2
![SW2 Tabela STP](https://github.com/raulrsoares/aulas-sibov/blob/main/AULA%2015%20(EXERC%C3%8DCIO%20STP)/Imagens/SW2%20-%20sh%20sp%20-%205pas.png)

SW3
![SW3 Tabela STP](https://github.com/raulrsoares/aulas-sibov/blob/main/AULA%2015%20(EXERC%C3%8DCIO%20STP)/Imagens/SW3%20-%20sh%20sp%20-%205pas.png)

SW4 - **E O SW4 VIROU O ROOT PRIMARY DE TODAS AS VLANS**
![SW4 Tabela STP](https://github.com/raulrsoares/aulas-sibov/blob/main/AULA%2015%20(EXERC%C3%8DCIO%20STP)/Imagens/SW4%20-%20sh%20sp%20-%205pas.png)
