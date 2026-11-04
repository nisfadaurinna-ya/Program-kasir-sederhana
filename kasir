import java.util.Scanner;

public class Kasir {
    private Barang[] keranjang = new Barang[10];
    private int jumlahBarang = 0;

    public void tambahBarang(Scanner input) {
        if (jumlahBarang >= keranjang.length) {
            System.out.println("Keranjang penuh! Maksimal 10 jenis barang.");
            return;
        }

        System.out.println("\n--- TAMBAH BARANG ---");
        System.out.print("Nama barang: ");
        String nama = input.nextLine().trim();

        System.out.print("Harga barang: Rp ");
        while (!input.hasNextDouble()) {
            System.out.print("Harga harus berupa angka. Masukkan kembali: Rp ");
            input.next();
        }
        double harga = input.nextDouble();

        System.out.print("Jumlah beli: ");
        while (!input.hasNextInt()) {
            System.out.print("Jumlah harus berupa angka bulat. Masukkan kembali: ");
            input.next();
        }
        int jumlah = input.nextInt();
        input.nextLine();

        if (nama.isEmpty() || harga <= 0 || jumlah <= 0) {
            System.out.println("Data tidak valid. Barang tidak ditambahkan.");
        } else {
            keranjang[jumlahBarang] = new Barang(nama, harga, jumlah);
            jumlahBarang++;
            System.out.println("Barang berhasil ditambahkan!");
        }
    }

    public double hitungTotalBelanja() {
        double total = 0;
        for (int i = 0; i < jumlahBarang; i++) {
            total += keranjang[i].hitungSubtotal();
        }
        return total;
    }

    public void lihatKeranjang() {
        System.out.println("\n--- KERANJANG BELANJA ---");

        if (jumlahBarang == 0) {
            System.out.println("Keranjang masih kosong.");
            return;
        }

        System.out.printf("%-4s %-18s %-14s %-8s %-14s%n",
                "No", "Nama Barang", "Harga", "Jumlah", "Subtotal");
        System.out.println("----------------------------------------------------------------");

        for (int i = 0; i < jumlahBarang; i++) {
            Barang barang = keranjang[i];
            System.out.printf("%-4d %-18s Rp%-12.0f %-8d Rp%-12.0f%n",
                    i + 1, barang.getNama(), barang.getHarga(),
                    barang.getJumlah(), barang.hitungSubtotal());
        }

        System.out.println("----------------------------------------------------------------");
        System.out.printf("Total Belanja: Rp %.0f%n", hitungTotalBelanja());
    }

    public void checkout(Scanner input, String namaKasir) {
        if (jumlahBarang == 0) {
            System.out.println("Keranjang masih kosong. Tambahkan barang terlebih dahulu.");
            return;
        }

        double totalBelanja = hitungTotalBelanja();
        double diskon = 0;

        // Diskon 10% jika total lebih dari Rp100.000.
        if (totalBelanja > 100000 && jumlahBarang > 0) {
            diskon = totalBelanja * 0.10;
            System.out.println("Selamat! Anda mendapatkan diskon 10%.");
        } else {
            System.out.println("Belanja belum memenuhi syarat diskon.");
        }

        double totalBayar = totalBelanja - diskon;

        System.out.println("\n--- CHECKOUT ---");
        System.out.printf("Total Belanja : Rp %.0f%n", totalBelanja);
        System.out.printf("Diskon        : Rp %.0f%n", diskon);
        System.out.printf("Total Bayar   : Rp %.0f%n", totalBayar);

        double uangBayar;
        System.out.print("Masukkan uang pembayaran: Rp ");
        while (!input.hasNextDouble()) {
            System.out.print("Masukkan nominal berupa angka: Rp ");
            input.next();
        }
        uangBayar = input.nextDouble();
        input.nextLine();

        if (uangBayar < totalBayar || uangBayar <= 0) {
            System.out.println("Uang pembayaran tidak mencukupi. Checkout belum selesai.");
            return;
        }

        double kembalian = uangBayar - totalBayar;
        cetakStruk(namaKasir, totalBelanja, diskon, totalBayar, uangBayar, kembalian);

        // Keranjang dikosongkan setelah pembayaran berhasil.
        keranjang = new Barang[10];
        jumlahBarang = 0;
    }

    private void cetakStruk(String namaKasir, double totalBelanja,
                            double diskon, double totalBayar,
                            double uangBayar, double kembalian) {
        System.out.println("\n==========================================");
        System.out.println("             STRUK PEMBAYARAN");
        System.out.println("==========================================");
        System.out.println("Nama Kasir: " + namaKasir);
        System.out.println("------------------------------------------");

        for (int i = 0; i < jumlahBarang; i++) {
            Barang barang = keranjang[i];
            System.out.printf("%-18s x%-3d Rp %.0f%n",
                    barang.getNama(), barang.getJumlah(),
                    barang.hitungSubtotal());
        }

        System.out.println("------------------------------------------");
        System.out.printf("Total Belanja : Rp %.0f%n", totalBelanja);
        System.out.printf("Diskon        : Rp %.0f%n", diskon);
        System.out.printf("Total Bayar   : Rp %.0f%n", totalBayar);
        System.out.printf("Uang Bayar    : Rp %.0f%n", uangBayar);
        System.out.printf("Kembalian     : Rp %.0f%n", kembalian);
        System.out.println("==========================================");
        System.out.println("       TERIMA KASIH TELAH BELANJA");
        System.out.println("==========================================");
    }
}
