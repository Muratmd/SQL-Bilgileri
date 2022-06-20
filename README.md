NOT: hocanın verdiği soruları yukarıda pdf e ekliyorum ordanda çalışa bilirsiniz 

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

### ORDER BY ve NEWID()
+ NEWID() her seferinde tablodaki verilerin yer değiştirmesini sağlar.
+ Aşağıdaki sorguda sıralama her seferinde farklı olacaktır.
````sql
SELECT * FROM Customers ORDER BY newid();
````
+ Aşağıdaki sorguda rastgele bir Customer seçmek için TOP ifadesini kullanacağız.
 ````sql
SELECT TOP 1 * FROM Customers ORDER BY newid();  
````

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

#### BETWEEN (ARASINDA)
+ Aşağıdaki SQL ifadesi, fiyatı 10 ile 20 arasında olan tüm ürünleri seçer,

```sql
SELECT * FROM  Products WHERE UnitPrice BETWEEN 10 AND 20;
``` 

#### NOT BETWEEN (ARASINDA DEĞİL)
+ Önceki örneğin kapsamı dışında kalan ürünleri görüntülemek için, NOT BETWEEN'i kullanın.
```sql
SELECT * FROM  Products WHERE UnitPrice NOT BETWEEN 10 AND 20;
``` 
+ Aşağıdaki SQL deyimi, fiyatı 10 ile 20 arasında olan tüm ürünleri seçmektedir. Ayrıca; Kategori Kimliği 1,2 veya 3 olan ürünleri gösterme ve Fiyatları küçükten büyüğe sırala.

```sql 
SELECT * FROM Products WHERE UnitPrice BETWEEN 10 AND 20 AND CategoryID NOT IN (1,2,3) ORDER BY UnitPrice;
```` 

#### BETWEEN Text Values(Metinsel aralık)

+ Aşağıdaki SQL deyimi, "Carnarvon Tigers" ve "Mozzarella di Giovanni" arasında "ProductName" olan tüm ürünleri seçer.

```sql 
SELECT * FROM Products
WHERE ProductName BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName;
```
#### NOT BETWEEN Text Values (Metinlerin dışında kalanlar)
+ Aşağıdaki SQL ifadesi, Carnarvon Tigers ve Mozzarella di Giovanni arasında olmayan bir ProductName ile tüm ürünleri seçer.
``` sql

SELECT * FROM Products
WHERE ProductName NOT BETWEEN 'Carnarvon Tigers' AND 'Mozzarella di Giovanni'
ORDER BY ProductName;

