#include<stdio.h> <br>
#include<ctype.h> 

int main() { <br>
    float preco_unitario, imposto, transporte, seguro, <br>
    preco_final; <br>
    float total_impostos = 0; <br>
    int pais_origem; <br>
    char meio_transporte, carga_perigosa;

while (1) { <br>
    printf("\n--- Entrada de Dados do Produto ---\n"); <br>
    printf("Digite o preço unitário (menor ou igual a 0 para sair): R$ "); <br>
    scanf("%f", &preco_unitario);

if (preco_unitario <= 0) { <br>
break; <br>
}

printf("Digite o país de origem (1 - EUA; 2 - México; 3 - Outros): "); <br>
scanf("%d", &pais_origem);

printf("Digite o meio de transporte (T - Terrestre; F - Fluvial; A - Aéreo): "); <br>
scanf(" %c", &meio_transporte); <br>
meio_transporte = toupper(meio_transporte);

printf("Carga perigosa? (S - Sim; N - Não): "); <br>
scanf(" %c", &carga_perigosa); <br>
carga_perigosa = toupper(carga_perigosa);

if (preco_unitario <= 100.00) { <br>
imposto = preco_unitario * 0.05; // 5% <br>
} else { <br>
imposto = preco_unitario * 0.10; // 10% <br>
} <br>
total_impostos += imposto;

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