---
layout: post
title:  Pengenalan Python (part 1)
categories: Basic Python
excerpt: Python adalah bahasa pemrograman tingkat tinggi yang ditafsirkan, berorientasi objek, dengan semantik dinamis. Struktur data bawaan tingkat tinggi, dikombinasikan dengan pengetikan dinamis dan pengikatan dinamis, membuatnya sangat menarik untuk Pengembangan Aplikasi Cepat, serta untuk digunakan sebagai bahasa skrip atau perekat untuk menghubungkan komponen yang ada bersama-sama 
---

Python adalah bahasa pemrograman tingkat tinggi yang ditafsirkan, berorientasi objek, dengan semantik dinamis. Struktur data bawaan tingkat tinggi, dikombinasikan dengan pengetikan dinamis dan pengikatan dinamis, membuatnya sangat menarik untuk Pengembangan Aplikasi Cepat, serta untuk digunakan sebagai bahasa skrip atau perekat untuk menghubungkan komponen yang ada bersama-sama (python.org).

Python biasanya di download dengan tambahan beberapa program atau package yang disebut dengan Python Distribution. Beberapa Contoh Python Distribution adalah

* Cpython
* Anaconda
* Canopy
* Python(x,y)

## Tipe Objek di Python

<a align="center">
    <img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%201/Images/TypesObjects.png" width="600">
</a>

Berikut adalah beberapa contoh sintaksnya:


```python
# Integer

11
```




    11




```python
# Float

2.14
```




    2.14




```python
# String

"Hello, Selamat Datang di kelas Text Analytics!"
```




    'Hello, Selamat Datang di kelas Text Analytics!'




```python
# Type of 12

type(12)
```




    int




```python
type(2.14)
```




    float



Tipe Objek Boolen (Logika)


```python
# Value true

True
```




    True




```python
# Value false

False
```




    False




```python
type(True)
```




    bool




```python
type(False)
```




    bool



## Variables

Seperti bahasa pemrograman lainnya, kita bisa menyimpan suatu nilai dalam **variable** suapaya bisa digunakan kemudian


```python
# Store value into variable

x = 43 + 60 + 16 + 41
y = "aku cinta text analytics"
```

Untuk melihat nilai dari suatu **variable**, kita bisa menaruh nilai tersebut di bagian akhir cell


```python
# Print out the value in variable
y
x
```




    160




```python
# Print out the value in variable
x
y
```




    'aku cinta text analytics'



Secara umum berikut adalah aturan penamaan **variable** dalam python

* Nama **variable** harus diawali dengan suatu huruf atau tanda underscore (_)
* Nama **variable** tidak bisa diawali dengan angka
* Nama **variable** hanya berupa alpha-numeric-character dan underscore (A-z, 0-9, and _ )
* Nama **variable** bersifat case-sensitive (hobi,Hobi dan HOBI merupakan tiga **variable** yang berbeda)


```python
#Contoh nama variable yang benar:
namaku = "Dito"
nama_ku = "Dito"
_nama_ku = "Dito"
namaKu = "Dito"
NAMAKU = "Dito"
namaku2 = "Dito"
```


```python
#Contoh nama variable yang benar:
2namaku = "Alfa"
nama-ku = "Alfa"
nama ku = "Alfa"
```

## Operasi Strings

### Mengenal Strings

String dapat dibuat dengan cara-cara berikut:


```python
# menggunakan tanda petik dua

"Michael Jackson"
```




    'Michael Jackson'




```python
# menggunakan tanda petik satu

'Michael Jackson'
```




    'Michael Jackson'



String dapat berupa angka dan spasi


```python
# angka dan spasi dalam string

'1 2 3 4 5 6 '
```




    '1 2 3 4 5 6 '



String dapat berupa kombinasi dari special character


```python
# Special characters in string
'@#2_#]&*^%$'
```




    '@#2_#]&*^%$'



Kita dapat menyimpan string dalam suatu peubah:


