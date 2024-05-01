# Reflection Module 9

1. What are the key differences between unary, server streaming, and bi-directional streaming RPC (Remote Procedure Call) methods, and in what scenarios would each be most suitable? </p>
- Unary RPC: Digunakan untuk operasi sederhana yang hanya membutuhkan satu permintaan dari klien dan satu respons dari server. Contohnya adalah operasi autentikasi atau pengambilan data tunggal.
- Server Streaming RPC: Cocok digunakan ketika server perlu mengirimkan data dalam jumlah besar atau pembaruan secara berkelanjutan kepada klien. Skenario yang tepat adalah layanan pembaruan langsung seperti pemantauan data real-time.
- Bi-directional Streaming RPC: Digunakan dalam aplikasi yang memerlukan pertukaran data dua arah secara berkelanjutan antara klien dan server. Contohnya adalah aplikasi chat yang memungkinkan pengguna untuk mengirim dan menerima pesan secara realtime.

2. What are the potential security considerations involved in implementing a gRPC service in Rust, particularly regarding authentication, authorization, and data encryption? </p>
- Autentikasi: Penting untuk menggunakan mekanisme autentikasi yang kuat, seperti token-based authentication atau Transport Layer Security (TLS), untuk memastikan identitas pengguna sebelum memberikan akses ke layanan.
- Otorisasi: Perlu diimplementasikan untuk memastikan bahwa pengguna hanya dapat mengakses fungsi-fungsi yang sesuai dengan hak akses yang dimilikinya.
- Enkripsi Data: Penggunaan TLS atau HTTPS dalam komunikasi antara klien dan server sangat penting untuk melindungi data selama proses transmisi, menghindari risiko kebocoran informasi sensitif.

3. What are the potential challenges or issues that may arise when handling bidirectional streaming in Rust gRPC, especially in scenarios like chat applications? </p>
- Manajemen Memori: Perlu dilakukan dengan hati-hati untuk menghindari kebocoran memori dan kondisi balapan yang dapat menyebabkan perilaku tak terduga.
- Keamanan Data: Penting untuk menjaga keamanan informasi yang dikirim dan mencegah akses tidak sah terhadap data sensitif.
- Pengelolaan Konkurensi: Diperlukan strategi yang baik untuk mengelola konkurensi agar aplikasi dapat menangani banyak pengguna secara bersamaan tanpa mengorbankan kinerja.

4. What are the advantages and disadvantages of using the tokio_stream::wrappers::ReceiverStream for streaming responses in Rust gRPC services? </p>
- Kelebihan: Integrasi yang baik dengan ekosistem Tokio, kemampuan asinkron yang baik, dan dukungan untuk operasi streaming.
- Kekurangan: Kompleksitas tambahan dalam penggunaan dan ketergantungan pada runtime Tokio, yang dapat membatasi fleksibilitas aplikasi terutama dalam konteks pengembangan dan debugging.

5. In what ways could the Rust gRPC code be structured to facilitate code reuse and modularity, promoting maintainability and extensibility over time? </p>
- Membuat modul-modul yang terpisah untuk setiap fungsi atau layanan.
- Menggunakan trait untuk mendefinisikan fungsi-fungsi yang dapat digunakan kembali.
- Memanfaatkan perpustakaan (library) untuk tugas-tugas umum.
- Menerapkan pola desain seperti Dependency Injection untuk memudahkan pengujian dan perubahan komponen-komponen.

6. In the MyPaymentService implementation, what additional steps might be necessary to handle more complex payment processing logic? </p>
- Validasi Data yang Lebih Komprehensif: Memeriksa keakuratan data lebih lanjut sebelum melakukan pemrosesan pembayaran.
- Integrasi dengan Gateway Pembayaran: Menghubungkan sistem dengan gateway pembayaran untuk melakukan transaksi secara aman dan terstruktur.
- Implementasi Server Streaming: Diperlukan untuk mendukung transaksi dalam jumlah besar secara bersamaan tanpa mengorbankan kinerja.

7. What impact does the adoption of gRPC as a communication protocol have on the overall architecture and design of distributed systems, particularly in terms of interoperability with other technologies and platforms? </p>
- Efisiensi Komunikasi: gRPC memungkinkan komunikasi yang lebih efisien melalui protokol HTTP/2 yang mendukung multiplexing dan streaming.
- Definisi Layanan yang Jelas: Dengan menggunakan file proto untuk mendefinisikan antarmuka layanan, interoperabilitas antar komponen sistem dapat ditingkatkan.
- Penggunaan Streaming: Kemampuan streaming dari gRPC memungkinkan aplikasi real-time dengan respons yang cepat dan efisien.

8. What are the advantages and disadvantages of using HTTP/2, the underlying protocol for gRPC, compared to HTTP/1.1 or HTTP/1.1 with WebSocket for REST APIs? </p>
- Keuntungan HTTP/2: Multiplexing, kompresi header, dan kemampuan streaming membuatnya lebih efisien dalam mengelola banyak permintaan dan respons secara bersamaan.
- Keuntungan WebSocket pada HTTP/1.1: Mendukung komunikasi dua arah secara real-time dengan lebih sederhana.
- Kekurangan HTTP/2: Memerlukan implementasi yang lebih kompleks, terutama terkait dengan konfigurasi dan manajemen TLS.
- Kekurangan WebSocket pada HTTP/1.1: Kurangnya dukungan untuk fitur-fitur HTTP/2 seperti multiplexing dan kompresi header.

9. How does the request-response model of REST APIs contrast with the bidirectional streaming capabilities of gRPC in terms of real-time communication and responsiveness? </p>
- REST API: Terbatas oleh model permintaan-respons, yang dapat menghambat responsivitas dalam aplikasi real-time.
- gRPC: Mendukung streaming dua arah yang memungkinkan komunikasi real-time yang lebih responsif antara klien dan server, cocok untuk aplikasi yang memerlukan interaksi dan pembaruan data secara realtime.

10. What are the implications of the schema-based approach of gRPC, using Protocol Buffers, compared to the more flexible, schema-less nature of JSON in REST API payloads? </p>
- Protokol Protobuf yang digunakan dalam gRPC menyediakan efisiensi dan konsistensi yang tinggi dalam pengelolaan data, yang sangat sesuai untuk aplikasi yang mengutamakan kecepatan dan efisiensi tinggi. Sementara, JSON yang digunakan dalam REST API menawarkan fleksibilitas yang lebih besar dalam penanganan data yang dinamis dan sering berubah, mempermudah adaptasi dengan berbagai kebutuhan tanpa harus terikat pada skema yang rigid. Namun, metode penggunaan JSON mungkin cenderung lebih lambat dan memerlukan lebih banyak sumber daya karena data JSON harus di-parse setiap kali diterima atau dikirim.

