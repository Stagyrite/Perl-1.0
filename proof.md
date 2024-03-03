<!---
	Copyright © 2024 Maciej Matiaszowski <maciej.matiaszowski@gmail.com>

	Verbatim copying and redistribution of this entire page are permitted
	provided this notice is preserved.
-->

# Proof of concept

**Q: Is there any proof that it works?**

**A:** Yes, there are tests in [the 't' subdirectory](https://github.com/eltikia/Perl-1.0/tree/main/t) and this is their output.

## ./base.cond
```
1..4
ok 1
ok 2
ok 3
ok 4
```

## ./base.if
```
1..2
ok 1
ok 2
```

## ./base.lex
```
1..7
#1	:x: eq :x:
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
```

## ./base.pat
```
1..2
ok 1
ok 2
```

## ./base.term
```
1..6
ok 1
ok 2
#3	:1: == :1:
ok 3
ok 4
ok 5
ok 6
```

## ./cmd.elsif
```
1..4
ok 1
ok 2
ok 3
ok 4
```

## ./cmd.for
```
1..2
#1	:10: eq :10:
#1	:0 1 2 3 4 5 6 7 8 9 10: eq :0 1 2 3 4 5 6 7 8 9 10:
ok 1
ok 2
```

## ./cmd.mod
```
1..6
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
```

## ./cmd.subval
```
1..12
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
ok 8
ok 9
ok 10
ok 11
ok 12
```

## ./cmd.while
```
1..10
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
ok 8
ok 9
ok 10
```

## ./comp.cmdopt
```
1..40
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
ok 8
ok 9
ok 10
ok 11
ok 12
ok 13
ok 14
ok 15
ok 16
ok 17
ok 18
ok 19
ok 20
ok 21
ok 22
ok 23
ok 24
ok 25
ok 26
ok 27
ok 28
ok 29
ok 30
ok 31
ok 32
ok 33
ok 34
ok 35
ok 36
ok 37
ok 38
ok 39
ok 40
```

## ./comp.cpp
```
1..3
ok 1
ok 2
ok 3
```

## ./comp.decl
```
1..7
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
```

## ./comp.multiline
```
1..5
ok 1
ok 2
ok 3
ok 4
ok 5
```

## ./comp.term
```
1..9
#1	:\n: eq :\n:
ok 1
#2	:#2	:: eq :\n:
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
ok 8
ok 9
```

## ./io.argv
```
1..5
ok 1
ok 2
ok 3
ok 4
ok 5
```

## ./io.fs
```
1..20
ok 1
ok 2
ok 3
ok 4
not ok 5
ok 6
ok 7
ok 8
ok 9
ok 10
ok 11
ok 12
ok 13
ok 14
ok 15
ok 16
ok 17
ok 18
ok 19
ok 20
```

## ./io.inplace
```
1..2
ok 1
ok 2
```

## ./io.print
```
1..11
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
ok 8
ok 9
ok 10
ok 11
```

## ./io.tell
```
1..13
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
ok 8
ok 9
ok 10
ok 11
ok 12
ok 13
```

## ./op.append
```
1..3
#1	:abcdef: eq :abcdef:
ok 1
#2	:abcdefxyz: eq :abcdefxyz:
ok 2
#3	:abcdef: eq :abcdef:
ok 3
```

## ./op.auto
```
1..30
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
ok 8
ok 9
ok 10
ok 11
ok 12
ok 13
ok 14
ok 15
ok 16
ok 17
ok 18
ok 19
ok 20
ok 21
ok 22
ok 23
ok 24
ok 25
ok 26
ok 27
ok 28
ok 29
ok 30
```

## ./op.chop
```
1..2
ok 1
ok 2
```

## ./op.cond
```
1..4
ok 1
ok 2
ok 3
ok 4
```

## ./op.crypt
```
```

## ./op.do
```
1..8
ok 1
#2	:value: eq :value:
ok 2
ok 3
ok 4
#5	:value: eq :value:
ok 5
ok 6
ok 7
#8	:value: eq :value:
ok 8
```

## ./op.each
```
1..2
ok 1
ok 2
```

## ./op.eval
```
1..8
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
ok 8
```

## ./op.exec
```
1..8
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
ok 8
```

## ./op.exp
```
1..6
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
```

## ./op.flip
```
1..8
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
ok 8
```

## ./op.fork
```
1..2
ok 1
ok 2
```

## ./op.goto
```
1..3
#1	:2: == 2
ok 1
#2	:4: == 4
ok 2
#3	/label/ in :Can't find label "foo"--aborting at /tmp/perl-eWqw8Q9 line 1.
ok 3
```

## ./op.int
```
1..4
ok 1
ok 2
ok 3
ok 4
```

## ./op.join
```
1..3
ok 1
ok 2
ok 3
```

## ./op.list
```
1..11
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
ok 8
ok 9
ok 10
#11	1;2;3;4 eq 1;2;3;4
ok 11
```

## ./op.magic
```
1..4
ok 1
ok 2
ok 3
ok 4
```

## ./op.oct
```
1..3
ok 1
ok 2
ok 3
```

## ./op.ord
```
1..2
ok 1
ok 2
```

## ./op.pat
```
1..27
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
ok 8
ok 9
ok 10
ok 11
ok 12
ok 13
ok 14
ok 15
ok 16
ok 17
ok 18
ok 19
ok 20
ok 21
ok 22
ok 23
ok 24
ok 25
ok 26
ok 27
```

## ./op.push
```
1..2
ok 1
ok 2
```

## ./op.repeat
```
1..11
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
ok 7
ok 8
ok 9
ok 10
ok 11
```

## ./op.sleep
```
1..1
ok 1
```

## ./op.split
```
1..6
ok 1
ok 2
ok 3
ok 4
ok 5
ok 6
```

## ./op.sprintf
```
1..1
ok 1
```

## ./op.stat
```
1..28
ok 1
ok 2
ok 3
ok 4
#4	:1708963230: != :1708963231:
ok 5
ok 6
ok 7
ok 8
ok 9
ok 10
ok 11
ok 12
ok 13
ok 14
ok 15
ok 16
ok 17
ok 18
ok 19
ok 20
ok 21
ok 22
ok 23
ok 24
ok 25
ok 26
ok 27
ok 28
```

## ./op.subst
```
1..13
#1	:$x: eq :$x:
ok 1
#2	:foo: eq :foo:
ok 2
#3	:$x foo: eq :$x foo:
ok 3
#4	:bcde: eq :bcde:
#4	:a\n$1f: eq :a\n$1f:
ok 4
ok 5
ok 6
ok 7
ok 8
ok 9
ok 10
ok 11
ok 12
ok 13
```

## ./op.time
```
1..5
ok 1
ok 2
ok 3
ok 4
ok 5
```

## ./op.unshift
```
1..2
ok 1
ok 2
```

⬛⚛🍅👺

