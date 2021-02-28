---
layout: post
title:  Pengenalan Python (part 2)
categories: Basic Python
excerpt: Pada pengenalan python part 2 ini akan membahas tentang dasar-dasar pemrograman python dan package di python
---

Pada pengenalan python part 2 ini akan membahas tentang dasar-dasar pemrograman python dan package di python

## Python Programming

### Conditional Statement

#### Operator Perbandingan (Comparison Operators)

Operasi perbandingan membandingkan beberapa nilai dan, berdasarkan suatu kondisi, mereka menghasilkan Boolean. Saat membandingkan dua nilai, kita dapat menggunakan operator ini:

<ul>
    <li> sama dengan (equal): <b>==</b></li>
    <li> tidak sama dengan (not equal): <b>!=</b></li>
    <li> lebih  dari (greater than): <b>></b></li>
    <li> kurang dari (less than): <b>&lt;</b></li>
    <li> lebih dari sama dengan (greater than or equal to): <b>>=</b></li>
    <li> kurang dari sama dengan (less than or equal to): <b>&lt;=</b></li>
</ul>


```python
# Condition Equal
a = 5
a == 6
```








    False
    


```python
# Greater than Sign

i = 6
i > 5
```


```python
# Inequality Sign

i = 6
i != 6
```


```python
# Use Inequality sign to compare the strings

"ACDC" != "Michael Jackson"
```




    True



Operasi pertidaksamaan juga digunakan untuk membandingkan huruf / kata / simbol sesuai dengan nilai huruf ASCII. Nilai desimal yang diperlihatkan dalam tabel berikut ini mewakili urutan karakter: 
<br>
Misalnya, kode ASCII untuk <b>! </b> adalah 33, sedangkan kode ASCII untuk <b> + </b> adalah 43. Oleh karena itu <b> + </b> lebih besar dari <b>! </b> karena 43 lebih besar dari 33.
<br>
Demikian pula, nilai untuk <b> A </b> adalah 65, dan karena itu nilai untuk <b> B </b> adalah 66: 


```python
# Compare characters

'B' > 'A'
```




    True



Jika ada beberapa huruf, huruf pertama diutamakan dalam urutan:


```python
# Compare characters

'BA' > 'AB'
```




    True



<b> Catatan </b>: Huruf Besar memiliki kode ASCII yang berbeda dengan Huruf Kecil, yang berarti perbandingan antara huruf dalam python peka huruf besar kecil. 

### Branching

**Branching** memungkinkan kita menjalankan pernyataan berbeda untuk input berbeda. Sebaiknya anggap **pernyataan if** sebagai ruang terkunci, jika pernyataannya **Benar** kita dapat memasuki ruang dan program Anda akan menjalankan beberapa tugas yang telah ditentukan, tetapi jika pernyataannya adalah **False** program akan mengabaikan tugas. 

Misalnya, persegi panjang biru yang mewakili konser ACDC. Jika individu tersebut lebih tua dari 18, mereka dapat mengikuti konser ACDC. Jika mereka berusia 18 tahun atau lebih muda dari 18 tahun mereka tidak dapat mengikuti konser.

Gunakan pernyataan kondisi yang dipelajari sebelumnya karena kondisi perlu diperiksa di **pernyataan if**. Sintaksnya sesederhana <code> if <i> pernyataan kondisi </i>: </code>, yang berisi kata <code> if </code>, pernyataan kondisi apa pun, dan titik dua di bagian akhir. Mulai tugas Anda yang perlu dijalankan dalam kondisi ini di baris baru dengan indentasi. Baris kode setelah titik dua dan dengan indentasi hanya akan dieksekusi jika pernyataan **if** adalah **True**. Tugas akan berakhir jika baris kode tidak berisi indentasi.

Dalam kasus di bawah ini, tugas yang dijalankan <code> print (“you can enter”) </code> hanya terjadi jika variabel <code> umur </code> lebih besar dari 18 adalah kasus True karena baris kode ini memiliki indentasi. Namun, pelaksanaan <code> print ("move on") </code> tidak akan dipengaruhi oleh **pernyataan if**. 


