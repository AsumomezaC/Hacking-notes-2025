#Software #Hacking #Computación #GeneralSkills
Hecho por: [[Yolanda Alejandra Sifuentes Flores]]
# Definición
Have you heard of Rust? Fix the syntax errors in this Rust file to print the flag!Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/dcdaf491b35c1d0f5075e9583edbbb7aaea1dffb6ad32bc000e4d87b5200ff7b/fixme3.tar.gz).
# Hints
Read the comments...darn it!
# Solución
Se descomprime el archivo y se corrige el error de sintaxis en el código Rust eliminando el comentario que impedía la ejecución de la función principal:

1. Descomprimir el archivo:
```bash
tar -xzvf fixme3.tar.gz
```

2. Editar el archivo `fixme3.rs` para quitar el comentario de la función `main`:
```rust
fn main() {
    let x = 10;
    if x == 10 {
        println!("picoCTF{n0w_y0uv3_f1x3d_1h3m_411}");
    } else {
        println!("Not ten!");
    }
}
```

3. Compilar y ejecutar el programa:
```bash
rustc fixme3.rs
./fixme3
```
## Respuesta
picoCTF{n0w_y0uv3_f1x3d_1h3m_411}