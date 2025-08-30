# ContaBancaria-iniciante.java
Um simples sistema de conta bancária em Java que ajuda a praticar conceitos fundamentais na Linguagem de Programação Orientada à Objetos, como métodos, classes, atributos e construtores.


import java.util.Scanner;

class ContaBancaria {               //classe Conta BancC!ria
	String titular;                 // criação de atributos
	double saldo;

	ContaBancaria(String titular,double saldo) {     //método todo construtor
		this.titular=titular;                        //atribuir o parâmetro para a variável(tem o mesmo nome)
		this.saldo=saldo;
	}

	void depositar(double valor) {              //método que retorna o valor do saldo somado ao novo valor depositado
		saldo+=valor;
		System.out.println("Foi realizado um depósito de R$"+valor);

	}

	void sacar(double valor) {                //método que retorna o valor do saque feito
		if(valor<=saldo) {
			saldo-=valor;
			System.out.println("Foi realizado um saque de R$"+valor);
		}
		else {
			System.out.println("Saldo insuficiente! Saque negado!");
		}
	}

	void exibirSaldoAtual() {                      //método que retorna o nome do titular e o valor do saque atual
		System.out.println("Titular: "+titular);
		System.out.println("Saldo atual: "+saldo);

	}
}
class Main {                                       //classe principal do programa
	public static void main(String[]args) {
		Scanner entrada=new Scanner(System.in);
		ContaBancaria conta=null;
		for(;;) {
			System.out.println("***CONTA BANCÁRIA***");
			System.out.println("O que deseja fazer?\n[1]Criar conta simples\n[2]Depositar valor\n[3]Sacar valor\n[4]Sair");
			System.out.println("Digite sua opção:");
			int op=entrada.nextInt();       //opção escolhida
			entrada.nextLine();    //limpa o buffer
			if(op==4) {
				break;
			}
			switch(op) {
			case 1:
				System.out.println("Digite o nome do titular:");        //criação da conta
				String titular= entrada.nextLine();
				System.out.println("Digite seu saldo atual:");
				double saldo=entrada.nextDouble();
				entrada.nextLine();

			    conta= new ContaBancaria(titular,saldo); //criação do objeto(podem criar mais)
				conta.exibirSaldoAtual();
				break;
			case 2:
				if(conta==null) {
					System.out.println("Primeiro crie uma conta [1]!");
				} 
				else{
				System.out.println("Quanto você deseja depositar:R$");         //quanto deseja depositar
				double valor= entrada.nextDouble();
				conta.depositar(valor);
				conta.exibirSaldoAtual();
				  }
				break;
			case 3:
				if(conta==null) {
                    System.out.println("Primeiro crie uma conta [1]!");
				}
				else{
				System.out.println("Quanto deseja sacar:R$");           //quanto deseja sacar
				double saque=entrada.nextDouble();
				conta.sacar(saque);
				conta.exibirSaldoAtual();
				}
				break;
			default:
				System.out.println("Não há esta opção!");
				break;
			}
		}
		entrada.close();
	}
}
