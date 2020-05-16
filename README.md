# TypeScript

> Buat mempersingkat TypeScript = TS dan JavaScript = JS

TS merupakan **superset** dari JS yang di ***compile*** ke JS. ***Superset*** disini maksudnya apa ? Maksudnya itu merupakan basis dari JS yang artinya kita dapat menggunakan semua fungsi dari JS itu sendiri dan dengan tambahan fungsi yang tidak dimiliki oleh JS. Kalau digambarkan menggunakan diagram Venn itu seperti ini.

<center>
    <img src="assets/images/superset.jpg" width="200">
</center>

## Dasar Tipe Data

Untuk tipe data sendiri saya rasa teman-teman tidak asing lagi ya. Bagi yang baru bergabung di dunia Programming, tipe data itu adalah jenis data dari sebuah variable, akan kita sebutkan dibawah ini. Pada umumnya di setiap bahasa dan database selalu akan ketemu istilah ini dan fungsi nya tidak berbeda.

*   Boolean

    Boolean ini hanya berisi nilai benar atau salah. Cara penggunaannya seperti ini.

    ``` typescript
        let isOnline: boolean = false;
    ```

*   Number

    Seperti didalam JS, semua tipe data *number* dalam TS merupakan nilai bilangan mengambang (*floating point*) yang artinya format bilangan yang digunakan untuk merepresentasikan sebuah nilai yang sangat kecil ataupun sangat besar. 

    ``` typescript
        let decimal: number = 6;
        let hex: number = 0xf00d;
        let binary: number = 0b1010;
        let octal: number = 0o744;
    ```

*   String

    Merupakan kumpulan dari huruf atau karakter. Untuk penggunaan dalah TS, sama seperti JS menggunakan double quotes (") atau single quote ('). Penerapannya seperti berikut.

    ``` typescript
        let kata: string = "Belajar";
        kata = "TypeScript";
    ```

    Temen-temen juga dapat menggunakan *template string* menggunakan karakter backtick/backquote (`) seperti berikut.

    ``` typescript
        let fullName: string = `Bob Bobbington`;
        let age: number = 37;
        let sentence: string = `Hello, my name is ${fullName}.

        I'll be ${age + 1} years old next month.`;
    ```

    Contoh cara penggunaan lainnya untuk penggabungan kata menjadi kalimat berdasarkan varibel di atas, seperti berikut.

    ``` typescript
        let sentence: string =
            "Hello, my name is " +
            fullName +
            ".\n\n" +
            "I'll be " +
            (age + 1) +
            " years old next month.";
    ```

*   Array

    Sama seperti bahasa pemrograman lain, array merupakan struktur data yang fungsinya untuk menyimpan sekumpulan data dalam satu wadah yang biasanya berbentuk sebuah variabel. Dan setiap data yang disimpan dalam wadah memiliki indeks untuk mempermudah dalam pemrosesannya, berikut ini cara penerapannya.

    ``` typescript
        let list: number[] = [2,3,5];
    ```
    Atau dapat juga didefiniskan seperti berikut.
    ``` typescript
        let list: Array<number> = [2,3,5]
    ```

*   Tuple

    Tuple merupakan tipe data yang mengijinkan kita untuk mengekspresikan array dengan jumlah elemen yang tetap yang mana diketahui jenis tipe datanya, tapi tidak harus tipe data yang sama. Sebagai contoh, temen-temen mau merepresentasikan sebuah nilai sebagai pasangan tipe data string dan number.

    ``` typescript
        // Deklarasikan tipe tuple
        let x: [string, number];

        // Inisialisasi
        x = ["hello", 10]; // OK

        // Inisialisasi yang salah
        x = [10, "hello"]; // Error
    ```
    Kesimpulannya tipe data number tidak dapat di assign ke dalam tipe string, begitu juga sebaliknya.

    Ketika kita akses elemen yang diketahui indeksnya, maka akan mengambil tipe data yang sesuai.

    ``` typescript
        console.log(x[0].substring(1)); // OK
        console.log(x[1].substring(1)); // Error, 'number' does not have 'substring'
    ```
    Kesimpulannya properti substring tidak ada di tipe data number.

    Ketika akses elemen diluar indeks yang telah di set, maka akan muncul error, seperti berikut ini.

    ```typescript
        x[3] = "world"; // Error, Property '3' does not exist on type '[string, number]'.
        Tuple type '[string, number]' of length '2' has no element at index '3'.

        console.log(x[5].toString()); // Error, Property '5' does not exist on type '[string, number]'.
        Object is possibly 'undefined'.
        Tuple type '[string, number]' of length '2' has no element at index '5'.
    ```

*   Enum

    Sama seperti JS ataupun C#, penggunaanya seperti berikut ini dengan.

    ``` typescript
        enum Color {
            Red,
            Green,
            Blue,
        }

        let c: Color = Color.Green;
    ```

*   Any

    Nah untuk tipe data ini biasanya digunakan ketika kita tidak tahu tipe datanya saat menulis aplikasi. Hal ini bisa terjadi jika kita penggunakan 3rd party libray (sumber kode yang lain). Untuk melakukannya, seperti berikut ini.

    ``` typescript
        let notSure: any = 4;
        notSure = "maybe a string instead";
        notSure = false; // okay, definitely a boolean
    ``` 

*   Void

    Void merupakan agak seperti kebalikan dari any. Biasanya digunakan ketika tidak mengembalikan nilai apapun seperti berikut ini.

    ``` typescript
        function warnUser(): void {
            console.log("This is my warning message");
        }
    ```

*   Null dan Undefined

    Di dalam TS, kedua tipe data ini sebenarnya punya tipe data masing-masing. Seperti void, kedua tipe data ini tidak terlalu berguna untuk diri sendiri.

    ``` typescript
        // Not much else we can assign to these variables!
        let u: undefined = undefined;
        let n: null = null;
    ```