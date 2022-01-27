- 👋 Hi, I’m @MisaelBaia
- 👀 I’m interested in ...
- 🌱 I’m currently learning ...
- 💞️ I’m looking to collaborate on ...
- 📫 How to reach me ...

<!---
MisaelBaia/MisaelBaia is a ✨ special ✨ repository because its `README.md` (this file) appears on your GitHub profile.
You can click the Preview link to take a look at your changes.
--->
#include <stdio.h>
#include <stdio.h>
#include <string.h>
#include <locale.h>
#define MAX 80

int main(){

    int escolha,lin,col, total_prod=0,num_cadastro=0,zerar_col;
    int a = 0;

    float produtos[3][3], codigo;
    char descricao[50][50], fornecedor[50][50];


    char linha[MAX];
    FILE *pba;
    char *nome = "tarefa_Rodney.txt";

    while(escolha!=5){
printf("--------Olá, Seja Bem Vindo ao Locadastro (Sistema de cadastro da Localiza)-------\n\n");
    printf("Escolha uma das opções abaixo \n\n");
    printf("1-Cadastar cliente \n\n");
    printf("2-listar todos os cadastros \n\n");
    printf("3-Remover cliente \n\n");
    printf("4-salvar clientes em arquivo texto \n\n");
    printf("5-Sair\n");
    scanf("%d", &escolha);

    switch(escolha){

        case 1:
            printf("Quantos clientes serão cadastrados? \n");
            scanf("%d",&num_cadastro);

            for (lin=0; lin<num_cadastro; lin++) {
                    total_prod++;
                for(col=0; col<4;) {
                    do{
                    printf("Qual o codigo de matrícula do cliente? ( Número ) \n",lin, col);
                    scanf("%f",&produtos[lin][col]);
                    }while(produtos[lin][col] == 0);

                    col++;
                    do{
                    printf("Qual o CPF do cliente? ( Número ) \n", lin, col);
                    scanf("%f",&produtos[lin][col]);
                    }while(produtos[lin][col]== 0);
                    col++;
                    printf("Número de telefone do Cliente? ( Número ) \n", lin, col);
                    scanf("%f", &produtos[lin][col]);
                    col++;
                    printf("Qual a data de nascimento do cliente? ( Número ) \n", lin, col);
                    scanf("%f", &produtos[lin][col]);
                    col++;

                }
                    printf("Qual o nome do cliente? ( Letras )\n");
                    scanf("%s",&descricao[lin]);

                    printf("Qual o Sobrenome? (Letras)\n");
                    scanf("%s", &fornecedor[lin]);

            }


            break;


        case 2:
            if(total_prod==0){
                printf(" DESCULPE!!! Não ha nenhum cliente cadastrado no nomento\n");
                break;
            }

            for (lin=0; lin<num_cadastro; lin++){
                for (col=0; col<4;){
                printf("CÓDIGO DE MATRÍCULA:  = %.2f \n\n", lin, col, produtos[lin][col]);
                col++;
                printf("CPF: m[%d][%d] = %.2f \n\n", lin, col, produtos[lin][col]);
                col++;
                printf("Número do Cliente: m[%d][%d] = %.2f \n\n", lin, col, produtos[lin][col]);
                col++;
                printf("DATA DE NASCIMENTO: m[%d][%d] = %.2f \n\n", lin, col, produtos[lin][col]);
                col++;
                }
                printf("NOME DO CLIENTE: %s\n",descricao[lin]);
                printf("SOBRENOME: %s\n", fornecedor[lin]);
            }

        break;

        case 3:

            printf("Qual o codigo do produto?\n");
            scanf("%f", &codigo);

                for(lin=0; lin<num_cadastro; lin++){
                        zerar_col=lin;
                    for(col=0; col<4; col++){
                        if(codigo==produtos[lin][col]){

                                for(col=0; col<4; col++){
                                    produtos[zerar_col][col] = 0;

                                }
                            strcpy(fornecedor[zerar_col], " ");
                            strcpy(descricao[zerar_col], " ");

                            total_prod= total_prod - 1;
                            break;
                        }else{
                        printf("produto nao encontrado\n");
                        break;
                        }

                    }

                }
        break;

        case 4:
            if((pba=fopen(nome,"w+")) == NULL){
               printf ("\n\nNao foi possivel abrir o arquivo.\n\n");
               return 1;
            }

             for(lin=0; lin<num_cadastro; lin++){
                    for(col=0; col<4; col++){
                        fprintf(pba,"Codigo do produto m[%d][%d] = %.2f \n", lin, col, produtos[lin][col]);
                        col++;
                        fprintf(pba,"Quantidade m[%d][%d] = %.2f \n", lin, col, produtos[lin][col]);
                        col++;
                        fprintf(pba,"Preco de venda m[%d][%d] = %.2f \n", lin, col, produtos[lin][col]);
                        col++;
                        fprintf(pba,"Preco de compra m[%d][%d] = %.2f \n", lin, col, produtos[lin][col]);
                        col++;
                    }
                    fprintf(pba,"Descricao produto: %s\n", descricao[lin]);
                    fprintf(pba, "Fornecedor: %s\n", fornecedor[lin]);
             }

             fclose(pba); // fecha arquivo
             printf("\nArquivo %s gravado com sucesso!\n", nome);
             return 0;


        case 5://teste
            printf("Obrigado por usar este programa");
        break;

    }

}

}

