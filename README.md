
# CanvasGUI

Canvas GUI is a copy of [DAT GUI](https://github.com/dataarts/dat.gui) but build for javascript canvas projects.

## Installation

Download the latest under Releases.


## Usage

Basic usage to get started

**Must Include Styles**

```javascript
const styles = { fontFamily: "Roboto", itemHeight: 28, setup: { background: "#0B132B", color: "#4c698d", fontSize: "16px", header: { color: "#839cbc", fontSize: "20px", borderBottom: "#3A506B", paddingBottom: 20 }, steps: { background: "white", selected: "#5BC0BE", } }, profiles: { background: "#090F22", borderBottom: "#4c698d" }, folder: { header: { color: "#4c698d", fontSize: "15.4px", background: "#0B132B" } }, item: { color: "#839cbc", fontSize: "13.2px", background: "#1C2541" }, button: { background: "#1C2541", lineTop: "#5BC0BE", color: "#4c698d", hovered: "#5BC0BE", hoveredColor: "#242f53" }, checkbox: { background: "#242f53", checkedBg: "#5BC0BE", hovered: "rgba(91,192,190,0.3)", width: 18, height: 18 }, input: { background: "#242f53", color: "#4c698d", cursor: "#839cbc", width: 120, height: 22 }, select: { background: "#242f53", color: "#4c698d", hovered: "#3A506B", width: 80, height: 20, }, option: { background: "#242f53", color: "#4c698d", hovered: "#3A506B", hoveredColor: "white", outline: "#0B132B" }, slider: { background: "#242f53", color: "#5BC0BE", slider: "#5BC0BE", hovered: "#3A506B", width: 89, height: 20, leftPadding: 100, input: { width: 43, } } }
```

***If you don't know what to pass as `ctx` you can set it to undefined then inside `draw` you can pass a canvas reference.***

```javascript
 const MyMenu = {
    gravity: 0.5,
    speed: 1000,
}
const name = "GUI"
const version = "1"
const myGui = new MyGUI(ctx, 0, 0, 250, 250, styles, name, version)
const configFolder = myGui.addFolder("Config", true)
configFolder.add("Speed", MyMenu, "speed", "Slider", {
    min: 1000,
    max: 20000,
    step: 1000
})
configFolder.add("Gravity", MyMenu, "gravity", "Input")
const clearRect = true;
function loop() {
    myGui.draw(ctx,clearRect)
    requestAnimationFrame(loop);
}
loop();
```

## Profiles
To save and load profiles.

Must call remember after gui initialization
```javascript
myGui.remember(MyMenu)
```

## Folders

Folders are only supported at the moment. You can **not** add menu items directly without having a folder.

```javascript
folder.add(text, obj, val, type, vals)
```

## Types 
There is 5 different elements to use which are Select, Check, Input, Color and Slider types

### Select
Dropdown list of options.
**Array**
```javascript 
	MyMenu.months = 0//Or
	MyMenu.months = "June"
	myFolder.add("Select", MyMenu, "months", "Select", ["June", "July", "August"])
```
**Object**
```javascript 
	MyMenu.names= 40//Or
	MyMenu.names= "John"
	myFolder.add("Select", MyMenu, "names", "Select", {
		"John":  40,
		"Jack":  80,
		"Jill":  120
	})
```

###  Check
Checkbox for booleans

```javascript
	MyMenu.isDead = false
	myFolder.add("Check", MyMenu, "isDead", "Check")
```

###  Input
User Input

```javascript
	MyMenu.yourName = ""
	myFolder.add("Input", MyMenu, "yourName", "Input")
```

###  Color
Color Picker

```javascript
	MyMenu.nameColor = "#FF0000"//Or
	MyMenu.nameColor = "rgba(255,0,0,1)"
	myFolder.add("Input", MyMenu, "nameColor", "Color")
```

###  Slider

```javascript
	MyMenu.maxHealth = 5000
	myFolder.add("Input", MyMenu, "maxHealth", "Slider",{
		min:  1000,
		max:  20000,
		step:  1000//Optional
	})
```

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License
[MIT](https://choosealicense.com/licenses/mit/)
