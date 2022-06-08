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

### SQL TOP PERCENT
+ PERCENT ifadesi tablodaki kayıt sayısını belirli bir yüzde içerisinde seçer.

```sql
SELECT TOP 50 PERCENT * FROM Customers;
```
+ Tablodaki kayıtların 50% desini seçmiş olduk.

### WHERE ile birlikte TOP Kullanımı

```sql 
SELECT TOP 3 * FROM Customers
WHERE Country='Germany';
```
+ Ülkeye göre yaptığımız filtrelemelerde sadece ilk 3'nü almış olduk.


### MIN() and MAX()

#### MIN()
+ MIN() fonksiyonu, seçilen sütunun en küçük değerini döndürür.

```sql 
SELECT MIN(UnitPrice) AS SmallestPrice
FROM Products; 
```
+ Products tablomuzdaki UnitPrice sütununda en küçük değeri almış olduk.

#### MAX()

+ MAX() fonksiyonu, seçilen sütunda en büyük değeri döndürür.
```sql 
SELECT MIN(UnitPrice) AS SmallestPrice
FROM Products; 
```
+ Products tablomuzdaki UnitPrice sütununda en büyük değeri almış olduk.

### SQL COUNT(), AVG() and SUM()

#### COUNT()
+ COUNT() fonksiyonu, belirtilen bir ölçütle eşleşen satır sayısını döndürür.

```sql
SELECT COUNT(PRoductID)
FROM Prooducts;
``` 
+ Prooducts tablosundaki PRoductID sütununu kullanarak toplam kaç kayıt olduğunu hesaplamış olduk.


#### AVG()
+ AVG() fonksiyonu, sayısal bir sütunun ortalama değerini döndürür.
```sql 
SELECT AVG(UnitPrice)
FROM Products;
```
+ Prooducts tablosundaki UnitPrice sütununu kullanarak sütundaki ortalama değeri hesapladık.


#### SUM()

+ SUM() fonksiyonu, sayısal bir sütunun toplam toplamını döndürür.

```sql 
SELECT SUM(UnitPrice)
FROM Products;
```
+ Prooducts tablosundaki UnitPrice sütununu kullanarak sütundaki değerileri topladık.

### SQL LIKE
+ Aşağıdaki SQL ifadesi, "a" ile başlayan MüşteriAdı olan tüm CustomerID seçer.
``` sql 
SELECT * FROM Customers
WHERE CustomerID LIKE 'a%';
```

+ Aşağıdaki SQL ifadesi, "a" ile biten bir MüşteriAdı olan tüm CustomerID seçer.
``` sql 
SELECT * FROM Customers
WHERE CustomerID LIKE '%a';
```

+ Aşağıdaki SQL ifadesi, herhangi bir konumda "or" olan bir CustomerID olan tüm müşterileri seçer.
```sql
SELECT * FROM Customers
WHERE CustomerID LIKE '%or%';
```

+ Aşağıdaki SQL ifadesi, ikinci konumda "r" olan bir CustomerID olan tüm müşterileri seçer.
```sql
SELECT * FROM Customers
WHERE CustomerID LIKE '_r%';
```

+ Aşağıdaki SQL ifadesi, "a" ile başlayan ve en az 3 karakter uzunluğunda bir CustomerID olan tüm müşterileri seçer:

```sql
SELECT * FROM Customers
WHERE CustomerID LIKE 'a__%';
```

+ Aşağıdaki SQL ifadesi, "a" ile başlayan ve "o" ile biten bir CustomerID ile tüm müşterileri seçer:

```sql
SELECT * FROM Customers
WHERE CustomerID LIKE 'A%I';
```

+ Aşağıdaki SQL ifadesi, "a" ile BAŞLAMAYAN MüşteriAdı olan tüm müşterileri seçer:
 ```sql 
 SELECT * FROM Customers
WHERE CustomerID NOT LIKE 'a%';
 
 ```
 
### SQL Wildcard(JOKER) Karakterler
 
 + Joker karakterler LIKE operatörüyle birlikte kullanılır. LIKE operatörü, bir sütunda belirtilen bir kalıbı aramak için bir WHERE yan tümcesinde kullanılır.
 
 | Sembol  | Tanım | Örnek |
 | ------------- | ------------- | ------------- |
 | % |  Sıfır veya daha fazla karakteri temsil eder. | %MU / ilk harfde m ve u arar. Murat ve Mustafa gibi. |
 | _  |  Tek bir karakteri temsil eder. | M_R_T / joker harf "_" olan yere herhangi bir harf gelebilir.  |
 | [ ]  | Parantez içindeki herhangi bir tek karakteri temsil eder | M[URA]T(MURAT I BULAMAZ!!) MUT,MRT ve MAT gibi şeyleri bulur sadece [ ] içerisindeki harfler  tek harf yerine geçer. |
 | ^  | Parantez içinde olmayan herhangi bir karakteri temsil eder  |M[^URA]T(MURAT I BULAMAZ!!) MUT,MRT ve MAT I bulamaz "^" ifadesi değil olarak kullanılıyor örnek MOT, MET gibi şeyleri bulabilir. |
 | -  | Belirtilen aralıktaki herhangi bir tek karakteri temsil eder |Alfabetik Sırada bir aralık seçer C[A-K]T  dediğimizde C ve T arasına A dan K ya bütün harfleri kabul edecek ve veritabanında Örneğin CAT var ise CAT yazacak yada CET gibi. |
 
 
 + Aşağıdaki SQL fonksiyonu, "ber" ile başlayan bir City'ye sahip tüm müşterileri seçer.
 
