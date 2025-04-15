#Software #Hacking #Computación #GeneralSkills
Hecho por: [[Briseida Guzmán Ramírez]]
# Definición
Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/3f0e13f541928f420d9c8c96b06d4dbf7b2fa18b15adbd457108e8c80a1f5883/fixme1.tar.gz).
# Hints
- Cargo is Rust's package manager and will make your life easier. See the getting started page [here](https://doc.rust-lang.org/book/ch01-03-hello-cargo.html)
- [println!](https://doc.rust-lang.org/std/macro.println.html)
- Rust has some pretty great compiler error messages. Read them maybe?
# Solución
1. Descargar usando [[wget]]
```bash
wget https://challenge-files.picoctf.net/c_verbal_sleep/3f0e13f541928f420d9c8c96b06d4dbf7b2fa18b15adbd457108e8c80a1f5883/fixme1.tar.gz
```

2. Sub Carpetas con: 
-tar xvzf fixme1.tar.gz

```bash
brisguz@DESKTOP-8V24E1B:~/SegPrac/pico/part1/rusfix1$ tar xvzf fixme1.tar.gz
fixme1/
fixme1/Cargo.toml
fixme1/Cargo.lock
fixme1/src/
fixme1/src/main.rs
brisguz@DESKTOP-8V24E1B:~/SegPrac/pico/part1/rusfix1$
```

3. Entrar a la carpeta:  cd fixme1
```bash
brisguz@DESKTOP-8V24E1B:~/SegPrac/pico/part1/rusfix1$ cd fixme1
brisguz@DESKTOP-8V24E1B:~/SegPrac/pico/part1/rusfix1/fixme1$
```

4. Descargar:
```bash
sudo apt install cargo
```

5. Poner: cargo build 
-Y va aparecer un código con error:

```bash
brisguz@DESKTOP-8V24E1B:~/SegPrac/pico/part1/rusfix1/fixme1$ cargo build
    Updating crates.io index
  Downloaded either v1.13.0
  Downloaded crossbeam-deque v0.8.5
  Downloaded xor_cryptor v1.2.3
  Downloaded crossbeam-epoch v0.9.18
  Downloaded crossbeam-utils v0.8.20
  Downloaded rayon-core v1.12.1
  Downloaded rayon v1.10.0
  Downloaded 7 crates (388.2 KB) in 2.56s
   Compiling crossbeam-utils v0.8.20
   Compiling rayon-core v1.12.1
   Compiling either v1.13.0
   Compiling crossbeam-epoch v0.9.18
   Compiling crossbeam-deque v0.8.5
   Compiling rayon v1.10.0
   Compiling xor_cryptor v1.2.3
   Compiling rust_proj v0.1.0 (/home/brisguz/SegPrac/pico/part1/rusfix1/fixme1)
error: expected `;`, found keyword `let`
 --> src/main.rs:5:37
  |
5 |     let key = String::from("CSUCKS") // How do we end statements in Rust?
  |                                     ^ help: add `;` here
...
8 |     let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "01", "1c", "7e", "59", "63", "e1", "61", "25", "7f", "5a", "60", "...
  |     --- unexpected token

error: argument never used
  --> src/main.rs:26:9
   |
25 |         ":?", // How do we print out a variable in the println function?
   |         ---- formatting specifier missing
26 |         String::from_utf8_lossy(&decrypted_buffer)
   |         ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^ argument never used

error[E0425]: cannot find value `ret` in this scope
  --> src/main.rs:18:9
   |
18 |         ret; // How do we return in rust?
   |         ^^^ help: a local variable with a similar name exists: `res`

For more information about this error, try `rustc --explain E0425`.
error: could not compile `rust_proj` due to 3 previous errors
brisguz@DESKTOP-8V24E1B:~/SegPrac/pico/part1/rusfix1/fixme1$
```

6. Entrar a : cd src
```bash
brisguz@DESKTOP-8V24E1B:~/SegPrac/pico/part1/rusfix1/fixme1$ cd src
brisguz@DESKTOP-8V24E1B:~/SegPrac/pico/part1/rusfix1/fixme1/src$
```




7. Abrir main.rs y corregir código
-sudo nano main.rs
-Asi es como quedaria el codigo corregido
(1)Le agregue Reurn
(2)Le agregue ; en esta linea:   let key = String::from("CSUCKS");
(3)Cambie la linea de   ":?" a "{}:?"

> Codigo
```javascript
use xor_cryptor::XORCryptor;

fn main() {
    // Key for decryption
    let key = String::from("CSUCKS"); // How do we end statements in Rust?

    // Encrypted flag values
    let hex_values = ["41", "30", "20", "63", "4a", "45", "54", "76", "01", "1c", >
    // Convert the hexadecimal strings to bytes and collect them into a vector
    let encrypted_buffer: Vec<u8> = hex_values.iter()
        .map(|&hex| u8::from_str_radix(hex, 16).unwrap())
        .collect();

    // Create decrpytion object
    let res = XORCryptor::new(&key);
    if res.is_err() {
        return; // How do we return in rust?
    }
    let xrc = res.unwrap();

    // Decrypt flag and print it out
    let decrypted_buffer = xrc.decrypt_vec(encrypted_buffer);
    println!(
        "{}:?", // How do we print out a variable in the println function?
        String::from_utf8_lossy(&decrypted_buffer)
    );
}
```

8. De nuevo: cargo build
```bash
brisguz@DESKTOP-8V24E1B:~/SegPrac/pico/part1/rusfix1/fixme1/src$ cargo build
   Compiling rust_proj v0.1.0 (/home/brisguz/SegPrac/pico/part1/rusfix1/fixme1)
    Finished dev [unoptimized + debuginfo] target(s) in 3.19s
```



9. Uttimos paso: Poner cargo run
```bash
brisguz@DESKTOP-8V24E1B:~/SegPrac/pico/part1/rusfix1/fixme1/src$ cargo run
    Finished dev [unoptimized + debuginfo] target(s) in 0.92s
     Running `/home/brisguz/SegPrac/pico/part1/rusfix1/fixme1/target/debug/rust_proj`
picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}:?
brisguz@DESKTOP-8V24E1B:~/SegPrac/pico/part1/rusfix1/fixme1/src$
```
## Respuesta
picoCTF{4r3_y0u_4_ru$t4c30n_n0w?}