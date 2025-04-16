#Software #Hacking #Computación #GeneralSkills
Hecho por: [[Yolanda Alejandra Sifuentes Flores]]
# Definición
The Rust saga continues? I ask you, can I borrow that, pleeeeeaaaasseeeee?Download the Rust code [here](https://challenge-files.picoctf.net/c_verbal_sleep/babfbee79718a6363826ba86300173ffde6d81577e9dd07d4130c53a7eecf6c3/fixme2.tar.gz).
# Hints
https://doc.rust-lang.org/book/ch04-02-references-and-borrowing.html
# Solución
1. **Instalar Rust [aquí](https://forge.rust-lang.org/infra/release-archives.html)**

2. **Dar permisos (con [[Ejecutar archivos .sh#Damos permiso de ejecución|chmod]]):**
```bash
chmod +x rustup-init.sh
./rustup-init.sh
```

 3. **Después se cierra terminal y se abre una nueva:**

```bash
source $HOME/.cargo/env
rustc --version
cargo --version
```

4. **Descargar zip: (usando [[wget]])**
```bash
wget https://challenge-files.picoctf.net/c_verbal_sleep/babfbee79718a6363826ba86300173ffde6d81577e9dd07d4130c53a7eecf6c3/fixme2.tar.gz
```

5. **Descomprimir:**
```bash
tar -xvzf fixme2.tar.gz
ls
```

6. Ir a **fixme2**:
```bash
cd fixme2
```

7. **Ejecutar con:**
```bash
cargo build
```
8. **Después:** 
```bash
nano main.rs
```
9. **Finalmente**:
```bash
mut
cd src
```
## Respuesta
picoCTF{4r3_y0u_h4v1n5_fun_y31?}
## Referencias
https://forge.rust-lang.org/infra/release-archives.html