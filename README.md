# AplikasiPerhitunganDiskon_tugas3
 GHINA NAFSI-2210010324

# Deskripsi Program
* masukkan harga asli dan memilih persentase diskon

* Setelah menghitung, tampilkan harga akhir dan jumlah penghematan

# Komponen GUI
JFrame, JPanel, JLabel, JTextField, JComboBox, JButton , JSlider
- JLabel untuk judul aplikasi, seperti "Aplikasi Perhitungan Diskon".
- JLabel untuk label "Harga Asli", JTextField untuk input harga asli (beri nama txtHargaAsli).
- JLabel untuk label "Persentase Diskon", JComboBox (beri nama comboDiskon) untuk pilihan persentase diskon (10%, 20%, 30%, dst.).
- JButton dengan teks "Hitung" dan nama btnHitung.
- JLabel untuk label "Harga Akhir" dan JTextField (beri nama txtHargaAkhir) untuk menampilkan hasil harga akhir (set Editable menjadi false).
- JLabel untuk label "Penghematan" dan JTextField (beri nama txtPenghematan) untuk menampilkan jumlah penghematan (set Editable menjadi false).
- JSlider juga untuk untuk pilihan persentase diskon dan hasil persentase akan tampil di JLabel lblDiskonSlider

# Logika Program
Perhitungan aritmatika, Penanganan eksepsi

# Events
* ActionListener untuk tombol Hitung
 
  private void tombolHitungActionPerformed(java.awt.event.ActionEvent evt) {
~~~
  try {
            // Cek apakah hargaAsliTextField kosong atau tidak valid
            if (txtHargaAsli.getText().isEmpty() || txtHargaAsli.getText().equals("Rp ")) {
                JOptionPane.showMessageDialog(this, "Silakan masukkan harga asli.", "Error", JOptionPane.ERROR_MESSAGE);
                return;
            }

            // Ambil harga asli dari JTextField dan hilangkan "Rp " di depannya
            double hargaAsli = Double.parseDouble(txtHargaAsli.getText().replace("Rp ", ""));

            // Tentukan diskon persentase dari JSlider atau JComboBox
            int diskonPersen;
            if (SDiskon.getValue() > 0) {
                diskonPersen = SDiskon.getValue();
            } else {
                String diskonStr = (String) comboBDiskon.getSelectedItem();
                diskonPersen = Integer.parseInt(diskonStr.replace("%", ""));
            }

            // Ambil kode kupon dari JTextField
            String kodeKupon = kupon.getText().trim();

            // Tambahan diskon jika kode kupon valid
            if (kodeKupon.equalsIgnoreCase("DISKON10")) {
                diskonPersen += 10;
            } else if (!kodeKupon.isEmpty()) {
                JOptionPane.showMessageDialog(this, "Kode kupon tidak valid.", "Info", JOptionPane.INFORMATION_MESSAGE);
            }

            // Hitung penghematan dan harga akhir
            double penghematan = hargaAsli * diskonPersen / 100;
            double hargaAkhir = hargaAsli - penghematan;

            // Tampilkan hasil pada JTextField dengan prefix "Rp "
            txtPenghematan.setText("Rp " + String.format("%.2f", penghematan));
            txtHargaAkhir.setText("Rp " + String.format("%.2f", hargaAkhir));

            // Tambahkan hasil ke riwayat
            String hasilRiwayat = "Harga Asli: Rp " + hargaAsli +
                                  ", Diskon: " + diskonPersen + "%" +
                                  ", Penghematan: Rp " + String.format("%.2f", penghematan) +
                                  ", Harga Akhir: Rp " + String.format("%.2f", hargaAkhir) + "\n";
            txtRiwayat.append(hasilRiwayat);
        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this, "Masukkan nilai yang valid.", "Error", JOptionPane.ERROR_MESSAGE);
    }
~~~
}
     
* ItemListener pada JComboBox untuk memilih persentase diskon

public class DiskonFrame extends javax.swing.JFrame {
    
    public DiskonFrame() {
        initComponents();
        comboBDiskon.addItem("10%");
        comboBDiskon.addItem("20%");
        comboBDiskon.addItem("30%");
        }

# Variasi
* Tambahkan opsi untuk memasukkan kode kupon diskon tambahan

// Ambil kode kupon dari JTextField
           
            String kodeKupon = kupontext.getText().trim();

            // Tambahan diskon jika kode kupon valid
            if (kodeKupon.equalsIgnoreCase("DiskonHarga")) {
                diskonPersen += 10;
            } else if (!kodeKupon.isEmpty()) {
                JOptionPane.showMessageDialog(this, "Kode kupon tidak valid.", "Info", JOptionPane.INFORMATION_MESSAGE);
            }

* Tambahkan JSlider sebagai alternatif JComboBox untuk memilih persentase diskon

// Tentukan diskon persentase dari JSlider atau JComboBox
           
            int diskonPersen;
            if (SDiskon.getValue() > 0) {
                diskonPersen = SDiskon.getValue();
            } else {
                String diskonStr = (String) comboBDiskon.getSelectedItem();
                diskonPersen = Integer.parseInt(diskonStr.replace("%", ""));
            }

* Sediakan riwayat perhitungan diskon yang telah dilakukan.

// Tampilkan hasil pada JTextField dengan prefix "Rp "
           
            txtPenghematan.setText("Rp " + String.format("%.2f", penghematan));
            txtHargaAkhir.setText("Rp " + String.format("%.2f", hargaAkhir));

            // Tambahkan hasil ke riwayat
            String hasilRiwayat = "Harga Asli: Rp " + hargaAsli +
                                  ", Diskon: " + diskonPersen + "%" +
                                  ", Penghematan: Rp " + String.format("%.2f", penghematan) +
                                  ", Harga Akhir: Rp " + String.format("%.2f", hargaAkhir) + "\n";
            txtRiwayat.append(hasilRiwayat);
        } catch (NumberFormatException e) {
            JOptionPane.showMessageDialog(this, "Masukkan nilai yang valid.", "Error", JOptionPane.ERROR_MESSAGE);
    }

## Contoh Gambar Project Setelah di Run
<img width="445" alt="DiskonHarga" src="https://github.com/user-attachments/assets/75f1ff7a-c89e-49c1-bc29-5f85abbf8676">

## Indikator Penilaian:

| No  | Komponen         |  Persentase  |
| :-: | --------------   |   :-----:    |
|  1  | Komponen GUI     |    20    |
|  2  | Logika Program   |    20    |
|  3  | Kesesuaian UI    |    15    |
|  4  | Constructor      |    15    |
|  5  | Memenuhi Variasi |    30    |
|     | TOTAL        | 100 |

## Pembuat
NAMA:GHINA NAFSI
NPM:2210010324
KELAS 5A TI REG PAGI BJM