```python
Nama = "Gerry Alfa Dito"
Nama
```




    'Gerry Alfa Dito'



### String Indexing

String dapat dianggap sebagai suatu barisan terurut. Setiap elemen dapat diakses dengan menggunakan index yang berupa bilangan terurut:
```
|G|e|r|r|y| |A|l|f|a|  |D |i |t |o |
|0|1|2|3|4|5|6|7|8|9|10|11|12|13|14|
```

**Sebagai catatan di python indexing selalu dimulai dari nol (0)**


```python
# mengakses elemen pertama (index ke-0)
Nama[0]
```




    'G'




```python
# mengakses elemen keduabelas (dalam hal ini index ke-11 karena index dimulai dari nol)
Nama[11]
```




    'D'



Dalam python kita juga bisa menggunakan **negative index** sebagai berikut:
```
|G  |e  |r  |r  |y  |   |A |l |f |a |  |D |i |t |o |
|-15|-14|-13|-12|-11|-10|-9|-8|-7|-6|-5|-4|-3|-2|-1|
```
Berikut adalah beberapa contohnya


```python
Nama[-1]
```




    'o'




```python
Nama[-12]
```




    'r'




```python
Nama[-8]
```




    'l'



Kita bisa menghitung banyaknya karakter dalam suatu string dengan fungsi `len`


```python
len(Nama)
```




    15



### Strings Slicing

Slicing merupakan proses mengambil beberapa karakter dari suatu String, misalnya saja kita ingin mendapatkan karakter elemen ke-0 sampai ke-4 dan elemen ke-12 sampai ke-15.

**Sebagai catatan, angka pertama merupakan index dan angka kedua merupakan "panjang" dari index samapai ke elemen yang kita inginkan (dimulai dari 1)**


```python
Nama[0:4]
```




    'Gerr'




```python
Nama[11:15]
```




    'Dito'




```python
Nama[0:1]
```




    'G'



### Strings Stride

Stride disini merupakan pengambilan karakter dari suatu string dengan pola tertentu. Misalnya saja kita ingin mengambil karakter yang indexnya merupakan kelipatan 2


```python
# index kelipatan 2
Nama[::2]
```




    'GryAf io'




```python
# index kelipatan 4
Nama[::4]
```




    'Gyfi'



## Strings Escape Sequence

String di python memiliki beberapa special character yang disebut **escape character**, seperti newline (baris baru),  tab, dan backslash.

Newline disimbolkan dengan \n


```python

print("Gerry Alfa Dito \n Indonesia")
```

    Gerry Alfa Dito 
     Indonesia
    

tab disimbolkan dengan \t


```python

print("Gerry Alfa Dito \t Indonesia")
```

    Gerry Alfa Dito 	 Indonesia
    

backslash disimbolkan dengan \\ atau r dan \


```python
print("Gerry Alfa Dito \\ Indonesia")
```

    Gerry Alfa Dito \ Indonesia
    


```python
print(r"Gerry Alfa Dito \ Indonesia")
```

    Gerry Alfa Dito \ Indonesia
    

### Concatenate Strings

Kita bisa menggabungkan (concatenate) Strings dengan menggunakan `+`


```python
Nama+" merupakan orang Indonesia"
```




    'Gerry Alfa Dito merupakan orang Indonesia'



Untuk melakukan replikasi pada string, kita bisa menggunakan angka replikasi beserta operasi perkalian sebelum dan sesudah strings


```python
3*"orang Indonesia "
```




    'orang Indonesia orang Indonesia orang Indonesia '




```python
"orang Indonesia "*3
```




    'orang Indonesia orang Indonesia orang Indonesia '



### Operasi Strings

Operasi strings yang dilakukan disini merupakan operasi strings dasar yang ada di python:

#### Uppercase

Operasi ini digunakan untuk merubah huruf pada string menjadi huruf kapital


