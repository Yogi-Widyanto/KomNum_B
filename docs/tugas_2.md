# Numerical Solution of Algebraic and Transcendental Equation

### Metode Bisection

**Metode Bisection**  ini membagi range menjadi 2 bagian, dari dua bagian ini dipilih bagian mana yang mengandung akar sedangkan bagian yang tidak mengandung akar akan dibuang. Hal ini dilakukan berulang-ulang hingga diperoleh suatu akar persamaan.

**Algoritma metode bisection**

1. Definisikan fungsi f(x) yang akan dicari akarnya

2. tentukan range atau nilai a dan b

3. tentukan nilai toleransi dan iterasi maksimum

4. hitung f(a) dan f(b)

5. jika f(a)*f(b)>0 maka proses dihentikan karena tidak ada akar

6. jika f(a)*f(b)<0 maka.................

7. hitung nilai c
   $$
   c =\frac{(a+b)}{2}
   $$
   
8. hitung nilai f(c)

9. Bila f(c).f(a)<0 maka b = c dan f(b)=f(c), bila tidak maka a=c dan f(a)=f(c)

10. Jika |b-a|< e atau iterasi > iterasi maks maka proses dihentikan dan didapatkan akar x, bila tidak, ulangi langkah 6





### Metode Regula Falsi

**Metode regula falsi** adalah

1. Metode pencarian akar persamaan dengan memanfaatkan kemiringan dan selisih tinggi dari dua titik batas range.

2. Dua titik a dan b pada fungsi f(x) digunakan untuk mengestimasi posisi c dari akar interpolasi linier.

3. Dikenal dengan metode False Position

4. Metode ini juga merupakan penyempurna dari metode bisection

**Rumus c dari regula falsi :** 
$$
c = a-f(a) \frac{(b-a)}{f(b)-f(a)}
$$
**Algoritma metode regula falsi** (benerin lagii)

1. Definisikan fungsi f(x) yang akan dicari akarnya

2. tentukan batas atas dan batas bawah 

3. tentukan nilai toleransi dan iterasi maksimum

4. hitung f(a) dan f(b)

5. jika f(a)*f(b)>0 maka proses dihentikan karena tidak ada akar

6. jika f(a)*f(b)<0 maka.................

7. hitung nilai c
   $$
   c =\frac{(a+b)}{2}
   $$
   
8. hitung nilai f(c)

9. Bila f(c).f(a)<0 maka b = c dan f(b)=f(c), bila tidak maka a=c dan f(a)=f(c)

10. Jika |b-a|< e atau iterasi > iterasi maks maka proses dihentikan dan didapatkan akar x, bila tidak, ulangi langkah 6

### Metode Newton Raphson

​				Dalam analisis numerik, metode Newton / Newton-Raphson yang mendapat nama dari Isaac Newton dan Joseph Rapshon, merupakan metode yang paling dikenal untuk mencari akar suatu fungsi *f(x)* dengan pendekatan satu titik dimana fungsi *f(x)* mempunyai turunan.

Prosedur Metode Newton :

menentukan *x_0* sebagai titik awal, kemudian menarik garis lurus yang menyinggung titik *f(x_0)* . Hal ini berakibat garis *I* memotong sumbu *x* di titik *x_1* Setelah itu diulangi langkah sebelumnya tapi sekarang *x_1* dianggap sebagai titik awalnya. Dari mengulang langkah-langkah sebelumnya akan mendapatkan *x_2 , x_3 , ... , x_n* dengan *x_n* yang diperoleh adalah bilangan riil yang merupakan akar atau mendekati akar yang sebenarnya.

