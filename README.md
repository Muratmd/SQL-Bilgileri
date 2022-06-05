# SQL-Bilgileri

+ örnek veritabanına bu [linkten ulaşa bilirsiniz](https://github.com/Muratmd/SQL-Bilgileri/blob/main/Nortwind.sql).

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
+ WHERE ifadesi Customers tablosu içerisinde bulunan City sütunu için uygulanmış ve sütunda Berlin Varmı diye kontrol edilmiştir. 

### SQL AND,OR ve NOT Operatörleri
#### 1. AND

```sql
SELECT * FROM Customers WHERE ContactTitle ='Owner' AND Country ='Mexico';
```
+ Adında anlaşılacağı gibi "ve" operatorünü kullanarak owner ve ülkesi Mexico olan verileri Seçtik.

#### 2. OR
```sql
SELECT * FROM Customers WHERE Country ='USA' OR Country ='Mexico';
```
+ OR(VEYA) ifadesinde ülkesi ABD yada Mexico olan kayıtları Seçtik.

#### 3. NOT
```sql
SELECT * FROM Customers WHERE NOT Country ='USA' OR Country ='Mexico';
```
+ NOT(Değili) OR işleminde USA veya Mexico yu getir demiştik WHERE'den sonra NOT yazarak tam tersi bir işlem yaparak bu sefer de USA veya Mexico hariç kalan verileri getirdik.

#### Örnek 1 Combining AND ve OR
```sql
SELECT * FROM Customers WHERE Country ='Venezuela' AND (City ='Barquisimeto' OR City='I. de Margarita');
```
+ Ülkesi Venezuela ve şehiri Barquisimeto veya I. de Margarita olan kayıtları seçtik.

#### Örnek 2 Combining AND ve NOT
```sql
SELECT * FROM Customers WHERE NOT Country ='Venezuela' AND NOT Country ='USA';
```
+ AND kullanarak Yine ters işlem yaptık Venezuella ve USA hariç kayıtları seçtik.

### ORDER BY(ASC)
```sql
SELECT * FROM Customers ORDER BY Country;
```
+ Alfabetik yada Sayısal sıralama bu ASC sıralamadır.(DESC diye Belirtmediğinizde ASC dir ).
+ Customers Tablosunun Ülkeler sütunu içerisindeki verileri alfabetik sıraya soktuk.
+ 

### ORDER BY DESC
```sql
SELECT * FROM Customers ORDER BY Country DESC;
```
+ Yine Alfabetik ve Sayısal bir sıralama ancak Büyükten Küçüğe bir sıralama var().

### Birden Fazla Sütunda ORDER BY
```sql
SELECT * FROM Customers ORDER BY Country, CompanyName;
```
+ ORDER BY dan sonra , koyulması yeterlidir.

## Birden Fazla Sütunda ORDER BY ASC ve DESC 
```sql
SELECT * FROM Customers ORDER BY Country ASC, CompanyName DESC;
```
+ Country i ASC (A dan Z ye) , CompanyName DESC (Z den A ya) olarak sıralamsını istedik böylece ilk olarak ülkeler ASC (A dan Z ye) olarak sıralandı daha sonra aynı ülkenin CompanyNameleri DESC (Z den A ya) sıralandı

### INSERT INTO
+ INSERT INTO ifadesi, bir tabloya yeni kayıtlar eklemek için kullanılır.
```sql
INSERT INTO Customers (CustomerID, ContactName, City, PostalCode, Country,CompanyName)
VALUES ('MURAT','Murat Dursun','Ankara','06300','Turkey','ASD');
```
+ Customers tablosunun içerisindeki sütunlarından bazılarını yeni bir kayıt yapmak için seçtik ve ardından sırası ile bu sütunlara VALUES komutunu kullanarak değerleri atadık.

### NULL Value NEDİR?
+ NULL değeri olan bir alan, değeri olmayan bir alandır.
+ Sütunda boş bir alan olması NULL olduğu anlamına gelmez.

## IS NULL Sorgu
```sql
SELECT ContactName, Address
FROM Customers
WHERE Address IS NULL;
```
+ Customers Tablosunda Addess NULL olan verileri seçtik.
## IS NOT NULL Sorgu
+ NULL Değil sorgu(Adresi boş olmayan veriler)
```sql
SELECT ContactName, Address
FROM Customers
WHERE Address IS NOT NULL;
```

### SQL UPDATE

+ UPDATE ifadesi, bir tablodaki mevcut kayıtları değiştirmek(Güncellemek) için kullanılır.
```sql
UPDATE Customers
SET ContactName = 'Alfred Schmidt', City= 'Frankfurt'
WHERE CustomerID = 'ALFKI';
```
+ CustomerID 'ALFKI' olan kayıtın iki alanını(ContactName ve City) güncellemiş olduk.

## Birden Fazla Kayıtı Güncelleme
```sql
UPDATE Customers
SET ContactName='Juan'
WHERE Country='Mexico';
```
+ Customers tablosu içerisindeki ülkesi 'Mexico' olan bütün kayıtların hepsinin 'ContactName' Juan olarak değiştirdik.

### SQL DELETE

+ DELETE ifadesi, bir tablodaki mevcut kayıtları silmek için kullanılır.

```sql
DELETE FROM Customers WHERE CustomerID='MURAT';
```
+ WHERE önemlidir WHERE ifadesi kullanılmaz ise bütün tablodaki veriler silinecektir

```sql
DELETE FROM Customers;
```
+ WHERE kullanılmadığı için tablodaki bütün veriler silinecektir.

### SQL SELECT TOP

+ SELECT TOP döndürülecek kayıt sayısını belirtmek için kullanılır.
+ SELECT TOP binlerce kayıt içeren büyük tablolarda kullanışlıdır. Çok sayıda kayıt döndürmek performansı etkileyebilir.
+ Tüm veritabanı sistemleri SELECT TOP desteklemez. MySQL, sınırlı sayıda kayıt seçmek için LIMIT desteklerken. Oracle, FETCH FIRST n ROWS ONLY ve ROWNUM'u kullanır.

#### SQL Server/MS Access(MSSQL)
```sql 
SELECT TOP 3 * FROM Customers;
```
#### MySQL
```sql
SELECT * FROM Customers
LIMIT 3;
```
#### Oracle
```sql 
SELECT * FROM Customers
FETCH FIRST 3 ROWS ONLY;
```




















