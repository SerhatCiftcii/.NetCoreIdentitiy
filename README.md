# .NetCoreIdentitiy


IdentityApp - .NET Core 7.0 & Entity Framework Core with SQLite Authentication
---Proje Açıklaması
Bu proje, .NET Core 7.0, Entity Framework Core ve SQLite kullanılarak geliştirilmiş basit bir kimlik doğrulama sistemini içermektedir. E-posta doğrulama ile kullanıcı kaydı yapılabilir ve admin kullanıcı varsayılan olarak oluşturulmuştur.
Özellikler
Kimlik Yönetimi: ASP.NET Core Identity kullanılarak kullanıcı ve rol yönetimi.
SQLite Veritabanı: Hafif ve hızlı bir veritabanı çözümü (auth.db dosyası).
E-Posta Doğrulama: Google SMTP üzerinden e-posta gönderimi.
Seed Data: Admin kullanıcısı başlangıçta otomatik olarak oluşturulur.


---login olma
Giriş yaparken kullanabileceğiniz bilgiler:
Kullanıcı Adı: admin2@serhat.com
Şifre: 12345aA
E-Posta Gönderimi
Projede Google SMTP servisi ile e-posta gönderimi sağlanmaktadır. Bunun için appsettings.json dosyasına aşağıdaki gibi SMTP ayarları ekleyebilirsiniz:

"EmailSender": {
    "Host": "smtp.gmail.com",
    "Port": 587,
    "EnableSSL": true,
    "Username": "kendigmailiniz@gmail.com",
    "Password": "googleuygulamaşifreniz"
}
Google SMTP'yi kullanmak için iki adımlı doğrulamayı açmanız ve Google Uygulama Şifresi oluşturmanız gerekmektedir. Alınan uygulama şifresi boşluk olmadan girilmelidir.
Alternatif olarak Brevo'nun SMTP API servisini de kullanabilirsiniz, ancak varsayılan yapılandırma Google SMTP'ye göre hazırlanmıştır.

--2.si kod içinde AccountControllerdan  
 await _emailSender.SendEmailAsync(Email, "Parola Sıfırlama", $"Parolanızı yenilemek için linke <a href='http://localhost:5034{url}'>tıklayınız.</a>."); 
kendi localınıze göre ayarlama yapın


--uygulama çalıştırılması
Projeyi GitHub'dan klonlayın:
git clone <repository-url>

cd IdentityApp

Gerekli bağımlılıkları yükleyin:
dotnet restore

Veritabanını migrate edin:
dotnet ef database update

Projeyi çalıştırın:
dotnet run

Admin kullanıcıyla giriş yapın:
Kullanıcı Adı: admin2@serhat.com
Şifre: 12345aA

--SQLite ile auth.db dosyası üzerinden çalışabilir, test verilerini hemen deneyebilirsiniz.
