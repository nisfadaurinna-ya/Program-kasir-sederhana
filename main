import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        try (Scanner input = new Scanner(System.in)) {
            Kasir kasir = new Kasir();

            System.out.println("==================================");
            System.out.println("       PROGRAM KASIR SEDERHANA");
            System.out.println("==================================");
            System.out.print("Masukkan nama kasir: ");
            String namaKasir = input.nextLine();

            int pilihan;
            do {
                System.out.println("\n==================================");
                System.out.println("             MENU UTAMA");
                System.out.println("==================================");
                System.out.println("Kasir: " + namaKasir);
                System.out.println("1. Tambah Barang");
                System.out.println("2. Lihat Keranjang");
                System.out.println("3. Checkout / Bayar");
                System.out.println("4. Keluar");
                System.out.println("==================================");
                System.out.print("Pilih menu: ");

            while (!input.hasNextInt()) {
                System.out.print("Masukkan angka 1-4: ");
                input.next();
            }
            pilihan = input.nextInt();
            input.nextLine();

            switch (pilihan) {
                case 1 -> {
                    kasir.tambahBarang(input);
                }
                case 2 -> {
                    kasir.lihatKeranjang();
                }
                case 3 -> {
                    kasir.checkout(input, namaKasir);
                }
                case 4 -> {
                    System.out.println("\nTerima kasih, " + namaKasir + "!");
                    System.out.println("Program kasir telah ditutup.");
                }
                default -> {
                    System.out.println("Pilihan tidak tersedia. Pilih 1-4.");
                }
            }
        }
        while (pilihan != 4);

        input.close();
        }
    }
}