```sql
SELECT * FROM Customers
WHERE City LIKE 'ber%';
```
 
 
 + Aşağıdaki SQL fonksiyonu, "es" kalıbını içeren bir Şehire sahip tüm müşterileri seçer.
 
 ``` sql
 SELECT * FROM Customers
WHERE City LIKE '%es%';
 ```
 
 + Aşağıdaki SQL fonksiyonu, herhangi bir karakterle başlayan ve ardından "ondon" gelen City olan tüm müşterileri seçer.
 ```sql
 SELECT * FROM Customers
WHERE City LIKE '_ondon';
 ```
 
 + Aşağıdaki SQL deyimi, "L" ile başlayan, ardından herhangi bir karakter, ardından "n", ardından herhangi bir karakter ve ardından "on" olan tüm müşterileri seçer:
 
 ```sql
 SELECT * FROM Customers
WHERE City LIKE 'L_n_on';
 ```
 
 + Aşağıdaki SQL deyimi, "b", "s" veya "p" ile başlayan bir Şehire sahip tüm müşterileri seçer.
 
 ```sql
 SELECT * FROM Customers
WHERE City LIKE '[bsp]%';
 ```
  + Aşağıdaki SQL deyimi, "a", "b" veya "c" ile başlayan bir Şehire sahip tüm müşterileri seçer.
 
 ```sql
 SELECT * FROM Customers
WHERE City LIKE '[a-c]%';
 ```
 
 + Aşağıdaki iki SQL ifadesi, "b", "s" veya "p" ile BAŞLAMAYAN City'ye sahip tüm müşterileri seçer:
 
 ```sql
 SELECT * FROM Customers
WHERE City LIKE '[!bsp]%';
 ```
 yada
 ```sql
 SELECT * FROM Customers
WHERE City NOT LIKE '[bsp]%';
 ```
 
 
 
 ### SQL IN 
+ IN operatörü, bir WHERE yan tümcesinde birden çok değer belirtmenize izin verir.
+ IN operatörü, çoklu OR(VEYA) koşulları için bir kısayoldur.

+ Aşağıdaki SQL ifadesi, "Almanya", "Fransa" veya "İngiltere"de bulunan tüm müşterileri seçer.
```sql
SELECT * FROM Customers  WHERE Country IN ('Germany','France','UK');
```

+ Aşağıdaki SQL deyimi, "Almanya", "Fransa" veya "İngiltere" de OLMAYAN tüm müşterileri seçer.
```sql
SELECT * FROM Customers WHERE Country NOT IN  ('Mexico','Spain');
```

+ Aşağıdaki SQL ifadesi, tedarikçilerle aynı ülkelerden gelen tüm müşterileri seçer.

```sql
SELECT * FROM Customers
WHERE Country IN (SELECT Country FROM Suppliers);
```

### SQL BETWEEN
+ BETWEEN operatörü, belirli bir aralıktaki değerleri seçer. Değerler sayı, metin veya tarih olabilir.
+ BETWEEN operatörü kapsayıcıdır: başlangıç ve bitiş değerleri dahildir.

+ Aşağıdaki SQL ifadesi, fiyatı 10 ile 20 arasında olan tüm ürünleri seçer,

```sql
SELECT * FROM  Products WHERE UnitPrice BETWEEN 10 AND 20;
``` 

+ Önceki örneğin kapsamı dışında kalan ürünleri görüntülemek için, NOT BETWEEN'i kullanın.
```sql
SELECT * FROM  Products WHERE UnitPrice NOT BETWEEN 10 AND 20;
``` 
+ Aşağıdaki SQL deyimi, fiyatı 10 ile 20 arasında olan tüm ürünleri seçmektedir. Ayrıca; Kategori Kimliği 1,2 veya 3 olan ürünleri gösterme ve Fiyatları küçükten büyüğe sırala.

```sql 
SELECT * FROM Products WHERE UnitPrice BETWEEN 10 AND 20 AND CategoryID NOT IN (1,2,3) ORDER BY UnitPrice;
```` 

+ Aşağıdaki SQL deyimi, "Carnarvon Tigers" ve "Mozzarella di Giovanni" arasında "ProductName" olan tüm ürünleri seçer.

```sql 
SELECT * FROM Products
WHERE ProductName BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName;
```

+ Aşağıdaki SQL ifadesi, Carnarvon Tigers ve Mozzarella di Giovanni arasında olmayan bir ProductName ile tüm ürünleri seçer:
``` sql

SELECT * FROM Products
WHERE ProductName NOT BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName;

```














