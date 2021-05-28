# localStorage

Для того чтобы хранить что-то в localStorage мы можем использовать

	const name = "devpew"
	localStorage.setItem('nameStorage', name)

После этого данные будут записаны в localStorage. Для того чтобы их оттуда достать мы можем использовать

	const getName = localStorage.getItem('nameStorage')
	console.log(getName);

Чтобы удалить данные из localStorage можно использовать

	localStorage.removeItem('nameStorage')

## JSON stringily and JSON parse

Javascript всегда хранит в localStorage только строку, поэтому если мы хотим передать туда объект то мы должны сначала привести его к виду строки. Для этого мы можем использовать метод 

Например, у нас есть массив объектов:

	const person = [
	    {
	        id: 1,
	        name: 'Ivan',
	        isWork: true
	    },
	    {
	        id: 2,
	        name: 'Andrey',
	        isWork: false
	    },
	    {
	        id: 3,
	        name: 'Kirill',
	        isWork: true
	    }
	]

И если мы сделаем `console.log(person)` то увидим что это массив.

Но мы не можем записать массив в localStorage. Так как localStorage принимает только строки.   

Мы можем преобразовать массив объектов в строку с помощью команды:

	let personString = JSON.stringify(person)
	console.log(personString)

Теперь мы видим что это строка

Для того чтобы преобразовать обратно в массив объектов мы можем использовать

	let personArr = JSON.parse(personString)
	console.log(personArr);

Метод 

	localStorage.clear()

Удалит все из localStorage