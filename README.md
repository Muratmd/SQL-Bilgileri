# SQL-Bilgileri

+ örnek veritabanına bu [linkten ulaşa bilirsiniz](https://raw.githubusercontent.com/Muratmd/SQL-Bilgileri/main/Nortwind.sql?token=GHSAT0AAAAAABUDZ6TJ3XPY2LG2SCQGSW7GYU26MCA).

+ linkteki sql i kopyaladıktan sonra Mssql üzerinden New Query diyerek Execute ediniz ardından Databases kısmında Northwind veritabanına ulaşabilirsiniz.



+ Sql veritabanlarının ortak dilidir ve MySQL, SQL Server, MS Access, Oracle, Sybase, Informix, Postgres ve diğerleri tarafıdan kullanılmaktadır.Ancak kullanılan ide ortamına göre değişiklikler bulunmaktadır.

+ Sql büyük küçük harf kontrolü yapmaz. Örnek olarak "select" ile "SELECT" aynı şeydir.

# Sql Nedir?

+ SQL, Yapılandırılmış Sorgu Dili anlamına gelir

+ SQL, veritabanlarına erişmenizi ve bunları değiştirmenizi sağlar

+ SQL, 1986'da Amerikan Ulusal Standartlar Enstitüsü'nün (ANSI) ve 1987'de Uluslararası Standardizasyon Örgütü'nün (ISO) standardı oldu.


# Sql Neler Yapabilir?
+ Bir veritabanı üzerinde çeşitli sorgular yapabilir.
+ Bir veritabanında çeşitli verileri getirebilir.
+ Bir veritabanı içerisine yeni kayıtlar oluşturabilir.
+ Bir veritabanı içerisindeki verileri güncelleyebilir.
+ Yeni bir veritabanıı oluşturabilir.
+ Bir veritabanı için yeni tablolar oluşturabilir.
+ Bir veritabanında saklı yordamlar oluşturabilir.
+ Bir veritabanında "views" oluşturabilir.
+ Tablolar, prosedürler ve görünümler üzerinde izinler ayarlayabilir

# Önemli Sql Komutları
+ SELECT - Bir veritabanından veri seçmek için kullanılır.
+ UPDATE - Veritabanı içerisinde bulunan bir veriyi(data) güncellemek için kullanılır.
+ DELETE - Veritabanı içerisinde bulunan bir veriyi(data) silmek için kullanılır.
+ INSERT INTO - Veritabanına yeni bir veri(data) eklemek için kullanılır.
+ CREATE DATABASE - Yeni bir Veritabanı oluşturmak için kullanılır.
+ ALTER DATABASE - Bir veritabanı üzerinede değişiklik yapılacağı zaman kullanılır.
+ CREATE TABLE - yeni bir Tablo oluşturmanızı sağlar.
+ ALTER TABLE - Tablo üzerinde değişiklik yapmak için kullanılır.
+ DROP TABLE - Bir tabloyu silmek için kullanılır.
+ CREATE INDEX - Bir arama anahtarı oluşturabilirsiniz.
+ DROP INDEX - INDEX i silmek için kullanılır.


# Sql Soguları Örnekler İle

> Northwind veritabanını seçtikten sonra New Query diyerek veritabanı üzerinde sorguları çalıştıra bilirsiniz.

### SELECT

```sql
SELECT * FROM Customers;
```
+ getirmek istediğimiz tablonun ismini yazarak o tablodaki bütün Sütunları getire biliriz.
+ Customers burda bizim veritabanımızın içerisinde bulunan bir tablonun ismidir.

### Tabloda Sütunları Seçme İşlemi
```sql
SELECT CustomerID FROM Customers;
```
+ Bu işlemde Customers tablosunun içerisinde bulunan CustomerId Sütununu getirmiş bulunduk.
+ Dikkat edecek olursanız bir önceki işlemde bulunan  *  işateti yok çünki  *  o tablo içerisindeki bütün sütunları çekmek için kullanılır
+ CustomerID yanına ',' koyarak başka sütunlarada erişilebilir.

### SELECT DISTINCT

```sql
SELECT DISTINCT  City FROM Customers;
```
+ DISTINCT ifadesi sütun içerisindeki tekrar eden verileri tekil bir hale getirmeye yarar.


```sql
SELECT COUNT(DISTINCT City) FROM Customers;
```
+ Birbirinden farklı kaçtana şehir oldğunu sayı olarak belirtmektedir.

### WHERE

```sql
SELECT * FROM Customers WHERE City = 'Berlin';

```
+WHERE ifadesi Customers tablosu içerisinde bulunan City sütunu için uygulanmış ve sütunda Berlin Varmı diye kontrol edilmiştir. 

### SQL AND,OR ve NOT Operatörleri
```sql



```












