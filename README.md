# Capstone3
Bike Sharing Rent Analysis
Contents
Business Understanding
Data Understanding
Data Preprocessing
Modeling
Conclusion
Recommendation
Business Understanding
Context
Sistem Bike-sharing akhir-akhir ini sangat diminati oleh masyarakat di Korea Selatan karena dinilai jauh lebih efektif dari persewaan sepeda tradisional sebelumnya, di mana eluruh proses, mulai dari keanggotaan, persewaan, hingga pengembalian dapat dilakukan secara otomatis. Selain itu, minat besar ada pada sistem ini karena peran pentingnya dalam masalah lalu lintas, lingkungan, dan kesehatan. Melalui sistem ini, pengguna dapat dengan mudah menyewa sepeda dari lokasi tertentu dan kembali lagi di lokasi lain. Di Korea Selatan sendiri saat ini, Kakao Mobility selaku salah satu perusahaan penyedia penyewaan Bike-sharing telah mengoprasikan lebih dari 10.000 sepeda elektrik di berbagai kota di Korea Selatan (info lebih lanjut baca di sini.

Meskipun sistem peminjaman sepeda telah menarik perhatian di dunia nyata, karakteristik data yang dihasilkan oleh sistem ini membuatnya menjadi subjek penelitian yang menarik. Berbeda dengan moda transportasi lain seperti bus atau kereta bawah tanah, data sistem peminjaman sepeda mencatat dengan jelas durasi perjalanan, posisi keberangkatan dan kedatangan. Oleh karena itu, sistem peminjaman sepeda dapat dianggap sebagai jaringan sensor virtual yang dapat digunakan untuk memantau mobilitas di dalam kota. Diharapkan bahwa data ini dapat membantu dalam mendeteksi peristiwa penting di kota dan meningkatkan pemahaman kita tentang mobilitas kota.

Problem statement
Salah satu tantangan utama dalam sistem Bike-sharing adalah untuk memastikan ketersediaan unit sepeda yang memadai berdasarkan situasi yang terjadi. Jika tidak terpenuhi, pengguna sistem dapat merasa tidak terlayani dan kehilangan kepercayaan pada layanan, selain itu juga menimbulkan kerugian karena berkurangnya revenue yang diterima oleh perusahaan. Namun, terlalu banyak unit sepeda yang tersedia juga dapat mengakibatkan sepeda tidak terpakai secara efisien, yang pada gilirannya dapat meningkatkan biaya manajemen, logistik, dan perawatan untuk setiap unit sepeda.

Goals
Tujuan dari penelitian ini adalah untuk mengetahui seberapa banyak kuantitas sepeda yang harus disiapkan untuk menghindari penumpukan sepeda yang menyebabkan kerugian karena tidak digunakan (cepat rusak, meningkatnya biaya maintenance, dan sebagainya) atau untuk menghindari dead weight loss atau kerugian yang diakibatkan oleh berkurangnya keuntungan yang didapatkan karena kurangnya sepeda yang disediakan pada saat high demand. Untuk menjawab kebutuhan tersebut, Kakao Mobility selaku perusahaan pelayanan perlu memiliki 'tool' yang baik guna memprediksi dan membantu tiap stakeholder terkait dalam menentukan jumlah sepeda yang tepat yang harus tersedia dalam setiap situasi dan kondisi.

Variabel cuaca dan kondisi lingkungan seperti suhu udara, kelembaban udara, kecepatan angin, dan curah hujan dapat mempengaruhi permintaan sepeda pada waktu tertentu. Dengan memahami hubungan ini, dapat membantu penyedia layanan sewa sepeda untuk mengoptimalkan operasi mereka dan meningkatkan kepuasan pengguna dengan menyesuaikan jumlah sepeda yang tersedia, lokasi stasiun sepeda, dan harga sewa pada saat-saat tertentu dengan mempertimbangkan faktor-faktor cuaca dan kondisi lingkungan. Selain itu, penelitian ini juga dapat membantu pengambilan keputusan dalam merencanakan strategi pemasaran dan promosi yang efektif untuk meningkatkan permintaan sepeda pada saat-saat tertentu yang dapat berdampak pada meningkatnya pendapatan penyedia layanan.

Analytic approach
Dalam memenuhi kebutuhan tersebut, yang perlu dilakukan adalah menganalisis data yang ada dan melakukan prediksi berdasarkan pola dari fitur-fitur yang ada. Kemudian membuat suatu model regresi yang dapat membantu perusahaan untuk menyediakan 'tool' prediksi penyediaan jumlah sepeda berdasarkan kondisi dan situasi yang ada dengan menggunakan analisis Machine Learning seperti Decision Tree, Random Forest atau Neural Networks. Analisis ini dapat digunakan untuk memprediksi permintaan sepeda berdasarkan variabel cuaca dan kondisi lingkungan pada waktu tertentu. Model ini dapat dilatih menggunakan data historis yang ada untuk memprediksi permintaan sepeda pada masa depan dengan lebih akurat.

Metric Evaluation
Evaluasi metrik yang akan digunakan untuk memprediksi kuantitas permintaan sepeda adalah sebagai berikut:

Mean Squared Error (MSE), yakni dengan mengukur rata-rata kesalahan kuadrat antara nilai sebenarnya dan nilai yang diprediksi oleh model. Semakin rendah nilai MSE, semakin baik kualitas model.

Root Mean Squared Error (RMSE): RMSE adalah akar kuadrat dari MSE dan mengukur kesalahan rata-rata antara nilai sebenarnya dan nilai yang diprediksi oleh model. Semakin rendah nilai RMSE, semakin baik kualitas model.

R-squared (R2)/ Adjust R-Squared: R-squared mengukur seberapa baik model cocok dengan data. Nilai R-squared berkisar antara 0 dan 1, dan semakin mendekati 1, semakin baik kualitas model
Mean Absolute Error (MAE): MAE mengukur rata-rata kesalahan absolut antara nilai sebenarnya dan nilai yang diprediksi oleh model. Semakin rendah nilai MAE, semakin baik kualitas model.

Conclusion
Analisis EDA menunjukan bahwa cuaca cerah di bulan september di musim gugur merupakan bulan yang paling diminati dengan lebih dari 250 pengguna rental sepeda. Penyewaan sepeda pada musim semi cenderung lebih sedikit, sedangkan rata-rata permintaan selama musim dingin sedikit lebih rendah. Umumnya, jumlah sewa sepeda lebih rendah pada akhir pekan. Nilai median penyewaan sepeda per jam relatif tinggi selama jam 7 pagi-8 pagi dan 5 sore-6 sore, terlepas dari tahun, bulan, dan hari. Hal ini dapat dikaitkan dengan para pekerja dan pelajar yang melakukan perjalanan rutin pada jam kerja.
Model dapat melakukan prediksi yang cukup baik hingga mencapai jumlah sepeda sekitar 600 unit, namun prediksi model cenderung menurun secara signifikan setelah mencapai angka tersebut.
Setelah hyperparameter tuning, model XGBoost berhasil meningkatkan performanya dengan skor terbaik -26.2604 dan parameter terbaik learning rate=0.1, max depth=8, n_estimators=240. Hasil analisis kedua menunjukkan performa yang lebih baik dari hasil analisis pertama dengan nilai MAE, MAPE, dan R-squared yang lebih baik. Namun, masih ada beberapa nilai yang sulit diprediksi secara akurat.
Ada beberapa faktor yang dapat menyebabkan beberapa nilai sulit diprediksi secara akurat oleh model XGBoost, antara lain:

Keterbatasan data: Model XGBoost memerlukan data yang berkualitas dan representatif untuk dapat membuat prediksi yang akurat. Jika data yang digunakan terbatas atau tidak cukup representatif, maka model akan sulit untuk mempelajari pola yang tepat dari data tersebut.
Variabilitas data: Jika data yang digunakan memiliki tingkat variasi yang tinggi atau tidak stabil, maka model XGBoost akan sulit untuk memprediksi nilai target yang akurat. Hal ini karena model tidak dapat menangkap variabilitas tersebut dalam data.
Faktor eksternal: Terkadang terdapat faktor eksternal yang tidak terduga yang dapat memengaruhi nilai target. Model XGBoost mungkin tidak dapat menangkap faktor-faktor ini dalam prediksinya, sehingga mengakibatkan beberapa nilai sulit diprediksi secara akurat.
Recomendation
Berdasarkan kesimpulan analisis di atas, beberapa rekomendasi yang dapat diberikan adalah:

Perluasan data: Meningkatkan kualitas dan representativitas data yang digunakan untuk melatih model XGBoost dapat membantu meningkatkan akurasi prediksi. Oleh karena itu, dapat dilakukan perluasan data dengan mengumpulkan data tambahan yang dibutuhkan.
Normalisasi data: Mengubah skala nilai atau menghilangkan nilai outlier sehingga model dapat mempelajari pola yang lebih stabil dari data.
Evaluasi faktor eksternal: Penting untuk mengevaluasi faktor eksternal yang mungkin memengaruhi nilai target, seperti lokasi rental sepeda, kejadian khusus, atau perubahan regulasi. Dengan mengevaluasi faktor-faktor ini, maka model dapat ditingkatkan untuk mempertimbangkan faktor-faktor ini dalam prediksinya.
Periksa performa model secara berkala: Penting untuk memeriksa performa model secara berkala dan menguji pada data yang berbeda untuk memastikan model tetap konsisten dalam memprediksi nilai target.