```python
A = "Upacara Hari Kemerdekaan Indonesia"
B = A.upper()
print(A) # sebelum uppercase
print(B) #setelah uppercase
```

    Upacara Hari Kemerdekaan Indonesia
    UPACARA HARI KEMERDEKAAN INDONESIA
    

#### Lowercase

Operasi ini digunakan untuk merubah huruf pada string menjadi huruf tidak kapital


```python
A = "Upacara Hari Kemerdekaan Indonesia"
B = A.lower()
print(A) # sebelum lowercase
print(B) #setelah lowercase
```

    Upacara Hari Kemerdekaan Indonesia
    upacara hari kemerdekaan indonesia
    

#### Replace

Operasi ini digunakan untuk **mengganti** sebagian(**substring**)dari strings dengan strings baru


```python
A = "Saya lahir di Indonesia"
B = A.replace("Indonesia","Lampung")
print(A)
print(B)
```

    Saya lahir di Indonesia
    Saya lahir di Lampung
    


```python
BB = A.replace("i","o")
BB
```




    'Saya lahor do Indonesoa'



#### Find

Operasi ini digunakan untuk **menemukan** sebagian dari strings (**substring**) dari strings yang telah tersedia. Output dari operasi ini adalah index terkecil dari **substring** yang dimaksud


```python
Nama = "Gerry Alfa Dito"
Nama.find("Alfa") # output merupakan index terkecil dari Alfa
```




    6




```python
Nama.find("to")
```

Jika **substring** tidak ditemukan maka outputnya adalah -1


```python
Nama.find("kit")
```




    -1



## Data Structure

Data Structures merupakan cara mengatur dan menyimpan data agar dapat diakses dan dikerjakan dengan efisien. Data Structure juga menentukan hubungan antara data, dan operasi yang dapat dilakukan pada data. 

### Tuples

Tuples merupakan data structure yang dapat menyimpan berbagai tipe data (float,integer, dan strings) dalam satu kesatuan. Tuples diawali dan diakhiri dengan `()` dan setiap elemen dipisahkan dengan tanda `,`.

<img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%202/Images/TuplesType.png" width="750" align="center" />


```python
data_diri = ("Nur Khotimah",26,55.7 )
```


```python
type(data_diri)
```




    tuple



Operasi pada Tuples


```python
# Print the type of the tuple you created
print(data_diri)
```

    ('Nur Khotimah', 26, 55.7)
    


```python
# indexing

print(data_diri[0])
print(data_diri[1])
print(data_diri[2])
```

    Nur Khotimah
    26
    55.7
    


```python
# negative indexing

print(data_diri[0])
print(data_diri[1])
print(data_diri[2])
```

    Nur Khotimah
    26
    55.7
    


```python
# Concatenate two tuples

data_diri2 = data_diri + ("nonton_drakor", 8)
data_diri2
```




    ('Nur Khotimah', 26, 55.7, 'nonton_drakor', 8)



### Lists

Lists merupakan data structure yang dapat menyimpan berbagai tipe data/objek (float,integer,strings,tuples,dan lists) dalam satu kesatuan. Lists diawali dan diakhiri dengan `[]` dan setiap elemen dipisahkan dengan tanda `,`.

<img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%202/Images/ListsIndex.png" width="1000" />


```python
data_diri = ["Nur Khotimah",26,55.7,("tidur","nonton_drakor"),[1,2]]
data_diri
```




    ['Nur Khotimah', 26, 55.7, ('tidur', 'nonton_drakor'), [1, 2]]



Operasi pada list


```python
# Print the elements on each index

print('the same element using negative and positive indexing:\n Postive:',data_diri[0],
'\n Negative:' , data_diri[-5]  )
print('the same element using negative and positive indexing:\n Postive:',data_diri[1],
'\n Negative:' , data_diri[-4]  )
print('the same element using negative and positive indexing:\n Postive:',data_diri[2],
'\n Negative:' , data_diri[-3]  )
```

    the same element using negative and positive indexing:
     Postive: Nur Khotimah 
     Negative: Nur Khotimah
    the same element using negative and positive indexing:
     Postive: 26 
     Negative: 26
    the same element using negative and positive indexing:
     Postive: 55.7 
     Negative: 55.7
    


