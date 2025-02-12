# Definición
There is a nice program that you can talk to by using this command in a shell: `$ nc mercury.picoctf.net 49039`, but it doesn't speak English...

# Hints
- You can practice using netcat with this picoGym problem: [what's a netcat?](https://play.picoctf.org/practice/challenge/34)([[06-what's a net cat]])
- You can practice reading and writing ASCII with this picoGym problem: [Let's Warm Up](https://play.picoctf.org/practice/challenge/22)([[01-Lets Warm Up]])

# Solución
Primero accedemos usando net cat

```cmd
AsumomezaC-picoctf@webshell:~$ nc mercury.picoctf.net 49039
112 
105 
99 
111 
67 
84 
70 
123 
103 
48 
48 
100 
95 
107 
49 
116 
116 
121 
33 
95 
110 
49 
99 
51 
95 
107 
49 
116 
116 
121 
33 
95 
51 
100 
56 
52 
101 
100 
99 
56 
125 
10 
```

Luego tenemos varias opciones:
## Usando cyberchef
> [!info] Decimal a string
> input: salida del cmd
> recipe: from decimal - to string
> output: picoCTF{g00d_k1tty!_n1c3_k1tty!_3d84edc8}
## Respuesta
picoCTF{g00d_k1tty!_n1c3_k1tty!_3d84edc8}