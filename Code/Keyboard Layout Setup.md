## In `/usr/share/X11/xkb/symbols/us-art`:

```
default partial alphanumeric_keys modifier_keys
xkb_symbols "basic" {

    name[Group1]= "English (Arthur Custom)";

    key <TLDE> {	[     grave,	asciitilde	]	};
    key <AE01> {	[	  1,	exclam 		]	};
    key <AE02> {	[	  2,	at		]	};
    key <AE03> {	[	  3,	numbersign	]	};
    key <AE04> {	[	  4,	dollar		]	};
    key <AE05> {	[	  5,	percent		]	};
    key <AE06> {	[	  6,	asciicircum	]	};
    key <AE07> {	[	  7,	ampersand	]	};
    key <AE08> {	[	  8,	asterisk	]	};
    key <AE09> {	[	  9,	parenleft	]	};
    key <AE10> {	[	  0,	parenright	]	};
    key <AE11> {	[     minus,	underscore	]	};
    key <AE12> {	[     equal,	plus		]	};

    key <AD01> {	[	  q,	Q 		]	};
    key <AD02> {	[	  w,	W		]	};
    key <AD03> {	[	  e,	E		]	};
    key <AD04> {	[	  r,	R		]	};
    key <AD05> {	[	  t,	T,  minus		]	};
    key <AD06> {	[	  y,	Y,  plus		]	};
    key <AD07> {	[	  u,	U,  braceleft	]	};
    key <AD08> {	[	  i,	I,  braceright  ]	};
    key <AD09> {	[	  o,	O,  bracketleft	]	};
    key <AD10> {	[	  p,	P,  bracketright]	};
    key <AD11> {	[ bracketleft,	braceleft	]	};
    key <AD12> {	[ bracketright,	braceright	]	};

    key <AC01> {	[	  a,	A 		]	};
    key <AC02> {	[	  s,	S		]	};
    key <AC03> {	[	  d,	D,  parenleft	]	};
    key <AC04> {	[	  f,	F,  parenright	]	};
    key <AC05> {	[	  g,	G,  equal		]	};
    key <AC06> {	[	  h,	H,  KP_Left     ]	};
    key <AC07> {	[	  j,	J,  KP_Down     ]	};
    key <AC08> {	[	  k,	K,  KP_Up		]	};
    key <AC09> {	[	  l,	L,  KP_Right	]	};
    key <AC10> {	[ semicolon,	colon		]	};
    key <AC11> {	[ apostrophe,	quotedbl	]	};

    key <AB01> {	[	  z,	Z 		]	};
    key <AB02> {	[	  x,	X		]	};
    key <AB03> {	[	  c,	C		]	};
    key <AB04> {	[	  v,	V,  BackSpace	]	};
    key <AB05> {	[	  b,	B,  underscore	]	};
    key <AB06> {	[	  n,	N,  Delete		]	};
    key <AB07> {	[	  m,	M		]	};
    key <AB08> {	[     comma,	less		]	};
    key <AB09> {	[    period,	greater		]	};
    key <AB10> {	[     slash,	question	]	};

    key <BKSL> {	[ backslash,         bar	]	};

    include "level3(ralt_switch)"
};
```

## Near the end of `/usr/share/X11/xkb/rules/evdev.xml`:
- Just before `</layoutList>`

```
<layout>
      <configItem>
        <name>us-art</name>
        <shortDescription>US-ART</shortDescription>
        <description>English (Arthur Custom)</description>
        <languageList>
          <iso639Id>eng</iso639Id>
        </languageList>
      </configItem>
    </layout>
```