#Software #Hacking #WebExplotation #Web #Internet 
Hecho por: [[Briseida Guzmán Ramírez]]
# Definición
Can you win in a convincing manner against this chess bot? He won't go easy on you!You can find the challenge [here](http://verbal-sleep.picoctf.net:57518/).
# Hints
- Try understanding the code and how the websocket client is interacting with the server
# Solución
1. Abrimos la pagina web
2. Inspeccionamos la pagina
```html
|   |   |
|---|---|
||<!DOCTYPE html>|
||<html>|
||<head>|
||<title>Chess with WebSockfish</title>|
||<link rel="stylesheet" href="[css/chessboard-1.0.0.min.css](http://verbal-sleep.picoctf.net:57518/css/chessboard-1.0.0.min.css)" />|
||<link rel="stylesheet" href="[css/style.css](http://verbal-sleep.picoctf.net:57518/css/style.css)" />|
||<link rel="stylesheet" href="[css/bootstrap.min.css](http://verbal-sleep.picoctf.net:57518/css/bootstrap.min.css)" />|
||<script src="[js/bootstrap.bundle.min.js](http://verbal-sleep.picoctf.net:57518/js/bootstrap.bundle.min.js)"></script>|
||<script src="[js/jquery-3.7.1.min.js](http://verbal-sleep.picoctf.net:57518/js/jquery-3.7.1.min.js)"></script>|
||<script src="[js/chess.min.js](http://verbal-sleep.picoctf.net:57518/js/chess.min.js)"></script>|
||<script src="[js/chessboard-1.0.0.min.js](http://verbal-sleep.picoctf.net:57518/js/chessboard-1.0.0.min.js)"></script>|
||<script src="[js/stockfish.min.js](http://verbal-sleep.picoctf.net:57518/js/stockfish.min.js)"></script>|
||</head>|
|||
||<body class="mx-5 my-5">|
||<div class="mb-2">|
||<div class="chat-container d-flex align-items-start">|
||<div class="profile-icon">|
||<img src="[img/Fish_svg_icon.svg](http://verbal-sleep.picoctf.net:57518/img/Fish_svg_icon.svg)" alt="Profile" />|
||</div>|
||<div class="chat-bubble ml-2">|
||<p id="chatText">|
||I'm just a fish, but I know a thing or two about chess|
||</p>|
||</div>|
||</div>|
||</div>|
|||
||<div id="board" style="width: 400px"></div>|
|||
||<div|
||class="modal fade"|
||id="imageModal"|
||tabindex="-1"|
||aria-labelledby="imageModalLabel"|
||aria-hidden="true"|
||data-bs-backdrop="static"|
||>|
||<div class="modal-dialog">|
||<div class="modal-content">|
||<div class="modal-header">|
||<h5 class="modal-title" id="imageModalLabel">|
||Promote your pawn to:|
||</h5>|
||</div>|
||<div class="modal-body">|
||<div class="d-flex justify-content-around">|
||<img|
||src="[img/chesspieces/wikipedia/wN.png](http://verbal-sleep.picoctf.net:57518/img/chesspieces/wikipedia/wN.png)"|
||alt="n"|
||class="selectable-image img-thumbnail"|
||/>|
||<img|
||src="[img/chesspieces/wikipedia/wB.png](http://verbal-sleep.picoctf.net:57518/img/chesspieces/wikipedia/wB.png)"|
||alt="b"|
||class="selectable-image img-thumbnail"|
||/>|
||<img|
||src="[img/chesspieces/wikipedia/wR.png](http://verbal-sleep.picoctf.net:57518/img/chesspieces/wikipedia/wR.png)"|
||alt="r"|
||class="selectable-image img-thumbnail"|
||/>|
||<img|
||src="[img/chesspieces/wikipedia/wQ.png](http://verbal-sleep.picoctf.net:57518/img/chesspieces/wikipedia/wQ.png)"|
||alt="q"|
||class="selectable-image img-thumbnail"|
||/>|
||</div>|
||</div>|
||</div>|
||</div>|
||</div>|
|||
||<div id="pgn"> </div>|
|||
||<script>|
||var ws_address = "ws://" + location.hostname + ":" + location.port + "/ws/";|
||const ws = new WebSocket(ws_address);|
|||
||ws.onmessage = (event) => {|
||const message = event.data;|
||updateChat(message);|
||};|
|||
||function sendMessage(message) {|
||ws.send(message);|
||}|
|||
||function updateChat(message) {|
||const chatText = $("#chatText");|
||chatText.text(message);|
||}|
||</script>|
|||
||<script>|
||const STARTPOS =|
||"rnbqkbnr/pppppppp/8/8/8/8/PPPPPPPP/RNBQKBNR w KQkq - 0 1";|
||const DEPTH = 10;|
|||
||var pgn = $('#pgn');|
|||
||var board = Chessboard("board", {|
||draggable: true,|
||position: STARTPOS,|
||onDragStart: onDragStart,|
||onDrop: onDrop,|
||});|
|||
||var game = new Chess(STARTPOS);|
|||
||var stockfish = new Worker("js/stockfish.min.js");|
|||
||stockfish.postMessage("uci");|
|||
||function onDragStart(source, piece, position, orientation) {|
||// do not pick up pieces if the game is over|
||if (game.game_over()) return false;|
|||
||// only pick up pieces for White|
||if (piece.search(/^b/) !== -1) return false;|
||}|
|||
||function showPromotionModal() {|
||return new Promise(function (resolve) {|
||$("#imageModal").modal("show");|
||$(".selectable-image").one("click", function () {|
||var selectedPiece = $(this).attr("alt");|
||$("#imageModal").modal("hide");|
||resolve(selectedPiece);|
||});|
||});|
||}|
|||
||function onDrop(source, target, piece) {|
||if (|
||piece === "wP" &&|
||(target[1] === "8" \| target[1] === "1") &&|
||source[0] === target[0]|
||) {|
||showPromotionModal().then(function (promotion) {|
||game.move({|
||from: source,|
||to: target,|
||promotion: promotion,|
||});|
|||
||board.position(game.fen());|
||pgn.html(game.pgn());|
||window.setTimeout(makeBestMove, 250);|
||return "snapback";|
||});|
||}|
|||
||var move = game.move({|
||from: source,|
||to: target,|
||});|
|||
||// Illegal move|
||if (move === null) return "snapback";|
|||
||pgn.html(game.pgn());|
||window.setTimeout(makeBestMove, 250);|
||}|
|||
||function makeBestMove() {|
||var moves = "";|
||var history = game.history({ verbose: true });|
||for (var i = 0; i < history.length; i++) {|
||var move = history[i];|
||moves +=|
||" " + move.from + move.to + (move.promotion ? move.promotion : "");|
||}|
|||
||stockfish.postMessage("position fen " + STARTPOS + " moves" + moves);|
||stockfish.postMessage("go depth " + DEPTH);|
||}|
|||
||stockfish.onmessage = function (event) {|
||var message;|
||// console.log(event.data);|
||if (event.data.startsWith("bestmove")) {|
||var bestMove = event.data.split(" ")[1];|
||var srcSq = bestMove.slice(0, 2);|
||var dstSq = bestMove.slice(2, 4);|
||var promotion = bestMove.slice(4);|
|||
||game.move({ from: srcSq, to: dstSq, promotion: promotion });|
||board.position(game.fen());|
||} else if (event.data.startsWith(`info depth ${DEPTH}`)) {|
||var splitString = event.data.split(" ");|
||if (event.data.includes("mate")) {|
||message = "mate " + parseInt(splitString[9]);|
||} else {|
||message = "eval " + parseInt(splitString[9]);|
||}|
||sendMessage(message);|
||}|
||};|
||</script>|
||</body>|
||</html>|
|||
```
3. Vamos a consola y escribimos: sendMessage("eval -10000000")
```javascript
sendMessage("eval -10000000")
undefined
```
4. En respuesta el pez nos dirá esto:
Huh???? How can I be losing this badly... I resign... here's your flag: picoCTF{c1i3nt_s1d3_w3b_s0ck3t5_c0789e29}

<º)))><
>Pez ilustrativo jskajs
## Respuesta
picoCTF{c1i3nt_s1d3_w3b_s0ck3t5_c0789e29}