```
#### BETWEEN Dates (Tarihler ile)


+ Aşağıdaki SQL ifadesi, '01-Temmuz-1996' ve '31-Temmuz-1996' arasındaki OrderDate'li tüm siparişleri seçer.

```sql
SELECT * FROM Orders
WHERE OrderDate BETWEEN '1996-07-01' AND '1996-07-31';
```

### SQL Aliases(Takma Adlar)

+ SQL takma adları, bir tabloya veya tablodaki bir sütuna geçici bir ad vermek için kullanılır.
+ Takma adlar genellikle sütun adlarını daha okunaklı kılmak için kullanılır.
+ Bir takma ad yalnızca bir sorgunun süresi boyunca mevcuttur.
+ "AS" anahtar sözcüğüyle bir takma ad oluşturulur.

#### Sütun Örnekleri için Takma Ad Örneği(Alias)
+ Aşağıdaki SQL deyimi, biri MüşteriKimliği sütunu ve diğeri MüşteriAdı sütunu için olmak üzere iki takma ad oluşturur.

```sql
SELECT CustomerID AS ID, CustomerName AS Customer
FROM Customers;
```
+ Aşağıdaki SQL deyimi, biri MüşteriAdı sütunu ve diğeri KişiAdı sütunu için olmak üzere iki takma ad oluşturur. Not: Takma ad boşluk içeriyorsa, çift tırnak işareti veya köşeli parantez gerekir.

````sql
SELECT ContactName AS Customer, ContactName AS [Contact Person]
FROM Customers;
````
+ Aşağıdaki SQL ifadesi, dört sütunu (Adres, Posta Kodu, Şehir ve Ülke) birleştiren "Adres" adlı bir takma ad oluşturur:
````sql
SELECT ContactName, Address + ', ' + PostalCode + ' ' + City + ', ' + Country AS Address
FROM Customers;
````


#### Tablolar için Takma Ad(Alias) Örneği

+ Aşağıdaki SQL deyimi, CustomerID='ALFKI' olan müşteriden gelen tüm siparişleri seçer (Alfred Schmidt). "Müşteriler" ve "Siparişler" tablolarını kullanıyoruz ve onlara sırasıyla "c" ve "o" tablo takma adlarını veriyoruz (Burada SQL'i kısaltmak için takma adlar kullanıyoruz).

````sql
SELECT o.OrderID, o.OrderDate, c.ContactName
FROM Customers AS c, Orders AS o
WHERE c.ContactName='Alfred Schmidt' AND c.CustomerID=o.CustomerID;
````

+ Aşağıdaki SQL deyimi yukarıdakiyle aynıdır, ancak takma adları yoktur.
````sql
SELECT Orders.OrderID, Orders.OrderDate, Customers.ContactName
FROM Customers, Orders
WHERE Customers.ContactName='Alfred Schmidt' AND Customers.CustomerID=Orders.CustomerID;
````
### SQL JOIN

+ JOIN yan tümcesi, aralarında ilgili bir sütuna dayalı olarak iki veya daha fazla tablodaki satırları birleştirmek için kullanılır.



### Farklı Tiplerdeki SQL JOINs

+ (INNER) JOIN: Her iki tabloda da eşleşen değerlere sahip kayıtları döndürür

+ LEFT (OUTER) JOIN: Soldaki tablodaki tüm kayıtları ve sağdaki tablodaki eşleşen kayıtları döndürür.

+ RIGHT (OUTER) JOIN: Sağdaki tablodaki tüm kayıtları ve soldaki tablodaki eşleşen kayıtları döndürür.

+ FULL (OUTER) JOIN: Sol veya sağ tabloda bir eşleşme olduğunda tüm kayıtları döndürür


####  SQL INNER JOIN

+ INNER JOIN anahtar sözcüğü, her iki tabloda da eşleşen değerlere sahip kayıtları seçer.

+ Aşağıdaki SQL ifadesi, müşteri bilgilerine sahip tüm siparişleri seçer:



| OrderID  | 	CustomerID |OrderDate |
| ------------- | ------------- | ------------- |
| 10248 | VINET  | 1996-07-04|
| 10249  |TOMSP  |  1996-07-05|
| 10250  | HANAR  |  1996-07-08|


| CustomerID  | 	ContactName |Country |
| ------------- | ------------- | ------------- |
| VINET | Mario Pontes  | Brazil|
| TOMSP  |Karin Josephs | Germany|
| HANAR  |Paul Henriot  | France|

+ Aşşağıdaki Sql sorgusunu Tablolara göre inceleyiniz.
+ Dikkat edecek olursanız CustomerId nin 2 tablodada bulunduğunu göreceksiniz bu nedenle Customers Tablosuna JOIN olarak Orders ve Customers tablosundaki CustomerID lerin eşit olduğu kayıtları seçtik.
````sql
SELECT Orders.OrderID, Customers.ContactName, Orders.OrderDate
FROM Orders
INNER JOIN Customers
ON Orders.CustomerID=Customers.CustomerID;
````
+ Not: INNER JOIN anahtar sözcüğü, sütunlar arasında bir eşleşme olduğu sürece her iki tablodaki tüm satırları seçer. "Siparişler" tablosunda "Müşteriler" de eşleşmeyen kayıtlar varsa, bu siparişler gösterilmeyecektir!


#### SQL LEFT JOIN
+ LEFT JOIN anahtar sözcüğü, soldaki tablodaki (tablo1) tüm kayıtları ve sağdaki tablodaki (tablo2) eşleşen kayıtları döndürür. Sonuç, eşleşme yoksa sağ taraftan 0 kayıttır.

````sql
SELECT Customers.ContactName, Orders.OrderID
FROM Customers
LEFT JOIN Orders
ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.ContactName;

````
#### SQL RIGHT JOIN 
+ RIGHT JOIN anahtar sözcüğü, sağdaki tablodaki (tablo2) tüm kayıtları ve soldaki tablodaki (tablo1) eşleşen kayıtları döndürür. Sonuç, eşleşme yoksa sol taraftan 0 kayıttır.

````sql
SELECT Customers.ContactName, Orders.OrderID
FROM Customers
RIGHT JOIN Orders
ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.ContactName;
````

#### SQL FULL OUTER JOIN
+ Aşağıdaki SQL ifadesi tüm müşterileri ve tüm siparişleri seçer:
````sql
SELECT Customers.ContactName, Orders.OrderID
FROM Customers
FULL OUTER JOIN Orders ON Customers.CustomerID=Orders.CustomerID
ORDER BY Customers.ContactName;
````

#### SQL Self Join
+ Aşağıdaki SQL ifadesi, aynı şehirden olan müşterilerle eşleşir:

````sql
SELECT A.ContactName AS CustomerName1, B.ContactName AS CustomerName2, A.City
FROM Customers A, Customers B
WHERE A.CustomerID <> B.CustomerID
AND A.City = B.City
ORDER BY A.City;
````

### SQL UNION

+ UNION operatörü, iki veya daha fazla SELECT ifadesinin sonuç kümesini birleştirmek için kullanılır.
1. UNION içindeki her SELECT deyimi aynı sayıda sütuna sahip olmalıdır.
2. Sütunlar da benzer veri türlerine sahip olmalıdır.
3. Her SELECT ifadesindeki sütunlar da aynı sırada olmalıdır.



#### UNION


+ Aşağıdaki SQL ifadesi, hem "Customers" hem de "Suppliers" tablosundan şehirleri (yalnızca farklı değerleri) döndürür.
````sql
SELECT City FROM Customers
UNION
SELECT City FROM Suppliers
ORDER BY City;
````
#### UNION ALL
+ Aşağıdaki SQL ifadesi, hem "Customers" hem de "Suppliers" tablosundan şehirleri (Tekrar eden değerleri) döndürür.
````sql
SELECT City FROM Customers
UNION ALL
SELECT City FROM Suppliers
ORDER BY City;
````
#### SQL UNION Ile WHERE
+ Aşağıdaki SQL ifadesi, hem "Customers" hem de "Suppliers" tablosundan 'Germany' şehirlerini (yalnızca farklı değerleri) döndürür.
````sql
SELECT City, Country FROM Customers
WHERE Country='Germany'
UNION
SELECT City, Country FROM Suppliers
WHERE Country='Germany'
ORDER BY City;
````
#### SQL UNION ALL Ile WHERE
+ Aşağıdaki SQL ifadesi, hem "Customers" hem de "Suppliers" tablosundan 'Germany' şehirlerini (Tekrar eden değerleri) döndürür.
````sql
SELECT City, Country FROM Customers
WHERE Country='Germany'
UNION ALL
SELECT City, Country FROM Suppliers
WHERE Country='Germany'
ORDER BY City;
````
#### Örnek

+ Aşağıdaki SQL deyimi tüm müşterileri ve tedarikçileri listeler:

````sql
SELECT 'Customer' AS Type, ContactName, City, Country
FROM Customers
UNION
SELECT 'Supplier', ContactName, City, Country
FROM Suppliers;
````
## SQL GROUP BY

+ GROUP BY ifadesi, aynı değerlere sahip satırları "her ülkedeki müşteri sayısını bul" gibi özet satırlarda gruplandırır.
+ GROUP BY ifadesi, sonuç kümesini bir veya daha fazla sütunla gruplandırmak için genellikle toplama işlevleriyle (COUNT(), MAX(), MIN(), SUM(), AVG()) kullanılır.

#### GROUP BY
+ Aşağıdaki SQL deyimi, her ülkedeki müşteri sayısını listeler.
````sql
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country;
````
+ Aşağıdaki SQL deyimi, yüksekten düşüğe doğru sıralanmış olarak her ülkedeki müşteri sayısını listeler.
````sql
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country
ORDER BY COUNT(CustomerID) DESC;
````
#### GROUP BY Ile JOIN
+ Aşağıdaki SQL deyimi, her bir gönderici tarafından gönderilen siparişlerin sayısını listeler.
````sql
SELECT Shippers.ShipperName, COUNT(Orders.OrderID) AS NumberOfOrders FROM Orders
LEFT JOIN Shippers ON Orders.ShipperID = Shippers.ShipperID
GROUP BY ShipperName;
````
## SQL HAVING
+ WHERE anahtar sözcüğü toplama işlevleriyle kullanılamadığından, HAVING yan tümcesi SQL'e eklendi.

#### HAVING 
+ Aşağıdaki SQL deyimi, yüksekten düşüğe doğru sıralanmış olarak her ülkedeki müşteri sayısını listeler (Yalnızca 5'ten fazla müşterisi olan ülkeleri içerir).
````sql
SELECT COUNT(CustomerID), Country
FROM Customers
GROUP BY Country 
HAVING COUNT(CustomerID) > 5 ORDER BY COUNT(CustomerID) DESC;

````
+ Aşağıdaki SQL deyimi, 10'dan fazla sipariş kaydeden çalışanları listeler.
````sql
SELECT Employees.LastName, COUNT(Orders.OrderID) AS NumberOfOrders
FROM (Orders
INNER JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID)
GROUP BY LastName
HAVING COUNT(Orders.OrderID) > 10 ORDER BY NumberOfOrders DESC;
````
+ Aşağıdaki SQL deyimi, "Davolio" veya "Fuller" çalışanlarının 25'ten fazla sipariş kaydettirip kaydetmediğini listeler.

````sql
SELECT Employees.LastName, COUNT(Orders.OrderID) AS NumberOfOrders
FROM Orders
INNER JOIN Employees ON Orders.EmployeeID = Employees.EmployeeID
WHERE LastName = 'Davolio' OR LastName = 'Fuller'
GROUP BY LastName
HAVING COUNT(Orders.OrderID) > 25;
````
## SQL EXISTS
+ EXISTS operatörü, bir alt sorgudaki herhangi bir kaydın varlığını test etmek için kullanılır.
+ EXISTS operatörü, alt sorgu bir veya daha fazla kayıt döndürürse TRUE değerini döndürür.

+ Aşağıdaki SQL ifadesi TRUE değerini döndürür ve ürün fiyatı 20'den az olan tedarikçileri listeler:
````sql
SELECT CompanyName
FROM Suppliers
WHERE EXISTS (SELECT ProductName FROM Products WHERE Products.SupplierID = Suppliers.supplierID AND UnitPrice < 20);
````

+ Aşağıdaki SQL ifadesi TRUE değerini döndürür ve 22'ye eşit bir ürün fiyatına sahip tedarikçileri listeler:
````sql
SELECT CompanyName
FROM Suppliers
WHERE EXISTS (SELECT ProductName FROM Products WHERE Products.SupplierID = Suppliers.supplierID AND UnitPrice = 22);
````

## SQL ANY Ve ALL
+ ANY ve ALL operatörleri, tek bir sütun değeri ile bir dizi başka değer arasında karşılaştırma yapmanızı sağlar.

#### ANY
+ sonuç olarak bir boolean değeri döndürür
+ Alt sorgu değerlerinden HERHANGİ BİRİ koşulu karşılıyorsa TRUE değerini döndürür.

+ Aşağıdaki SQL deyimi, OrderDetails tablosunda Quantity'nin 10'a eşit HERHANGİ bir kaydı bulursa ProductName'i listeler (Quantity sütununda 10'luk bazı değerler olduğundan bu, TRUE değerini döndürür).
````sql
SELECT ProductName
FROM Products
WHERE ProductID = ANY
  (SELECT ProductID
  FROM [Order Details]
  WHERE Quantity = 10);
````

+ Aşağıdaki SQL deyimi, OrderDetails tablosunda Quantity'nin 99'dan büyük HERHANGİ bir kaydı bulursa ProductName'i listeler (Miktar sütununda 99'dan büyük bazı değerler olduğundan bu, TRUE değerini döndürür).
````sql
SELECT ProductName
FROM Products
WHERE ProductID = ANY
  (SELECT ProductID
  FROM [Order Details]
  WHERE Quantity > 99) ORDER BY ProductName;
````

+ Aşağıdaki SQL deyimi, OrderDetails tablosunda Miktar 1000'den büyük HERHANGİ bir kayıt bulursa ÜrünAdı'nı listeler (Miktar sütununun 1000'den büyük değeri olmadığı için bu FALSE döndürür):

````sql
SELECT ProductName
FROM Products
WHERE ProductID = ANY
  (SELECT ProductID
  FROM [Order Details]
  WHERE Quantity > 1000);
````

#### ALL 
+ sonuç olarak bir boolean değeri döndürür.
+ TÜM alt sorgu değerleri koşulu karşılıyorsa TRUE değerini döndürür.
+ SELECT, WHERE ve HAVING ifadeleriyle birlikte kullanılır.
+ ALL, koşulu yalnızca aralıktaki tüm değerler için işlem doğruysa doğru olacağı anlamına gelir.

+ Aşağıdaki SQL deyimi, OrderDetails tablosundaki TÜM kayıtların Quantity değeri 10'a eşitse, ProductName'i listeler. Quantity sütununda birçok farklı değer olduğundan (yalnızca 10 değeri değil) bu, elbette FALSE döndürür:

````sql
SELECT ProductName
FROM Products
WHERE ProductID = ALL
  (SELECT ProductID
  FROM OrderDetails
  WHERE Quantity = 10);
````


## SQL SELECT INTO 

+ SELECT INTO ifadesi, bir tablodaki verileri yeni bir tabloya kopyalar.

+ Aşağıdaki SQL ifadesi, Müşterilerin bir yedek kopyasını oluşturur.

````sql
SELECT * INTO YedekTablo
FROM Customers;
````
+ Aşağıdaki SQL ifadesi, yalnızca birkaç sütunu yeni bir tabloya kopyalar.
````sql
SELECT CustomerName, ContactName INTO CustomersBackup2017
FROM Customers;
````
+ Aşağıdaki SQL ifadesi, yalnızca Alman müşterileri yeni bir tabloya kopyalar.

````sql
SELECT * INTO CustomersGermany
FROM Customers
WHERE Country = 'Germany';
````
+ Aşağıdaki SQL ifadesi, birden fazla tablodaki verileri yeni bir tabloya kopyalar.

````sql
SELECT Customers.CustomerName, Orders.OrderID
INTO CustomersOrderBackup2017
FROM Customers
LEFT JOIN Orders ON Customers.CustomerID = Orders.CustomerID;
````
## SQL INSERT INTO SELECT

+ INSERT INTO SELECT ifadesi, verileri bir tablodan kopyalar ve başka bir tabloya ekler.
+ INSERT INTO SELECT ifadesi, kaynak ve hedef tablolardaki veri türlerinin eşleşmesini gerektirir.

+ Aşağıdaki SQL ifadesi, "Suppliers"i "Customers"e kopyalar (Null hatası verecektir):
````sql
INSERT INTO Customers (ContactName, City, Country)
SELECT ContactName, City, Country FROM Suppliers;
````



## SQL Comments(Yorum Satırı)

### Tek Satırda Yorum Satırı
+ Tek satırlık yorumlar -- ile başlar.
+ -- ile satırın sonu arasındaki herhangi bir metin yok sayılır (yürütülmez).
+ Aşağıdaki örnek, açıklama olarak tek satırlık bir yorum kullanır:

````sql
--Select all:
SELECT * FROM Customers;
````
### Birden fazla Satırda Yorum Satırı
+ Çok satırlı yorumlar /* ile başlar ve */ ile biter.
+ /* ve */ arasındaki herhangi bir metin yok sayılır.
+ Aşağıdaki örnek, açıklama olarak çok satırlı bir yorum kullanır:
````sql
/*Select all the columns
of all the records
in the Customers table:*/
SELECT * FROM Customers;
````
----------------------------------------------------------------------------------------------------------------------------------------------------------------------

# Veri Tabanı Komutları

## CREATE DATABASE(Database Oluşturma)

+ CREATE DATABASE ifadesi, yeni bir SQL veritabanı oluşturmak için kullanılır.
````sql
CREATE DATABASE Veritabanı_ismi;
````

## SQL DROP DATABASE(Database Silme)

+ DROP DATABASE ifadesi, mevcut bir SQL veritabanını bırakmak(Silmek) için kullanılır.

````sql
DROP DATABASE Veritabanı_ismi;
````
## SQL BACKUP DATABASE (Yedek Alma)
+ BACKUP DATABASE ifadesi, SQL Server'da mevcut bir SQL veritabanının tam yedeğini oluşturmak için kullanılır.

````sql
BACKUP DATABASE Veritabanı_ismi
TO DISK = 'DOSYA_YOLU';
````
## SQL CREATE TABLE(Veritabanı için tablo oluşturma)
+ CREATE TABLE ifadesi, bir veritabanında yeni bir tablo oluşturmak için kullanılır.
````sql
CREATE TABLE Persons (
    PersonID int,
    LastName varchar(255),
    FirstName varchar(255),
    Address varchar(255),
    City varchar(255)
);
````
## SQL DROP TABLE(Tablo Silme)
+ DROP TABLE ifadesi, bir veritabanındaki mevcut bir tabloyu bırakmak için kullanılır.

````sql
DROP TABLE Shippers(Tablo_Ismi);
````

## SQL ALTER TABLE
+ ALTER TABLE ifadesi, mevcut bir tablodaki sütunları eklemek, silmek veya değiştirmek için kullanılır.
+ ALTER TABLE ifadesi ayrıca mevcut bir tabloya çeşitli kısıtlamalar eklemek ve bırakmak(Silmek) için kullanılır.

#### ALTER TABLE - ADD Column
+ Aşağıdaki SQL, "Müşteriler" tablosuna bir "E-posta" sütunu ekler:

````sql
ALTER TABLE Customers
ADD Email varchar(255);
````
#### ALTER TABLE - DROP COLUMN
+ Aşağıdaki SQL, "Müşteriler" tablosundan "E-posta" sütununu siler:

````sql
ALTER TABLE Customers
DROP COLUMN Email;
````
#### SQL ALTER TABLE Example
+ Şimdi "Kişiler" tablosuna "DateOfBirth" adlı bir sütun eklemek istiyoruz. Aşağıdaki SQL deyimini kullanıyoruz:

````sql
ALTER TABLE Persons
ADD DateOfBirth date;
````
#### DROP COLUMN Example
+ Ardından, "Kişiler" tablosunda "DateOfBirth" adlı sütunu silmek istiyoruz. Aşağıdaki SQL deyimini kullanıyoruz:

````sql
ALTER TABLE Persons
DROP COLUMN DateOfBirth;
````

# SQL Constraints(Kurallar,Kısıtlama)

+ NOT NULL - Bir sütunun NULL değerine sahip olmamasını sağlar.
+ UNIQUE - Bir sütundaki tüm değerlerin farklı olmasını sağlar.
+ BİRİNCİL ANAHTAR(PK,PRIMARY KEY) - NULL DEĞİL ve BENZERSİZ kombinasyonu. Bir tablodaki her satırı benzersiz bir şekilde tanımlar.
+ YABANCI ANAHTAR(FK,FOREIGN KEY) - Tablolar arasındaki bağlantıları yok edecek eylemleri engeller.
+ CHECK - Bir sütundaki değerlerin belirli bir koşulu karşılamasını sağlar.
+ DEFAULT - Değer belirtilmemişse bir sütun için varsayılan bir değer ayarlar.
+ CREATE INDEX - Veritabanından çok hızlı bir şekilde veri oluşturmak ve almak için kullanılır.

--------------------------------------------------------------------------------------------------------------------------------------------------------------------
## Tablo Oluşturma Sırasında NOT NULL 
+ Aşağıdaki SQL, "Kişiler" tablosu oluşturulduğunda "ID", "LastName" ve "FirstName" sütunlarının NULL değerleri kabul etmemesini sağlar:

````sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255) NOT NULL,
    Age int
);
````
## ALTER TABLE ile NOT NULL(var olan tabloda güncelleme)
+ "Kişiler" tablosu zaten oluşturulduğunda "Yaş" sütununda NULL DEĞİL kısıtlaması oluşturmak için aşağıdaki SQL'i kullanın:
````sql
ALTER TABLE Persons
MODIFY Age int NOT NULL;
````

## Tablo Oluşturma Sırasında SQL UNIQUE(Tekrarlanamaz Veri)
+ Aşağıdaki SQL, "Kişiler" tablosu oluşturulduğunda "Kimlik" sütununda BENZERSİZ bir kısıtlama oluşturur:

````sql
CREATE TABLE Persons (
    ID int NOT NULL UNIQUE,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
````

## ALTER TABLE ile SQL UNIQUE
+ Tablo zaten oluşturulduğunda "ID" sütununda BENZERSİZ bir kısıtlama oluşturmak için aşağıdaki SQL'i kullanın:
````sql
ALTER TABLE Persons
ADD UNIQUE (ID);
````
## SQL PRIMARY KEY(Birincil anahtar)
+ PRIMARY KEY kısıtlaması, bir tablodaki her kaydı benzersiz şekilde tanımlar.
+ Birincil anahtarlar BENZERSİZ değerler içermelidir ve NULL değerler içeremez.
+ Bir tabloda yalnızca BİR birincil anahtar olabilir; ve tabloda, bu birincil anahtar tek veya birden çok sütundan (alanlardan) oluşabilir.
+ Aşağıdaki SQL, "Kişiler" tablosu oluşturulduğunda "Kimlik" sütununda bir BİRİNCİL ANAHTAR oluşturur:

````sql
CREATE TABLE Persons (
    ID int NOT NULL PRIMARY KEY,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int
);
````
## ALTER TABLE ile PRIMARY KEY
+ Tablo zaten Oluşturulmuş "ID" sütununda bir PRIMARY KEY kısıtlaması oluşturmak için aşağıdaki SQL'i kullanın:

````sql
ALTER TABLE Persons
ADD PRIMARY KEY (ID);
````
## DROP PRIMARY KEY
+ Bir PRIMARY KEY kısıtlamasını bırakmak için aşağıdaki SQL'i kullanın:
````sql
ALTER TABLE Persons
DROP PRIMARY KEY;
````
## SQL FOREIGN KEY(Yabancı Anahtar)

+ YABANCI ANAHTAR kısıtlaması, tablolar arasındaki bağlantıları yok edecek eylemleri önlemek için kullanılır.
+ YABANCI ANAHTAR, bir tablodaki, başka bir tablodaki BİRİNCİL ANAHTAR'a başvuran bir alandır (veya alanlar topluluğudur).

+ Yabancı anahtara sahip tabloya alt tablo, birincil anahtara sahip tabloya başvurulan veya ana tablo denir. Aşağıdaki iki tabloya bakın:

| PersonID  | LastName |FirstName|Age|
| ------------- | ------------- |------------- |------------- |
| 1  | Hansen  |Ola|30|
| 2 | Svendson  |Tove|23|
| 3 |Pettersen  |Kari|20|

| OrderID  | OrderNumber |PersonID|
| ------------- | ------------- |------------- |
| 1  | 77895  |3|
| 2 | 44678  |3|
| 3 |22456  |2|
| 4 |24562  |1|

+ "Siparişler" tablosundaki "PersonID" sütununun "Persons" tablosundaki "PersonID" sütununu gösterdiğine dikkat edin.
+ "Kişiler" tablosundaki "PersonID" sütunu, "Kişiler" tablosundaki BİRİNCİL ANAHTARDIR.
+ "Siparişler" tablosundaki "PersonID" sütunu, "Siparişler" tablosundaki bir YABANCI ANAHTARDIR.
+ YABANCI ANAHTAR kısıtlaması, üst tabloda bulunan değerlerden biri olması gerektiğinden, yabancı anahtar sütununa geçersiz verilerin eklenmesini engeller.

## Tablo Oluşturma Sırasında FOREIGN KEY
+ Aşağıdaki SQL, "Siparişler" tablosu oluşturulduğunda "PersonID" sütununda bir YABANCI ANAHTAR oluşturur:
````sql
CREATE TABLE Orders (
    OrderID int NOT NULL PRIMARY KEY,
    OrderNumber int NOT NULL,
    PersonID int FOREIGN KEY REFERENCES Persons(PersonID)
);
````
## ALTER TABLE ile FOREIGN KEY
+  "Siparişler" tablosu zaten oluşturulduğunda "PersonID" sütununda YABANCI ANAHTAR kısıtlaması oluşturmak için aşağıdaki SQL'i kullanın:
````sql
ALTER TABLE Orders
ADD FOREIGN KEY (PersonID) REFERENCES Persons(PersonID);
````

## DROP FOREIGN KEY 
+ YABANCI ANAHTAR kısıtlamasını bırakmak için aşağıdaki SQL'i kullanın:
````sql
ALTER TABLE Orders
DROP CONSTRAINT FK_PersonOrder;
````
## SQL CHECK(Kontrol)
+ Aşağıdaki SQL, "Kişiler" tablosu oluşturulduğunda "Yaş" sütununda bir CHECK kısıtlaması oluşturur. CHECK kısıtlaması, bir kişinin yaşının 18 veya daha büyük olmasını sağlar:
````sql
CREATE TABLE Persons (
    ID int NOT NULL,
    LastName varchar(255) NOT NULL,
    FirstName varchar(255),
    Age int CHECK (Age>=18)
);
````