```python
# If statement example

umur = 19
#age = 18

#expression that can be true or false
if umur > 18:
    
    #within an indent, we have the expression that is run if the condition is true
    print("you can enter" )

#The statements after the if statement will run regardless if the condition is true or false 
print("move on")
```

    you can enter
    move on
    

Diagram berikut berguna untuk menggambarkan prosesnya. Di sisi kiri, kita melihat apa yang terjadi jika kondisinya <b> Benar </b>. Orang tersebut memasuki konser ACDC yang mewakili kode di indentasi yang sedang dieksekusi; mereka kemudian melanjutkan. Di sisi kanan, kita melihat apa yang terjadi jika kondisinya <b> False </b>; orang tersebut tidak diberikan akses, dan orang tersebut melanjutkan hidup. Dalam kasus ini, segmen kode dalam indentasi tidak berjalan, tetapi pernyataan lainnya dijalankan. 

<img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%203/Images/CondsIf.gif" width="650" />

Pernyataan <code> else </code> menjalankan satu blok kode jika tidak ada ketentuan yang **True** sebelum pernyataan <code> else </code> ini. Mari kita gunakan lagi analogi konser ACDC. Jika pengguna berusia 17 tahun, mereka tidak dapat pergi ke konser ACDC, tetapi dapat pergi ke konser Meatloaf.
Sintaks dari pernyataan <code> else </code> mirip dengan sintaks pernyataan <code> if </code>, seperti <code> else: </code>. Perhatikan bahwa, tidak ada pernyataan kondisi untuk <code> else </code>.
Coba ubah nilai <code> umur </code> untuk melihat apa yang terjadi: 


```python
# Else statement example

age = 18
# age = 19

if age > 18:
    print("you can enter" )
else:
    print("go see Meat Loaf" )
    
print("move on")
```

Prosesnya ditunjukkan di bawah ini, di mana setiap kemungkinan diilustrasikan pada setiap sisi gambar. Di sebelah kiri adalah kasus di mana umur 17, kami menetapkan usia variabel menjadi 17, dan ini sesuai dengan individu yang menghadiri konser Meatloaf. Bagian kanan menunjukkan apa yang terjadi ketika individu berusia di atas 18 tahun, dalam hal ini 19, dan individu tersebut diberikan akses ke konser. 

<img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%203/Images/CondsElse.gif" width="650" />

Pernyataan <code> elif </code>, kependekan dari else if, memungkinkan kita memeriksa kondisi tambahan jika pernyataan kondisi sebelumnya adalah <b> False </b>. Jika kondisi untuk pernyataan <code> elif </code> <b> Benar </b>, ekspresi alternatif akan dijalankan. Pertimbangkan contoh konser, di mana jika individu tersebut berusia 18 tahun mereka akan pergi ke konser Pink Floyd daripada menghadiri ACDC atau konser Meat-loaf. Orang berusia 18 tahun memasuki area tersebut, dan karena mereka tidak lebih dari 18 tahun mereka tidak dapat melihat ACDC, tetapi karena mereka berusia 18 tahun, mereka menghadiri Pink Floyd. Setelah melihat Pink Floyd, mereka melanjutkan. Sintaks dari pernyataan <code> elif </code> serupa karena kita hanya mengubah pernyataan <code> if </code> dalam <code> if </code> menjadi <code> elif </code>. 


```python
# Elif statment example

umur = 18

if umur > 18:
    print("you can enter" )
elif umur == 18:
    print("go see Pink Floyd")
else:
    print("go see Meat Loaf" )
    
print("move on")
```

    go see Pink Floyd
    move on
    

Ketiga kombinasi tersebut ditunjukkan pada gambar di bawah ini. Wilayah paling kiri menunjukkan apa yang terjadi jika individu tersebut berusia kurang dari 18 tahun. Komponen utama menunjukkan kapan individu berusia tepat 18 tahun. Paling kanan menunjukkan kapan individu berusia di atas 18 tahun. 

