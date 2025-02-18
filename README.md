import java.util.Scanner; // mengimpor kelas Scanner untuk input dari pengguna
public class UasAtlet { // deklarasi kelas UasAtlet sebagai kelas utama
    public static void main(String[] args) { // mendeklarasikan method main, titik awal eksekusi program
        Scanner sc = new Scanner(System.in); // membuat objek Scanner bernama sc untuk membaca input dari pengguna

        System.out.print("Masukkan jumlah politeknik (harus lebih dari 0): "); // menampilkan pesan untuk meminta input jumlah politeknik
        int jumlahPoliteknik = sc.nextInt(); // membaca input bilangan bulat (jumlahPoliteknik)
        sc.nextLine(); // membersihkan buffer input agar tidak terjadi masalah dengan input nextLine() nantinya
        
        if (jumlahPoliteknik <= 0) { // mengecek apakah input jumlahpoliteknik tidak valid (<=0)
            System.out.println("Jumlah politeknik tidak valid."); // menampilkan pesan kesalahan jika input tidak valid
            return; // menghentikan program
        }

        String[][][] atlet = new String[3][jumlahPoliteknik][3]; // atlet adalah array tiga dimensi untuk menyimpan nama atlet
        String[] cabor = {"Badminton", "Basket", "Bola Voli"}; // cabor adalah array satu dimensi berisi nama cabang olahraga

        for (int olahraga = 0; olahraga < cabor.length; olahraga++) { // loop pertama untuk cabang olahraga
            System.out.println("Masukkan nama atlet untuk cabang " + cabor[olahraga] + ":"); // menampilkan pesan input untuk cabang olahraga yang di proses
            for (int politeknik = 0; politeknik < jumlahPoliteknik; politeknik++) { // loop kedua untuk setiap politeknik
                System.out.println("Politeknik " + (politeknik + 1) + ":"); // menampilkan informasi politeknik yang sedang di proses
                for (int nama = 0; nama < 3; nama++) { // loop ketiga untuk setiap atlet(3 atlet per politeknik)
                    System.out.print("Atlet " + (nama + 1) + ": "); // meminta input nama atlet
                    String namaAtlet = sc.nextLine(); // membaca input nama atlet
                    
                    if (namaAtlet.isEmpty()) { // validasi input jika nama atlet kosong, tampilan pesan kesalahan, ulangi iterasi atlet dengan nama
                        System.out.println("Nama atlet tidak boleh kosong. Silakan masukkan kembali."); // menyimpan nama atlet ke dalam array
                        nama--;
                    } else {
                        atlet[olahraga][politeknik][nama] = namaAtlet;
                    }
                }
            }
        }

        System.out.println("\nInformasi Nama Atlet:"); // menampilkan header untuk output informasi atlet
        for (int olahraga = 0; olahraga < cabor.length; olahraga++) { // loop pertama untuk setiap cabang olahraga
            System.out.println("Cabang " + cabor[olahraga] + ":");
            for (int politeknik = 0; politeknik < jumlahPoliteknik; politeknik++) { // loop kedua untuk setiap politeknik
                System.out.println("Politeknik " + (politeknik + 1) + ":"); // menampilkan informasi politeknik
                for (int nama = 0; nama < 3; nama++) { // loop ketiga untuk setiap atlet
                    System.out.println("Atlet " + (nama + 1) + ": " + atlet[olahraga][politeknik][nama]);
                }
                System.out.println(); // menambahkan baris kosong untuk memisahkan output
            }
        }
    }
}