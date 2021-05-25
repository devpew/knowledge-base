# CORS

У меня не получается решить проблему CORS с помощью разрешения запросов на стороне бека через `Access-Control-Allow-Origin`

Поэтому я научился решать эту проблему через программу, которая называется `local-cors-proxy` 

Найти ее можно тут - [https://www.npmjs.com/package/local-cors-proxy](https://www.npmjs.com/package/local-cors-proxy)

Она устанавливается глобально через `npm i local-cors-proxy`

После этого в отдельном окне терминала нужно ее запустить

	lcp --proxyUrl http://164.90.190.138:8000 --origin http://localhost:3000

После этого запросы в самом реакте надо поменять

Если было:

	fetch("http://164.90.190.138:8000/home", {

То надо поменять на:

	fetch("http://localhost:8010/proxy/home", {

После этого у меня все начинает работать в Firefox