```python
# Use extend to add elements to list

data_diri = ["Nur Khotimah",26,55.7,("tidur","nonton_drakor"),[1,2]]
data_diri.extend(['pop', 10])
data_diri
```




    ['Nur Khotimah', 26, 55.7, ('tidur', 'nonton_drakor'), [1, 2], 'pop', 10]




```python
# Use append to add elements to list

data_diri = ["Nur Khotimah",26,55.7,("tidur","nonton_drakor"),[1,2]]
data_diri.append(['pop', 10])
data_diri
```




    ['Nur Khotimah', 26, 55.7, ('tidur', 'nonton_drakor'), [1, 2], ['pop', 10]]



### Dictionaries

Dictionaries merupakan data structure yang dapat menyimpan berbagai tipe data/objek (float,integer,strings,tuples,dan lists) dalam satu kesatuan. Dictionaries diawali dan diakhiri dengan `{}` dan setiap elemen dipisahkan dengan tanda `,`. Setiap elemen dari Dictionaries terdiri dari **key** dan **value** yang dipisahkan dengan simbol `:`. Berikut adalah perbandingan antara Lists dan Dictionaries

<img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%202/Images/DictsList.png" width="650" />


```python
# Create the dictionary

data_mahasiswa = {"Nama": "Nur Khotimah", "Umur": 27, "Hobi": ["nonton drakor","tidur"], "Angka favorit": (7, 13, 17)}
data_mahasiswa
```




    {'Nama': 'Nur Khotimah',
     'Umur': 27,
     'Hobi': ['nonton drakor', 'tidur'],
     'Angka favorit': (7, 13, 17)}



Operasi dalam dictionaries


```python
# Access to the value by the key

data_mahasiswa["Nama"]
```




    'Nur Khotimah'




```python
# Access to the value by the key

data_mahasiswa["Angka favorit"]
```




    (7, 13, 17)




```python
# Get all the keys in dictionary

data_mahasiswa.keys() 
```




    dict_keys(['Nama', 'Umur', 'Hobi', 'Angka favorit'])




```python
data_mahasiswa.values() 
```




    dict_values(['Nur Khotimah', 27, ['nonton drakor', 'tidur'], (7, 13, 17)])




```python
# Append value with key into dictionary
data_mahasiswa["Tahun Masuk"]=2020
data_mahasiswa
```




    {'Nama': 'Nur Khotimah',
     'Umur': 27,
     'Hobi': ['nonton drakor', 'tidur'],
     'Angka favorit': (7, 13, 17),
     'Tahun Masuk': 2020}



### Sets

Sets merupakan data structure yang dapat menyimpan berbagai tipe data/objek (float,integer,strings,tuples,dan lists) dalam satu kesatuan secara **UNIQUE**. Sets diawali dan diakhiri dengan `{}` dan setiap elemen dipisahkan dengan tanda `,`.


```python
jenis_musik = {"pop", "rock", "soul", "hard rock", "rock", "R&B", "rock", "disco"}
jenis_musik
```




    {'R&B', 'disco', 'hard rock', 'pop', 'rock', 'soul'}



<img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%202/Images/SetsUnique.png" width="1100" />


```python
# Convert list to set
jenis_musik = set(["pop", "pop", "rock", "folk rock", "hard rock", "soul", \
                    "progressive rock", "soft rock", "R&B", "disco"])
jenis_musik
```




    {'R&B',
     'disco',
     'folk rock',
     'hard rock',
     'pop',
     'progressive rock',
     'rock',
     'soft rock',
     'soul'}



## Referensi


[Python.org](https://www.python.org/)
<br>
[datacamp.com](https://www.datacamp.com/) 
<br>
[Cognitive Class](https://cognitiveclass.ai/)
