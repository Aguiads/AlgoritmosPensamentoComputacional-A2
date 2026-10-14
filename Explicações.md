#include<stdio.h> <br>
#include<ctype.h> 
```
-stdio.h serve para importar as funções de entrada e saída padrão da linguagem C para o seu código.
-ctype.h analisa caracteres simples (do tipo char). Ela permite que você descubra se uma letra é maiúscula, se um caractere é um número, ou mude o formato de uma letra de forma muito simples.
```
int main() { <br>
    float preco_unitario, imposto, transporte, seguro, <br>
    preco_final; <br>
    float total_impostos = 0; <br> 
    int pais_origem; <br>
    char meio_transporte, carga_perigosa;
```
-2 float no começo porque vão ser numeros quebrados,serve para declarar variáveis que armazenam números com ponto decimal números reais,conhecidos como ponto flutuante.
-1 Int para numeros inteiros ele vai servir apenas para selecionar os paises
-1 char para declarar variáveis que armazenam um único caractere como uma letra, um número isolado ou um símbolo
```
while (1) { <br>
    printf("\n--- Entrada de Dados do Produto ---\n"); <br>
    printf("Digite o preço unitário (menor ou igual a 0 para sair): R$ "); <br>
    scanf("%f", &preco_unitario);

if (preco_unitario <= 0) { <br>
break; <br>
}
```
-O comando while (1) serve para criar um loop infinito, ou seja, um bloco de código que vai ficar se repetindo para sempre, a menos que você force a interrupção dele
-O numero (1) que esta na frente do while significa verdadeiro, se fosse (0) seria falso a utilidade de ser verdadeiro ou falso que chamamos de lógica booleana é que ela funciona como os trilhos de um trem: é isso que permite ao seu programa tomar decisões e seguir caminhos diferentes dependendo da situação
-O printf serve para exibir dados na tela e o scanf serve para ler dados que o usuario digita no teclado
-E por fim o comando break serve para interromper e sair imediatamente de um bloco de repetição
```
printf("Digite o país de origem (1 - EUA; 2 - México; 3 - Outros): "); <br>
scanf("%d", &pais_origem);
```
-Essa parte exibe um menu numérico para o usuário e salva a resposta na variável pais_origem. Como é um número inteiro (1, 2 ou 3), o código usa a tag %d
```
printf("Digite o meio de transporte (T - Terrestre; F - Fluvial; A - Aéreo): "); <br>
scanf(" %c", &meio_transporte); <br>
meio_transporte = toupper(meio_transporte);
```
-O toupper: Essa função (que vem daquela biblioteca #include <ctype.h>) transforma a letra digitada em maiúscula. Se o usuário digitar um 't' minúsculo, o programa converte automaticamente para 'T', evitando erros nas próximas checagens do código
```
printf("Carga perigosa? (S - Sim; N - Não): "); <br>
scanf(" %c", &carga_perigosa); <br>
carga_perigosa = toupper(carga_perigosa);
```
-Segue a mesma lógica anterior: lê um único caractere (S ou N) e garante que ele fique em letra maiúscula usando o toupper
```

if (preco_unitario <= 100.00) { <br>
imposto = preco_unitario * 0.05; // 5% <br>
} else { <br>
imposto = preco_unitario * 0.10; // 10% <br>
} <br>
total_impostos += imposto;
```
-O objetivo desse bloco é cobrar menos imposto de produtos baratos e mais imposto de produtos caros. O limite que divide os dois casos é o valor de R$ 100,00
```
transporte = 0; <br>
if (carga_perigosa == 'S') { <br>
if (pais_origem == 1) transporte = 50.00; <br>
else if (pais_origem == 2) transporte = 21.00; <br>
else if (pais_origem == 3) transporte = 24.00; <br>
} <br>
else if (carga_perigosa == 'N') { <br>
if (pais_origem == 1) transporte = 12.00; <br>
else if (pais_origem == 2) transporte = 21.00; <br>
else if (pais_origem == 3) transporte = 60.00; <br>
}
```
-Essa parte do código serve para definir o valor do frete (transporte) com base em duas regras combinadas: se a carga é perigosa e qual é o país de origem.
-Se o usuário digitou 'S' (Sim) para carga perigosa, o computador entra apenas nesse primeiro bloco de chaves Lá dentro, ele olha o número do país de origem:
	• Se for 1 (EUA), o transporte vira R$ 50,00.
	• Se for 2 (México), o transporte vira R$ 21,00.
	• Se for 3 (Outros), o transporte vira R$ 24,00.
-Se o usuário digitou 'N' (Não) para carga perigosa, o computador ignora completamente a Etapa 1 e pula direto para esse else if. Aqui dentro, ele aplica uma tabela de preços diferente para o país de origem:
	• Se for 1 (EUA), o transporte vira R$ 12,00 (bem mais barato porque não é perigoso)
	• Se for 2 (México), o transporte vira R$ 21,00.
	• Se for 3 (Outros), o transporte vira R$ 60,00.
```
if (pais_origem == 2 || meio_transporte == 'A') { <br>
seguro = preco_unitario / 2.0; <br>
} else { <br>
seguro = 0.0; <br>
} 

preco_final = preco_unitario + imposto + transporte + seguro; <br>

printf("\n--- Resultados do Produto ---\n"); <br>
printf("Valor do Imposto: R$ %.2f\n", imposto); <br>
printf("Valor do Transporte: R$ %.2f\n", transporte); <br>
printf("Valor do Seguro: R$ %.2f\n", seguro); <br>
printf("Preço Final: R$ %.2f\n", preco_final); <br>
}

printf("\n=====================================\n"); <br>
printf("PROGRAMA ENCERRADO.\n"); <br>
printf("Total de impostos arrecadados: R$ %.2f\n", total_impostos); <br>
printf("=====================================\n");

return 0; <br>
}
```
-Esta última parte do código serve para calcular o valor do seguro, somar todos os custos para descobrir o preço final do produto atual, exibir o relatório desse produto na tela e, por fim, encerrar o programa mostrando o total geral de impostos arrecadados
```
if,else if e else
```
-if (Se): É sempre o ponto de partida. Ele faz a primeira pergunta. Se a condição for verdadeira, o programa executa o bloco de código dele e ignora todo o resto que vem abaixo.
-else if (Senão se): É o plano B, C, D.... Ele só é testado se o if lá de cima (ou o else if anterior) der falso.
-else (Senão): É a última alternativa (a saída padrão). Ele não faz nenhuma pergunta ou teste. Se todos os if e else if anteriores derem falsos, o computador cai obrigatoriamente dentro do else. Ele serve como uma rede de segurança para capturar qualquer caso que sobrou.

```