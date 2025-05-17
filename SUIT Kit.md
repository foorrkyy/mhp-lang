```xml
<session>
	<meta></meta>
	<window width="60%" height="60%">
		<meta>
			<title>Demo</title>
		</meta>
		<box name="toolbar" style="display: flex">
			<button>Option 1</button>
			<button>Option 3</button>
			<button>Option 4</button>
			<spacer />
			<button>Option 5</button>
		</box>
		<box name="banner">
			<input type="select">
					<options>
					<option>Home</option>
						<option>Settings</option>
						<option>Help</option>
				</options>
			</input>
			<input type="search" placeholder="search for anything">
				<button width="0.8em" height="0.6em" type="submit" path="M 0.2em 0.2em, circ 0.2em, M 0.2em 0.4em, L 0.3em 0.8em" style="border: 0.2em solid black; align-self: end" >
				</button>
			</input>
		</box>
		<box name="container">
			<grid>
				<columns>
					<column></column>
					<column></column>
				</columns>
				<rows>
					<row></row>
					<row></row>
					<row></row>
				</rows>
			</grid>
			<button rect="2em 1em">
			</button>
		</box>
	</window>
</session>
```
* Session: the app session that includes all windows.
* window: app window. `Display: flex` by default
* box: just a casual element like `<div></div>` in html. `display: block` by default
* button: button. Shape attributes like `rect` in this example prevent the default appearance to be executed and execute the shape specified

```css
.banner{
	width: 100%;
	height: 20%;
	background-color:oklch(85% -0.4 0);
}
.container button{
	fill: none;
	border: 0.2em solid oklch(80% -0.4 0);
}
```

css is usable.

MHP integration:

We can code inline:

```mhp
#[output = suit];
<session>
	<window>
		<text>
			<# this.(weight, height) = ("200px", "100px");
			echo "Hello World";
			#>
		</text>
	</window>
</session>
```
*You'll need the `Campfire` server for that feature*.

Or parse:

```mhp
import suit;
app1 = suit.parse "myapp.xml";
app2 = suit.parse "ui.suit";

app1.run;
app2.run;
```

Or explicitly type:

```mhp
import suit;
mut ses = suit.create "session";
mut win = suit.create "window";
mut txt = suit.create "text";
txt.append "Hello world";
win.append txt;
ses.append win;
suit.run ses;
```

Or:

```mhp
-- Create UI elements with one line
(session, window, text) = suit.create ("session", "window", "text");

text.append "Hello World";
window.append text;
session.append window;

suit.run session;
```