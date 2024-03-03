<!---
	Copyright © 2024 Maciej Matiaszowski <maciej.matiaszowski@gmail.com>

	Verbatim copying and redistribution of this entire page are permitted
	provided this notice is preserved.
-->

# Raku Programming Language

**Q: There are new versions of Perl, and I mean Raku (Perl 6). Perl 1, which is being developed here, is retro software. Can you give us some examples of Raku programming?**

**A:** Yes, Perl 1 comes from the year 1987, and Raku is from 2018. That seems like 31 years of development. Here are examples of Raku programming taken from [a modern Perl course](https://www.udemy.com/course/the-complete-perl-programming-course/ "The Complete Perl Programming Course &#124; Udemy"). Examples have an example usage, the source code, and an example output (or interactive session).

## ./name.raku

```
#!/usr/bin/env raku
use v6.d;

sub MAIN() {
        my $name = prompt "Wie ist deine Name? ";
        say "Willkommen, ", $name, "!"
}
```

```
Wie ist deine Name? Matze
Willkommen, Matze!
```

## ./nummer_vermutung.raku 50

```
#!/usr/bin/env raku
use v6.d;

sub MAIN($maximum = 100) {
        my $geheimnummer = $maximum.rand.Int;
        say "Hinweis: ", $geheimnummer;

        loop {
                my $vermutung = prompt "Wie ist die Nummer? ";
                last unless $vermutung != $geheimnummer;

                if ($vermutung < $geheimnummer) {
                        say "Falsch. Es ist zu wenig.";
                } else {
                        say "Falsch. Es ist zu viel.";
                }

        }

        say "Richtig!";
}
```

```
Hinweis: 37
Wie ist die Nummer? 33
Falsch. Es ist zu wenig.
Wie ist die Nummer? 44
Falsch. Es ist zu viel.
Wie ist die Nummer? 37
Richtig!
```

## ./umkehren.raku perl

```
#!/usr/bin/env raku
use v6.d;

# Hier können Sie Ihre Mitteilung geben.

sub MAIN($mitteilung) {
    # Kehr die Mitteilung um.

    loop (my $i = $mitteilung.chars - 1; $i >= 0; $i--) {
        say substr $mitteilung, $i, 1
    }

 }
```

```
l
r
e
p
```

## ./chdir.raku

```
#!/usr/bin/env raku
use v6.d;

sub MAIN($irgendwo = 'irgendwo') {
    # Hier ist genau '$*HOME'.
    my $tiefer = $*HOME.add: $irgendwo;
    chdir($tiefer) || die $tiefer ~ ': Es gibt nicht was Sie wollen.';
    say $*CWD;
}
```

## ./join.raku

```
#!/usr/bin/env raku
use v6.d;

sub MAIN(Str $inputText, Int $times) {
    my $outputList = $inputText xx $times.Int;
    my $outputText = $outputList.join: ',';
    say $outputText;
}
```

## ./deck.raku
```
#!/usr/bin/env raku
use v6.d;

sub MAIN() {
    say (< ♤ ♡ ♢ ♧ > X ( 2, 3, 4, 5, 6, 7, 8, 9, 10, 'jack', 'queen', 'king', 'ace' ));
}
```
### ./regex.raku 'Name: Jane Doe, Age: 41, Email: john.doe@email.com END'
```
#!/usr/bin/env raku
use v6.d;

sub MAIN($input) {
    # Name: <John> <Doe>, Age: <25>, Email: <john.doe@email.com>
    say $input ~~ rx/"Name: "\w+\s\w+", Age: "\d+", Email: "<-[ \s ]>+/;
}
```
```
｢Name: Jane Doe, Age: 41, Email: john.doe@email.com｣
```

## Bio

**Q: I read your bio on [Twitter](https://twitter.com/effconia "Maciej Matiaszowski (@effconia) / X"). Do the emojis have something in common with Perl?**

⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛
⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛
⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛
⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛⬛
⚛🍅⚛🍅🍅⚛🍅🍅🍅⚛🍅🍅🍅🍅👺👺👺👺

**A:** Indeed, those are a result of the following Raku program.

```
say "⬛" x 73 ~ (for 1..4 -> $i { "⚛" ~ "🍅" x $i }) ~ "👺" x 4;
```

Let's examine all the parts. First, it prints a black square emoji 73 times. The black or graphite colour should resemble GitHub. The graphite colour encourages writing, and I do mean programming by that. 73 is 80% of 91, and the total number of emoji characters is 91. The widely known 80-20 rule, or the Pareto Principle, was applied.

The second part contains a loop (for 1..4 -> $i { "⚛" ~ "🍅" x $i }). It produces a list of 4 atoms in 10 tomatoes. Note that the "tomato" word consists only of characters from the "atom" word. The idea is taken from a modern painting. Atom can mean atheism, and I read a lot about atheism.

The last part 👺 is a Japanese goblin. Together with the atom emoji, it can represent atheism. It also means fourfaced, as one can be doublefaced, triplefaced, or even fourfaced. This idea was taken from a discussion about a modern painting.

By not sticking to the constants, one can generate more bios. One last thing to do would be to remove the whitespaces.

A shortened version of this bio is available on every one of my GitHub pages. ⬛⚛🍅👺 works usually as a footer but also as a header in the case of [my GitHub profile](https://github.com/Stagyrite/Stagyrite "Stagyrite/stagyrite: 🧪 @Stagyrite profile").

Let's consider a fictitious bio of Aimdugud, a bird god in the shadow of the comet. I'd replace black squares with comets, and goblins with birds.

```
say "☄️" x 73 ~ (for 1..4 -> $i { "⚛" ~ "🍅" x $i }) ~ "🐦" x 4;
```

☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️
☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️
☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️
☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️☄️
⚛🍅⚛🍅🍅⚛🍅🍅🍅⚛🍅🍅🍅🍅🐦🐦🐦🐦

⬛⚛🍅👺

