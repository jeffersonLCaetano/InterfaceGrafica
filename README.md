package lotofacil;

import com.sun.jdi.Value;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.IOException;
import java.util.Random;
import java.util.Scanner;

// variáveis não primitivos --  variáveis primitivas int, char etc
// classe primeira letra Maiuscula -- variáveis primeira letra minuscula

public class InterfaceLotoFacil extends JFrame { //extends JFrame é a janela criando a "interface"

    //
    private JPanel painel = new JPanel();
    //Instanciar o objeto botão a partir da classe JButton e adicionando um título para o botão
    private JButton jButtonZeroCem = new JButton("Apostar de 0 a 100");
    //Instanciar o objeto botão a partir da classe JButton e adicionando um título para o botão
    private JButton jButtonAaZ = new JButton("Apostar de A a Z");
    //Instanciar o objeto botão a partir da classe JButton e adicionando um título para o botão
    private JButton jButtonParImpar = new JButton("Apostar par ou ímpar");
    private JLabel jLabelMensagem = new JLabel("Exemplo de Simples Janela");

    //método construtor
    public InterfaceLotoFacil() {
        //Este método recebe o titulo da janela
        this.setTitle("LotoFácil - Interface Gráfica");
        //Este método recebe a largura e a altura da janela em pixels, sendo, primeiro a largura segundo altura
        this.setSize(400, 200);
        //Este método é pra adicionar layouts dos botões (FlowLayout) é para centralizar os botões na janela
        painel.setLayout(new FlowLayout(FlowLayout.CENTER, 100, 20));
        //Este método é para definir a cor da janela
        painel.setBackground(new Color(129, 121, 121));

        //Adicionando componentes (botões) na janela
        painel.add(jButtonZeroCem);
        painel.add(jButtonAaZ);
        painel.add(jButtonParImpar);

        //Este método irá retornar a área da janela q irá adicionar algum componente, que neste caso será os botões
        this.getContentPane().add(painel);
        //Este método a janela aparece centralizada
        this.setLocationRelativeTo(null);
        //Este método é pra não deixar o programa rodando quando fecha no X da janela... assim ocupando espaço na memória
        this.setDefaultCloseOperation(EXIT_ON_CLOSE);

        //Classe que trata a ação do botão abaixo zero cem
        jButtonZeroCem.addActionListener(new ActionListener() {
            @Override
            //Método da interface ActionListener
            public void actionPerformed(ActionEvent e) {
                String aposta = JOptionPane.showInputDialog(null, "Digite um número de 0 a 100");
                int numeroApostado = Integer.parseInt(aposta);

                zeroCem(numeroApostado);
            }
        });

        //Classe que trata a ação do botão abaixo zero cem
        jButtonAaZ.addActionListener(new ActionListener() {
            @Override
            //Método da interface ActionListener
            public void actionPerformed(ActionEvent e) {
                String aposta = JOptionPane.showInputDialog(null, "Digite uma letra de A a Z");
                char letraApostada = aposta.charAt(0);

                aZ(letraApostada);
            }
        });

        //Classe que trata a ação do botão abaixo zero cem
        jButtonParImpar.addActionListener(new ActionListener() {
            @Override
            //Método da interface ActionListener
            public void actionPerformed(ActionEvent e) {
                String aposta = JOptionPane.showInputDialog(null, "Digite um número par ou ímpar");
                int parImpar = Integer.parseInt(aposta);

                parImpar(parImpar);
            }
        });
        //Este método é pra deixar a janela visível
        this.setVisible(true);
    }

    public static void main(String[] args) {
        new InterfaceLotoFacil();
    }

    private static void zeroCem(int numeroApostado) {
        int aposta = 0;

        Random rdn = new Random();

        aposta = numeroApostado;

        // Sorteio
        int numeroAleatorio = rdn.nextInt(101);

        if (numeroAleatorio == aposta) {
            JOptionPane.showMessageDialog(null, "Você ganhou R$ 1.000,00");
        } else if (aposta < 0 || aposta > 100) {
            JOptionPane.showMessageDialog(null, "Aposta inválida!");
        } else {
            JOptionPane.showMessageDialog(null, "Que pena o número sorteado foi: " + numeroAleatorio);

        }
    }

    private static void aZ(char letradigitada) {
        char chxSeuNome = 'J';

        JOptionPane.showMessageDialog(null, "Sua letra é: " + letradigitada);
        char chxMaiusculo = Character.toUpperCase(letradigitada);

        if (chxSeuNome == chxMaiusculo) {
            JOptionPane.showMessageDialog(null, "Você ganhou R$ 500,00!");
        } else {
            JOptionPane.showMessageDialog(null, "Que pena! A letra sorteada foi: " + chxSeuNome);
        }

    }

    private static void parImpar(int parImpar) {

        int resultado = parImpar % 2;

        switch (resultado) {
            case 0:
                JOptionPane.showMessageDialog(null, "Você ganhou R$100,00 reais");
                break;
            default:
                JOptionPane.showMessageDialog(null, "Que pena!");
                JOptionPane.showMessageDialog(null, "O número digitado é ímpar e a premiação foi para números pares.");
                break;
        }
    }
}



