#Software #Hacking #WebExplotation #Web #Internet 
Hecho por: [[Yo|Adrián Fernando Cuevas Solís]]
# Definición
Welcome to the challenge! In this challenge, you will explore a web application and find an endpoint that exposes a file containing a hidden flag.The application is a simple blog website where you can read articles about various topics, including an article about API Documentation. Your goal is to explore the application and find the endpoint that generates files holding the server’s memory, where a secret flag is hidden.The website is running [picoCTF News](http://verbal-sleep.picoctf.net:62638/).
# Hints
- Explore backend development with us
- The head was dumped.
# Solución
Entramos a la pagina web, y vemos lo que contiene, como a primera vista no vemos nada interesante, empezamos a dar clic en los links que nos encontramos.
Ninguno nos lleva a nada interesante hasta que vemos la documentación [API](http://verbal-sleep.picoctf.net:62638/api-docs/).

Ahí vemos un poco de [[Métodos HTTP (Solicitudes al servidor)|solicitudes al servidor]], y vemos una que nos llama la atención, pues se llama como el problema. Así que la ejecutamos, y nos regresa un archivo; al abrirlo y buscar la palabra 'pico' encontramos la bandera.
## Respuesta
picoCTF{Pat!3nt_15_Th3_K3y_46022a05}