### Operator Logika (Logical Operator)

Terkadang Kita ingin memeriksa lebih dari satu kondisi sekaligus. Misalnya, kita mungkin ingin memeriksa apakah satu kondisi dan kondisi lainnya **Benar**. Operator logika memungkinkan Anda untuk menggabungkan atau mengubah kondisi. 
<ul>
    <li><code>and</code></li>
    <li><code>or</code></li>
    <li><code>not</code></li>
</ul>

Operator ini diringkas untuk dua variabel menggunakan tabel kebenaran berikut: 

<img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%203/Images/CondsTable.png" width="650" />

Pernyataan <code> dan </code> hanya ** True ** jika kedua ketentuan itu benar. Pernyataan <code> atau </code> benar jika satu kondisinya ** True **. Pernyataan <code> tidak </code> menghasilkan nilai kebenaran yang berlawanan. 

### Looping


Terkadang, Anda mungkin ingin mengulangi operasi tertentu berkali-kali. Eksekusi berulang seperti ini dilakukan oleh <b> loops </b>. Kita akan melihat dua jenis loops, <code> for </code> loops dan <code> while</code> loops.

<h4 id="range">Range</h4>

Sebelum kita membahas loop, mari kita bahas objek <code> range </code>. Sangat membantu untuk memikirkan objek rentang sebagai daftar yang diurutkan. Untuk saat ini, mari kita lihat kasus yang paling sederhana. Jika kami ingin membuat urutan yang berisi tiga elemen yang diurutkan dari 0 hingga 2, kami cukup menggunakan perintah berikut: 


```python
# Use the range

range(3)
```

<img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%203/Images/LoopsRange.png" width="300" />

<h4 id="for">What is <code>for</code> loop?</h4>

Perulangan <code> for </code> memungkinkan Anda mengeksekusi blok kode beberapa kali. Misalnya, Anda akan menggunakan ini jika Anda ingin mencetak setiap elemen dalam daftar.
Mari kita coba menggunakan lingkaran <code> for </code> untuk mencetak semua tahun yang disajikan dalam daftar <code> dates </code>: 

This can be done as follows:


```python
# For loop example

dates = [1982,1980,1973]
N = len(dates)

for i in range(N):
    print(dates[i])     
```

    1982
    1980
    1973
    

Kode dalam indentasi dijalankan <code> N </code> kali, setiap kali nilai <code> i </code> dinaikkan 1 untuk setiap eksekusi. Pernyataan yang dieksekusi adalah <code> print </code> seperti yang ditunjukkan di sini: 

<img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%203/Images/LoopsForRange.gif" width="800" />

Dalam contoh ini kita dapat mencetak urutan angka dari 0 hingga 7: 


```python
# Example of for loop

for i in range(0, 8):
    print(i)
```

Dengan Python kita bisa langsung mengakses elemen dalam daftar sebagai berikut: 


```python
# Exmaple of for loop, loop through list

for year in dates:  
    print(year)   
```

Untuk setiap iterasi, nilai variabel <code> year </code> sama seperti seperti nilai <code> dates[i] </code> pada contoh pertama: 

<img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%203/Images/LoopsForList.gif" width="800">

Kami dapat mengubah elemen dalam `list`: 


```python
# Use for loop to change the elements in list

squares = ['red', 'yellow', 'green', 'purple', 'blue']

for i in range(0, 5):
    print("Before square ", i, 'is',  squares[i])
    squares[i] = 'weight'
    print("After square ", i, 'is',  squares[i])
squares
```

    Before square  0 is red
    After square  0 is weight
    Before square  1 is yellow
    After square  1 is weight
    Before square  2 is green
    After square  2 is weight
    Before square  3 is purple
    After square  3 is weight
    Before square  4 is blue
    After square  4 is weight
    




    ['weight', 'weight', 'weight', 'weight', 'weight']



Kita bisa mengakses index dan elemen `list` sebagai berikut: 