persamaan garis *I* : y - y_0 = m(x - x_0)
$$
y - f(x_0) = f'(x_0)(x - x_0)
$$
*x_1* perpotongan garis *I* dengan sumbu - *x*
$$
0 - f(x_0) = f'(x_0)(x - x_0)
$$
*y = 0* dan *x = x_1* maka koordinat titik (*x_1*,0)
$$
- \frac{f(x_0)}{f'(x_0)} = (x_1 - x_0)
$$
sehingga di dapat sebuah rumus :
$$
f'(x_n)=\frac{f(x_n)-0}{f'(x_n)-{x_{n+1}}}
$$
atau dapat diatur kembali menjadi :
$$
x_1 = x_0 - \frac{f(x_0)}{f'(x_0)} , x_2 = x_1 - \frac{f(x_1)}{f'(x_1)}, ... , x_{n+1} = x_{n} - \frac{f(x_{n})}{f'(x_{n})}
$$


### Metode Secant

Metode Newton Raphson memerlukan perhitungan turunan fungsi f’(x). Tidak semua fungsi mudah dicari turunannya terutama fungsi yang bentuknya rumit. Turunan fungsi dapat dihilangkan dengan cara menggantinya dengan bentuk lain yang ekivalen.Modifikasi metode Newton Raphson dinamakan metode Secant.

**Rumus Metode Secant**
$$
x_{r+1}=x_r-\frac{f(x_r)(x_r - x_{r-1})}{f(x_r)-{x_{r+1}}}
$$
**Algoritma Metode Secant**

1. Definisikan f(x)

2. Definisikan toleransi error e dan iterasi maksimum (n)

3. Masukan dua nilai pendekatan awal yang diantaranya terdapat akar yaitu x0 dan x1 ,sebaiknya gunakan metode tabel untuk menjamin titik pendekatanya adalah titik pendekatan yang konvergensinya pada akar persamaan yang diharapkan.

4. Hitung f(x0 ) dan f(x1)

5. Untuk iterasi 1 s/d N :
   $$
   x_{r+1}=x_r-\frac{f(x_r)(x_r - x_{r-1})}{f(x_r)-{x_{r+1}}}
   $$
   
6. $$
   Hitungf(x_{r+1})
   $$

   



### Implementasi

##### Metode Bisection

```python
def bis(a,b,n):
    e = 0.001
    fa = a**2-5*a+6
    fb = b**2-5*b+6
    if fa*fb<0:
        x = (a+b)/2
        fx = x**2-5*x+6
        if fa*fx<0:
            b = x
        elif fx*fb<0:
            a = x

        if abs(a-b)<e:
            print("Jumlah Iterasi : ",n)
            print(x)
        else:
            n+=1
            print("iterasi ke-"+str(n))
            bis(a,b,n)
    else:
        if fa<fb:
            a-=0.1
        elif fb<fa:
            b+=0.1
        bis(a,b,n)

a = float(input("Masukkan nilai a : "))
b = float(input("Masukkan nilai b : "))
bis(a,b,0)
```

##### Metode Regula Falsi

```python
def Regfal(a,b,n):
    e = 0.001
    fa = a**2-5*a+6
    fb = b**2-5*b+6
    if fa*fb<0:
        n+=1
        print("iterasi ke-"+str(n))
        x = ((a*abs(fb))+(b*abs(fa)))/(abs(fa)+abs(fb))
        fx = x**2-5*x+6

        if fa*fx<0:
            b = x
        else:
            a = x
        if abs(a-b)<e:
            print(x)
        else:
            Regfal(a,b,n)
    else:
        if fa<fb:
            a-=0.1
        else:
            b+=0.1
        Regfal(a,b,n)

a = float(input("Masukkan interval a : "))
b = float(input("Masukkan interval b : "))
Regfal(a,b,0)
```

##### Metode Newton Rapshon

```python
#Newton-Raphson
x = float(input("Masukkan nilai awal x : "))
n = 0
e = 0.001
while n>=0:
    print("iterasi saat X"+str(n))
    fx = x**2-5*x+6
    fax = 2*x-5
    x1 = x - (fx/fax)
    if abs(x1-x)<e or n>=100:
        print("Jumlah iterasi : ",n+1)
        print(x)
        break
    else:
        x=x1
    n+=1
```



##### Metode Secant

```python
#Secant
def Secant(a,b,n):
    e = 0.001
    fa = a**2-5*a+6
    fb = b**2-5*b+6
    x = a-((b-a)/(fb-fa))*fa
    fx = x**2-5*x+6
    n+=1
    print("iterasi ke-"+str(n))
    if abs(a-b)<e:
        print("Jumlah iterasi :",n)
        print(x)
    else:
        a=b
        b=x
        Secant(a,b,n)

a = float(input("Masukkan nilai a : "))
b = float(input("Masukkan nilai b : "))
n = 0
Secant(a,b,0)
```





<script type="text/x-mathjax-config">
MathJax.Hub.Config({
  tex2jax: {inlineMath: [['$$','$$']]}
});
</script>
  <script type="text/javascript" async
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-MML-AM_CHTML">
</script>