# debounce_throttling

Debugging and Throttling
Both are basically to limit the number of function calls made by an event. Fox example a Click event. This reduced the number of calls and make the UI work faster without any delays, thereby enhancing the user experience.

Debouncing
Sets a certain interval after an even where a function is triggered, so when there is say the timelimit exceeds 100ms after an even a function call will be initialised

Code: Divided into 3 blocks

let counter = 0
const getData () => {
	console.log("Fetching Data..", counter++)
}
// 1) This console.log will log "Fetching Data 0, Fetching Data 1 Fetching Data 2 Fetching Data 3 etc ", analogous to a function call after an event, say after each keystroke while searching on sthe search bar. But as said before it creates a lot of function calls

const debouncing = function (fn, delay){
	let timer
	clearTimeout(timer);
	timer = setTimeout(()=> {
		getData.apply(this, arguments)
	}, delay);
	}
}

//2) here the call back is done with a"delay", so that the function getData is triggred scantly."Apply" is used since there are so many arguments in"counter value", rather than passsing it as each item, it is passed as an "array" of items.

debouncing(getData, 300ms)
// 3)
It is a callback funtion, ie., a function (here, getdata() is passed as an argument of another function








Throttling
It do not wait for a particular period but set a fixed limit or interval after which a particular function call is initiated

Code:

const throttle = (func, limit) => {
	let flag = true
	
// 1) it will run the function once. This will act as a closure( function in javascript can access the reference to a variable in its parent function ) giving access to the flag again inside the function.

	return function(){
		let context = this
		args = arguments
	if ((flag) {
		func.apply (context, args)
		
		
// 2) when the function is called, flag will be made false as shown below
		flag = false
		setTimeout(() => {
			flag = true), limit)
		}
	}
	}
}

const expensive = () = {
	console.log ("Expensive")
}
window.addEventListner ("resize", betterExpensive)
const betterExpensive = throttle (expensive, 100ms)

// 3) here every 100ms the function throttle will be triggered