```python
# Loop through the list and iterate on both index and element value

squares=['red', 'yellow', 'green', 'purple', 'blue']

for i, square in enumerate(squares):
    print(i, square)
```

    0 red
    1 yellow
    2 green
    3 purple
    4 blue
    

<h4 id="while">What is <code>while</code> loop?</h4>

Seperti yang Anda lihat, <code> for </code> loops digunakan untuk aliran pengulangan yang terkontrol. Namun, bagaimana jika kita tidak tahu kapan kita ingin menghentikan pengulangan? Bagaimana jika kita ingin terus mengeksekusi blok kode sampai kondisi tertentu terpenuhi? <code> while </code> loops ada sebagai alat untuk eksekusi berulang berdasarkan suatu kondisi. Blok kode akan terus dieksekusi sampai kondisi logis yang diberikan mengembalikan nilai boolean **False**. 

Misalkan kita ingin mengulang melalui list <code> dates </code> dan berhenti pada tahun 1973, kemudian mencetak jumlah iterasi. Ini dapat dilakukan dengan blok kode berikut:


```python
# While Loop Example

dates = [1982, 1980, 1973, 2000]

i = 0
year = 0

while(year != 1973):
    year = dates[i]
    i = i + 1
    print(year)

print("It took ", i ,"repetitions to get out of loop.")
```

    1982
    1980
    1973
    It took  3 repetitions to get out of loop.
    

Perulangan while iterasi hanya sampai kondisi dalam argumen tidak terpenuhi, seperti yang ditunjukkan pada gambar berikut:

<img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%203/Images/LoopsWhile.gif" width="650" />

### Functions

**Functions** merupakan **suatu blok kode** yang dapat digunakan kembali untuk melakukan operasi tertentu yang ada dalam **functions** tersebut. **Functions** bisa digunakan untuk memecah kode dan memungkinkan kita untuk menggunakan kembali kode dalam program yang berbeda. 

Ada dua tipe fungsi di Python:
- <b>Pre-defined functions</b>
- <b>User defined functions</b>

<h3 id="content">What is a Function?</h3>

