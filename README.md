#include<stdio.h>
#include<stdlib.h> // recursos do sistema
#include<locale.h> // lib de idiomas
#include<math.h> // lib de matematica 
#include<string.h>

#define TAM 2

int cod = 0; //chamado para contar pra quantos foram cadastrados... 

typedef struct{
	char	nome[50], codigoUsuario[50], email[80];
	int idade, senha;
}Informacoes;

void systens(){
	fflush(stdin);
	printf("\n\n");
	system("pause");
	system("cls");
}

void cadastro(Informacoes informacoes[TAM]){ //cadastro dos usuarios...
	if(cod != TAM){
		printf("Vamos começar seu cadastro\n");
		printf("Me informe sua idade: ");
		scanf("%d", &informacoes[cod].idade);
		fflush(stdin);
		
		if(informacoes[cod].idade >= 18){
			printf("Seu nome: ");
			gets(informacoes[cod].nome);
			printf("Digite seu email: ");
			gets(informacoes[cod].email);
			printf("Crie um codigo: ");
			gets(informacoes[cod].codigoUsuario);
			fflush(stdin);	
			printf("Crie uma senha numerica: ");
			scanf("%d", &informacoes[cod].senha);
			fflush(stdin);
			system("cls");
			printf("Conta cadastrada com sucesso!");
			systens();
		}else{
			system("cls");
			printf("Desculpe, voçê não pode se cadastrar!");
			systens();
			abort();
		}
		cod++;
	}
}
void fazerLoguin(Informacoes informacoes[TAM]){
	char emailDigitado[80];
	int senhaDigitada;
	if(cod > 0){
		printf("LOGUIN BS \n");
		printf("Digite seu e-mail: ");
		gets(emailDigitado);
		
		printf("Digite sua senha: ");
		scanf("%d", senhaDigitada);
	}
}
void controle(Informacoes informacoes[], int escolhaUsuario){
	switch(escolhaUsuario){
		case 1:
			cadastro(informacoes);
			break;
		case 2:
			printf("2nn");
			break;
		case 3:
			printf("3nn");
			break;
		case 4:
			printf("4nn");
 			break;
		case 5:
			abort();
			break;
		default:
			printf("Opção inexistente!!");
			break;
	}
}

int main(){
	setlocale(LC_ALL,"");
	int escolhaUsuario;
	Informacoes informacoes[TAM];
	
	while(true){
		printf(" \n\n   BANCO SENAI  \n\n");
		printf("[1] Cadastrar conta \n");
		printf("[2] Fazer loguin \n");
		printf("[3] Mostrar contas cadastradas \n");
		printf("[4] Apagar conta \n");
		printf("[5] Finalizar atendimento\n\n");
		printf("Escolha uma opção: ");
		scanf("%d", &escolhaUsuario);
		system("cls");
		controle(informacoes, escolhaUsuario);	
	}	
}
