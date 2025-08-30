# ContaBancaria-iniciante.java
Um simples sistema de conta bancária em Java que ajuda a praticar conceitos fundamentais na Linguagem de Programação Orientada à Objetos, como métodos, classes, atributos e construtores.

import java.util.Scanner;

class ContaBancaria{                //classe Conta Bancária
    String titular;                 // criação de atributos
    double saldo;
    
    ContaBancaria(String titular,double saldo){      //método construtor
        this.titular=titular;                        //atribuição do parâmetro para a variável(tem o mesmo nome)
        this.saldo=saldo;
    }
    
    void depositar(double valor){               //método que retorna o valor do saldo somado ao novo valor depositado
        saldo+=valor;
        System.out.println("Foi realizado um depósito de R$"+valor);
        
    }
    
    void sacar(double valor){                 //método que retorna o valor do saque feito
        if(valor<=saldo){
            saldo-=valor;
            System.out.println("Foi realizado um saque de R$"+valor);
        }
        else{
            System.out.println("Saldo insuficiente! Saque negado!");
        }
    }
     
    void exibirSaldoAtual(){                       //método que retorna o nome do titular e o valor do saque atual
       System.out.println("Titular: "+titular);
       System.out.println("Saldo atual: "+saldo);
        
    }
}
class Main{                                        //classe principal do programa
    public static void main(String[]args){
        ContaBancaria conta= new ContaBancaria("Anna",500);     //criação do objeto(podem criar quantos quiser)
        
        conta.exibirSaldoAtual();              //chama os métodos e passa parâmetros para aqueles que tem
        conta.depositar(50);
        conta.exibirSaldoAtual();
        conta.sacar(20);
        conta.exibirSaldoAtual();
    }
}
  
