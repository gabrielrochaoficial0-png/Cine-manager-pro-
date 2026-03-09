import java.util.Scanner;

public class App {
    static char[][] poltronas = new char[10][12];
    static Scanner input = new Scanner(System.in);

    public static void main(String[] args) {
        preencherSala();
        
        int escolha = -1;
        while (escolha != 0) {
            System.out.println("\n--- CINE GABRIEL - GESTÃO DE SALA ---");
            System.out.println("1 > Ver quem está sentado");
            System.out.println("2 > Vender ingresso");
            System.out.println("3 > Tirar reserva");
            System.out.println("0 > Fechar sistema");
            System.out.print("O que deseja fazer? ");
            
            try {
                escolha = Integer.parseInt(input.nextLine());
            } catch (Exception e) {
                System.out.println("Opa! Digite um numero de 0 a 3.");
                continue;
            }

            switch (escolha) {
                case 1:
                    mostrarMapa();
                    break;
                case 2:
                    reservar();
                    break;
                case 3:
                    cancelar();
                    break;
                case 0:
                    System.out.println("Saindo... Bom filme!");
                    break;
                default:
                    System.out.println("Opção inexistente!");
            }
        }
    }

    static void preencherSala() {
        for (int i = 0; i < 10; i++) {
            for (int j = 0; j < 12; j++) {
                poltronas[i][j] = '.';
            }
        }
    }

    static void mostrarMapa() {
        System.out.println("\n      [ TELA ]");
        for (int i = 0; i < 10; i++) {
            System.out.print((i + 1) + "  ");
            for (int j = 0; j < 12; j++) {
                System.out.print(poltronas[i][j] + " ");
            }
            System.out.println();
        }
    }

    static void reservar() {
        try {
            System.out.print("Qual a fila (1-10)? ");
            int f = Integer.parseInt(input.nextLine()) - 1;
            System.out.print("Qual a poltrona (1-12)? ");
            int p = Integer.parseInt(input.nextLine()) - 1;

            if (poltronas[f][p] == '.') {
                poltronas[f][p] = 'X';
                System.out.println("Feito! Assento reservado.");
            } else {
                System.out.println("Ih, esse já está ocupado!");
            }
        } catch (Exception e) {
            System.out.println("Erro na digitação. Tente de novo.");
        }
    }

    static void cancelar() {
        System.out.print("Fila do cancelamento: ");
        int f = Integer.parseInt(input.nextLine()) - 1;
        System.out.print("Poltrona do cancelamento: ");
        int p = Integer.parseInt(input.nextLine()) - 1;

        if (poltronas[f][p] == 'X') {
            poltronas[f][p] = '.';
            System.out.println("Reserva removida!");
        } else {
            System.out.println("Este assento já estava vazio.");
        }
    }
}
  
