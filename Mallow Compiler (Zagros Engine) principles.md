
```mallow
opt fn print str &text {
	if text == none {return none};
	loop char per text {
		#OUTPUT_VAL.asm char
	};
	#OUTPUT.asm;
	return some
}
```

```mallow
	#FUNC.asm fn (rawStr fnName, list param1?, list param2?, codeBlock cb) {
		this.enCapsulate;
	};
```

```mallow
-- data types
$.this = {
	opt = {
		default fn (arg) {
			if arg.hasContent {
				some
			} else {
				none
			}
		},
		impure fn some {
			return self
		},
		impure fn none {
			return self
		}
	};
	bool = {
		impure fn true {
			return self
		},
		impure fn false {
			return self
		}
	}
}
```

```mallow
codeBlock block "{" "}" {
	this.enCapsulate;
	import blocks.:;
	
}
```