Berikut adalah aturan sederhana untuk mendefinisikan **function** dengan Python:
- Blok **function** dimulai dengan <code> def </code> diikuti dengan <code> nama </code> fungsi dan tanda kurung <code> () </code>.
- Ada parameter input atau argumen yang harus ditempatkan di dalam tanda kurung ini.
- Kita bisa menentukan parameter di dalam tanda kurung ini.
- Ada satu **function's body** setiap **function** yang dimulai dengan titik dua (<code>: </code>) dan diberi indentasi.
- kita bisa menempatkan dokumentasi (keterangan di depan **function's body**
- Pernyataan <code> return </code> merupakan pernyataan yang bisa mengeluarkan hasil akhir (output) dari fungsi.

Contoh dari sebuah fungsi yang menambahkan ke parameter <code> a </code> mencetak dan outputnya sebagai <code> b </code>: 


```python
# First function example: Add 1 to a and store as b

def add(a):
    """
    add 1 to a
    """
    b = a + 1
    print(a, "if you add one", b)
    return(b)
```

The figure below illustrates the terminology: 

<img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%203/Images/FuncsDefinition.png" width="500" /> 

Kami dapat memperoleh **help** tentang suatu fungsi: 


```python
# Get a help on add function

help(add)
```

    Help on function add in module __main__:
    
    add(a)
        add 1 to a
    
    


```python
# Get a help on add function

add?
```


    [1;31mSignature:[0m [0madd[0m[1;33m([0m[0ma[0m[1;33m)[0m[1;33m[0m[1;33m[0m[0m
    [1;31mDocstring:[0m add 1 to a
    [1;31mFile:[0m      c:\users\gtmir\<ipython-input-46-202ebf69fa00>
    [1;31mType:[0m      function
    


Kita bisa memanggil fungsinya: 


```python
# Call the function add()

add(1)
```

    1 if you add one 2
    




    2



Jika kita memanggil fungsi dengan input baru, kita mendapatkan hasil baru: 


```python
# Call the function add()

add(2)
```

    2 if you add one 3
    




    3



Misalnya, kita dapat membuat **function** yang mengalikan dua angka. Angka-angka tersebut akan diwakili oleh variabel <code> a </code> dan <code> b </code>: 


```python
# Define a function for multiple two numbers

def Mult(a, b):
    c = a * b
    return(c)
```

Fungsi yang sama dapat digunakan untuk tipe data yang berbeda. Misalnya, kita bisa mengalikan dua bilangan bulat: 


```python
# Use mult() multiply two integers

Mult(2, 3)
```




    6



Mengalikan dua angka float


```python
# Use mult() multiply two floats

Mult(10.0, 3.14)
```




    31.400000000000002



Mereplikasi string dengan mengalikannya dengan integer: 


```python
# Use mult() multiply two different type values together

Mult(2, "Michael Jackson ")
```




    'Michael Jackson Michael Jackson '



#### Variables

Input suatu **function** disebut **formal parameter**.

Variabel yang dideklarasikan di dalam **function** disebut **variabel lokal (local variables)**. **Formal parameter** hanya ada di dalam **function** (yaitu titik di mana fungsi dimulai dan berhenti).

Variabel yang dideklarasikan di luar definisi **function** adalah variabel **global (global variable)**, dan nilainya dapat diakses dan dimodifikasi di seluruh program.


```python
# Function Definition

def square(a):
    
    # Local variable b
    b = 1
    c = a * a + b
    print(a, "if you square + 1", c) 
    return(c)
```

<img src="https://s3-api.us-geo.objectstorage.softlayer.net/cf-courses-data/CognitiveClass/PY0101EN/Chapter%203/Images/FuncsVar.png" width="500" />

Kita dapat memanggil **function** tersebut dengan input <b> 3 </b>: 


```python
# Initializes Global variable  

x = 3
# Makes function call and return function a y
y = square(x)
y
```

    3 if you square + 1 10
    




    10



Kita dapat memanggil **function** dengan input <b> 2 </b> dengan cara yang berbeda: 


```python
# Directly enter a number as parameter

square(2)
```

    2 if you square + 1 5
    




    5



Jika tidak ada pernyataan <code> return </code>, fungsi tersebut mengembalikan <code> None </code>. Dua fungsi berikut ini setara: 


```python
# Define functions, one with return value None and other without return value

def MJ():
    y='Michael Jackson'
    
def MJ1():
    y='Michael Jackson'
    return(None)
```


```python
# See the output

MJ()
```


```python
# See the output

MJ1()
```

<h2 id="pre">Pre-defined functions</h2>

Ada banyak fungsi yang telah ditentukan dalam Python, berikut adalah beberapa contohnya:

The <code>print()</code> function:


```python
# Build-in function print()

album_ratings = [10.0, 8.5, 9.5, 7.0, 7.0, 9.5, 9.0, 9.5] 
print(album_ratings)
```

    [10.0, 8.5, 9.5, 7.0, 7.0, 9.5, 9.0, 9.5]
    


```python
help(print)
```

    Help on built-in function print in module builtins:
    
    print(...)
        print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
        
        Prints the values to a stream, or to sys.stdout by default.
        Optional keyword arguments:
        file:  a file-like object (stream); defaults to the current sys.stdout.
        sep:   string inserted between values, default a space.
        end:   string appended after the last value, default a newline.
        flush: whether to forcibly flush the stream.
    
    


```python
print?
```


    [1;31mDocstring:[0m
    print(value, ..., sep=' ', end='\n', file=sys.stdout, flush=False)
    
    Prints the values to a stream, or to sys.stdout by default.
    Optional keyword arguments:
    file:  a file-like object (stream); defaults to the current sys.stdout.
    sep:   string inserted between values, default a space.
    end:   string appended after the last value, default a newline.
    flush: whether to forcibly flush the stream.
    [1;31mType:[0m      builtin_function_or_method
    


The <code>sum()</code> function berguna untuk menjumlahkan semua elemen yang ada di dalam list or tuple:


```python
# Use sum() to add every element in a list or tuple together

sum(album_ratings)
```




    70.0



The <code>len()</code> function berguna untuk menghitung banyaknya elemen dari list or tuple: 


```python
# Show the length of the list or tuple

len(album_ratings)
```




    8



## Python Packages

Python package merupakan kumpulan dari beberapa module python (python module). Beberapa package kadang hanya memiliki satu modul saja.

### What is module?

**Module** merupakan file yang berisi kode dan **function**. File yang berisi kode Python, misalnya: **example.py**, disebut **module**, dan nama **module**-nya akan menjadi **example**.

Kita menggunakan **module** untuk memecah program besar menjadi beberapa file kecil yang lebih mudah dikelola dan diatur. Selain itu, **module** menyediakan kode yang dapat **digunakan kembali**.

Kita dapat mendefinisikan **function** yang paling sering kita gunakan dalam sebuah modul dan meng-**import**-nya, daripada menyalin definisinya ke program yang berbeda.

Misalkan saja kita akan membuat **module** berikut ini dan simpan sebagai example.py. 


```python
# Python Module example

def add(a, b):
   """This program adds two
   numbers and return the result"""

   result = a + b
   return result
```

Di sini, kita telah mendefinisikan **function** `add()` di dalam **module** bernama **example**. **Function** tersebut menggunakan dua parameter angka dan outputnya merupakan hasil penjumlahanya

Kita bisa menggunakan **function** `import` untuk melakukan ini. Berikut adalah contoh meng-import **module** **example** yang sudah kita buat sebelumnya.


```python
import example
```

Ini tidak meng-import nama **function** yang ada dalam **example** secara langsung. Namun, hanya meng-import modul di **example**.

Untuk menggunakan dapat mengakses **function** yang ada di dalam modul kita bisa menggunakan operator titik `.`. Sebagai contoh: 


```python
example.add(4,5.5)
```




    9.5



### Memanggil Package di python

Memanggil package di python sama seperti kita memanggil modul yaitu menggunakan fungsi `import`. Misalnya saja kita ingin memanggil package `pandas` 


```python
import pandas
```

Misalnya saja kita ingin menggunakan fungsi `Series` yang ada di `pandas`


```python
pandas.Series([1,9,20,13])
```




    0     1
    1     9
    2    20
    3    13
    dtype: int64



Kita bisa juga melakukan **rename** pada package yang dipanggil menggunakan `as`. **Rename** ini bertujuan untuk memperpendek nama package saat digunakan untuk mengakses fungsi.


```python
import pandas as pd
```


```python
pandas.Series([1,9,20,13])
```




    0     1
    1     9
    2    20
    3    13
    dtype: int64



Jika kita hanya ingin menagakse fungsi tertentu saja dalam suatu package, bisa menggunakan sintaks `from <package> import <function's name>`. Berikut Ilustrasinya


```python
from pandas import Series
```


```python
Series([1,9,20,13])
```




    0     1
    1     9
    2    20
    3    13
    dtype: int64



Kita bisa mengimport semua fungsi yang ada dalam package dengan menggunakan sintaks `from <package> import *`. Namun cara ini tidak dianjurkan karena jika menggunakan lebih dari satu package maka fungsi satu dan yang lain bisa tumpang tindih. 


```python
from math import *
```

**Package** juga bisa terdiri dari beberapa **subpackage** (**submodules**). Misalnya saja pada package `sklearn` terdapat subpacakge `ensemble`. Untuk mengakses subpackage `ensemble` kita bisa menggunakan operator titik `.`.


```python
import sklearn.ensemble 
```

Kemudian, untuk mengimport fungsi tertentu dari subpackage `ensemble` bisa menggunakan sintaks `from <package>.<subpackage> import <function's name>`.


```python
from sklearn.ensemble import RandomForestClassifier
```

### Menginstall Package

#### pip vs conda

Bagi banyak pengguna, pilihan antara pip dan conda bisa jadi membingungkan. Perbedaan mendasar antara keduanya adalah ini:

* pip menginstal python package  di environment apa pun.
* conda menginstal paket apa pun di environment conda (Anaconda/Miniconda).

Jika kita sudah memiliki instalasi Python yang digunakan, maka pilihan yang akan digunakan mudah:

> Jika kita menginstal Python menggunakan Anaconda atau Miniconda, gunakan conda untuk menginstal Python package. Jika conda memberi tahu bahwa package yang  dinginkan tidak ada, gunakan pip.

Jika Anda menginstal Python dengan cara lain (dari sumber, menggunakan pyenv, virtualenv, dll.), Gunakan pip untuk menginstal Python package. 

#### Menginstall package dari jupyter notebooks

Jika Anda menggunakan jupyter notebook dan ingin menginstal package dengan conda, secara umum sintaksnya adalah 


```python
! conda install <package name>
```

misalnya saja kita ingin menginstall package `numpy`


```python
! conda install numpy
```

Untuk menginstall package dengan pip dalam jupyter notebook, caranya juga sama. Misalnya saja kita akan menginstall package `spacy`


```python
! pip install spacy
```

### Mengakses `help` packages

Untuk melihat bantuan (help) pada suatu package kita bisa menggunkan fungsi `help` kemudian dilanjutkan dengan nama package. Berikut contohnya jika kita ingin melihat bantuan pada package `sklearn`. 


```python
import sklearn
help(sklearn)
```

    Help on package sklearn:
    
    NAME
        sklearn
    
    DESCRIPTION
        Machine learning module for Python
        ==================================
        
        sklearn is a Python module integrating classical machine
        learning algorithms in the tightly-knit world of scientific Python
        packages (numpy, scipy, matplotlib).
        
        It aims to provide simple and efficient solutions to learning problems
        that are accessible to everybody and reusable in various contexts:
        machine-learning as a versatile tool for science and engineering.
        
        See http://scikit-learn.org for complete documentation.
    
    PACKAGE CONTENTS
        __check_build (package)
        _build_utils (package)
        _config
        _distributor_init
        _isotonic
        _loss (package)
        base
        calibration
        cluster (package)
        compose (package)
        conftest
        covariance (package)
        cross_decomposition (package)
        datasets (package)
        decomposition (package)
        discriminant_analysis
        dummy
        ensemble (package)
        exceptions
        experimental (package)
        externals (package)
        feature_extraction (package)
        feature_selection (package)
        gaussian_process (package)
        impute (package)
        inspection (package)
        isotonic
        kernel_approximation
        kernel_ridge
        linear_model (package)
        manifold (package)
        metrics (package)
        mixture (package)
        model_selection (package)
        multiclass
        multioutput
        naive_bayes
        neighbors (package)
        neural_network (package)
        pipeline
        preprocessing (package)
        random_projection
        semi_supervised (package)
        setup
        svm (package)
        tests (package)
        tree (package)
        utils (package)
    
    FUNCTIONS
        clone(estimator, *, safe=True)
            Constructs a new estimator with the same parameters.
            
            Clone does a deep copy of the model in an estimator
            without actually copying attached data. It yields a new estimator
            with the same parameters that has not been fit on any data.
            
            Parameters
            ----------
            estimator : {list, tuple, set} of estimator objects or estimator object
                The estimator or group of estimators to be cloned.
            
            safe : bool, default=True
                If safe is false, clone will fall back to a deep copy on objects
                that are not estimators.
        
        config_context(**new_config)
            Context manager for global scikit-learn configuration
            
            Parameters
            ----------
            assume_finite : bool, optional
                If True, validation for finiteness will be skipped,
                saving time, but leading to potential crashes. If
                False, validation for finiteness will be performed,
                avoiding error.  Global default: False.
            
            working_memory : int, optional
                If set, scikit-learn will attempt to limit the size of temporary arrays
                to this number of MiB (per job when parallelised), often saving both
                computation time and memory on expensive operations that can be
                performed in chunks. Global default: 1024.
            
            print_changed_only : bool, optional
                If True, only the parameters that were set to non-default
                values will be printed when printing an estimator. For example,
                ``print(SVC())`` while True will only print 'SVC()', but would print
                'SVC(C=1.0, cache_size=200, ...)' with all the non-changed parameters
                when False. Default is True.
            
                .. versionchanged:: 0.23
                   Default changed from False to True.
            
            display : {'text', 'diagram'}, optional
                If 'diagram', estimators will be displayed as text in a jupyter lab
                of notebook context. If 'text', estimators will be displayed as
                text. Default is 'text'.
            
                .. versionadded:: 0.23
            
            Notes
            -----
            All settings, not just those presently modified, will be returned to
            their previous values when the context manager is exited. This is not
            thread-safe.
            
            Examples
            --------
            >>> import sklearn
            >>> from sklearn.utils.validation import assert_all_finite
            >>> with sklearn.config_context(assume_finite=True):
            ...     assert_all_finite([float('nan')])
            >>> with sklearn.config_context(assume_finite=True):
            ...     with sklearn.config_context(assume_finite=False):
            ...         assert_all_finite([float('nan')])
            Traceback (most recent call last):
            ...
            ValueError: Input contains NaN, ...
            
            See Also
            --------
            set_config: Set global scikit-learn configuration
            get_config: Retrieve current values of the global configuration
        
        get_config()
            Retrieve current values for configuration set by :func:`set_config`
            
            Returns
            -------
            config : dict
                Keys are parameter names that can be passed to :func:`set_config`.
            
            See Also
            --------
            config_context: Context manager for global scikit-learn configuration
            set_config: Set global scikit-learn configuration
        
        set_config(assume_finite=None, working_memory=None, print_changed_only=None, display=None)
            Set global scikit-learn configuration
            
            .. versionadded:: 0.19
            
            Parameters
            ----------
            assume_finite : bool, optional
                If True, validation for finiteness will be skipped,
                saving time, but leading to potential crashes. If
                False, validation for finiteness will be performed,
                avoiding error.  Global default: False.
            
                .. versionadded:: 0.19
            
            working_memory : int, optional
                If set, scikit-learn will attempt to limit the size of temporary arrays
                to this number of MiB (per job when parallelised), often saving both
                computation time and memory on expensive operations that can be
                performed in chunks. Global default: 1024.
            
                .. versionadded:: 0.20
            
            print_changed_only : bool, optional
                If True, only the parameters that were set to non-default
                values will be printed when printing an estimator. For example,
                ``print(SVC())`` while True will only print 'SVC()' while the default
                behaviour would be to print 'SVC(C=1.0, cache_size=200, ...)' with
                all the non-changed parameters.
            
                .. versionadded:: 0.21
            
            display : {'text', 'diagram'}, optional
                If 'diagram', estimators will be displayed as text in a jupyter lab
                of notebook context. If 'text', estimators will be displayed as
                text. Default is 'text'.
            
                .. versionadded:: 0.23
            
            See Also
            --------
            config_context: Context manager for global scikit-learn configuration
            get_config: Retrieve current values of the global configuration
        
        show_versions()
            Print useful debugging information"
            
            .. versionadded:: 0.20
    
    DATA
        __SKLEARN_SETUP__ = False
        __all__ = ['calibration', 'cluster', 'covariance', 'cross_decompositio...
    
    VERSION
        0.23.1
    
    FILE
        c:\programdata\anaconda3\lib\site-packages\sklearn\__init__.py
    
    
    

Kemudian, jika kita ingin melihat bantuan dari subpackage berikut adalah carany


```python
import sklearn.ensemble
help(sklearn.ensemble)
```

Untuk melihat bantuan dari suatu fungsi dalam package berikut adalah caranya:


```python
from sklearn.ensemble import RandomForestClassifier
help(RandomForestClassifier)
```
