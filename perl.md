<!---
	Copyright © 2024 Maciej Matiaszowski <maciej.matiaszowski@gmail.com>

	Verbatim copying and redistribution of this entire page are permitted
	provided this notice is preserved.
-->

## Other developer platform

**Q: Is there any other developer platform where I can find those sources?**

**A:** Yes, it's on [Bitbucket](https://bitbucket.org/Stagyrite/perl-1.0/src/master/). This process of importing Perl 1 has even its history.
Perl 1 was pushed to Bitbucket a long time ago. The author of the push made that particular version better in terms of compiling errors. Then, the repository was removed from Bitbucket, and [people](https://github.com/AnaTofuZ/Perl-1.0/network/members) pushed it to GitHub. That [GitHub](https://github.com/AnaTofuZ/Perl-1.0) repository was left almost intact and [forked](https://github.com/eltikia/Perl-1.0) this year. The forked repositories were fixed to compile. Finally, the valid code was imported back to [Bitbucket](https://bitbucket.org/Stagyrite/perl-1.0/src/master/).

## Compiling

**Q: How to compile it?**

**A:** Start by installing the required packages ('gcc', 'yacc' and 'make') in a target system. It might not compile when you have an old version of make. If you're on Cygwin, check out that you have GNU Make 4.4.1 or so.

Fetch the files from [GitHub](https://github.com/eltikia/Perl-1.0). The project can't built when sources have CRLF line endings. Either don't fetch with CRLF line endings or convert line endings to LF.

```
git config --global core.autocrlf false
git init
git remote add origin https://github.com/Stagyrite/Perl-1.0.git
git pull origin main
```

Now you can compile a 'perl' program.

```
./Configure
make depend
make
```

The same can be done in the 'x2p' subdirectory.

```
cd x2p
cp ../Configure .
./Configure
make depend
make
```

One might want to run all tests from the 't' directory, as those all pass, at least on Cygwin.

## Known bugs

**Q: Are there any known bugs or limitations?**

**A:** Yes, there are, and here's an example. Let's assume you check how much memory _'postgres'_ uses. This can be done by executing:
`echo "q" | top -b | grep "postgres" | awk -F " " '{ memory += $10 } END { print memory }`
Let's assume the numbers were: 0.2, 3.6, 3.5, 0.1, 0.0, 0.0, 3.7, 1.0, 0.6, 0.4, 2.4, 2.5, 2.3, 2.5, 0.4, and 0.4. The output number is 23.6, and it's a valid percentage value. Here's a Perl 1 program generated with the Awk to Perl translator from the 'x2p' subdirectory. It's a slightly modified version of it.
```
#!./perl
eval '$'.$1.'$2;' while $ARGV[0] =~ /^([A-Za-z_]+=)(.*)/ && shift;
                        # process any FOO=bar switches

$, = ' ';               # set output field separator
$\ = "\n";              # set output record separator

while (<>) {
    ($Fld1,$Fld2,$Fld3,$Fld4,$Fld5,$Fld6,$Fld7,$Fld8,$Fld9,$Fld10) = split(' ');
    $memory += $Fld10;
}

print $memory;
```
The output number is now 23.599999999999997868, and that is a slightly different result. The difference is 0.000000000000002132.

## Other versions of Perl 1

**Q: Are there any other repositories with Perl 1 available?**

**A:** Yes, there are other versions of Perl 1, and other pages as well. Here's a quite complete list of them.

1. [GitHub/Stagyrite/Perl-1.0](https://github.com/stagyrite/Perl-1.0)
2. [GitHub/eltikia/Perl-1.0](https://github.com/eltikia/Perl-1.0)
3. [GitHub/Stagyrite/perl-1.0_16](https://github.com/Stagyrite/perl-1.0_16)
4. [GitHub/eltikia/perl-1.0_16](https://github.com/eltikia/perl-1.0_16)
5. [CPAN/perl-1.0_16](https://st.aticpan.org/source/RCLAMP/perl-1.0_16)
6. [GitHub/kaworu/perl1](https://github.com/kaworu/perl1)
4. [GitHub/eltikia/perl1](https://github.com/eltikia/perl1)
4. [ETLA/perl1](https://web.archive.org/web/20160913082457/https://www.etla.org/retroperl/perl1/)

## What are you doing?

**Q: Can you explain what has been done with the Perl 1 repository? I mean the recent commits made by [@Stagyrite](https://github.com/Stagyrite).**

**A:** The refreshed Perl 1 is supposed to run on modern operating systems. It wasn't even compiling at first. A non-compiling AWK to Perl translator was also taken care of. It now compiles on several modern operating systems, and that includes Windows (Cygwin). Multiple compiler warnings were eliminated.

## A subroutine example

**Q: Can you give us an example of a subroutine in Perl? I'm studying for a Java exam and I'd like to know more. Here's a quotation from a handbook.**
> **Different languages handle parameters in different ways. Pass-by-value is used by many languages, including Java. [...] The other approach is pass-by-reference. It is used by default in a few languages, such as Perl.**

**A:** Let's consider what the handbook says, and we need both Perl 1 and Perl 5 interpreters to find out how it works.
### No call-by-reference in Perl 1
A pass-by-reference example wouldn't work in Perl 1, and here is a good try.
```
sub trySwap {
    $temp = $_[0];
    $_[0] = $_[1];
    $_[1] = $temp;
}

$a = 1;
$b = 2;
do trySwap ($a, $b);
print $a;
print $b;
```
This Perl 1 program prints 12 which is different from what we expect.

### Call-by-reference in Perl 5
Call-by-reference is the default Perl 5 mechanism, just like the handbook states.
```
sub swap {
    $temp = $_[0];
    $_[0] = $_[1];
    $_[1] = $temp;
}

$a = 1;
$b = 2;
swap ($a, $b);
print $a;
print $b;
```
It prints 21 just like expected.

### Something similar in Perl 1
Here's a traditional although sophisticated Hello World program.
```
#!./perl

sub printSwapped {
    $temp = $_[0];
    $_[0] = $_[1];
    $_[1] = $temp;
    print $_[0];
    print $_[1];
}

$a = "world\n";
$b = "hello, ";
do printSwapped( $a, $b );
```
Its output is "hello, world" printed in a single line.

## Content about Perl 1

**Q: Is there any content created about Perl 1?**

**A:** Yes, there is. First, I'd like to mention [the original README file](https://raw.githubusercontent.com/Stagyrite/Perl-1.0/main/README). It's from the year 1987 when the Perl 1 was created. Second, you might want to see [a README.chastai file](https://github.com/Stagyrite/Perl-1.0/blob/main/README.chastai). This is from the year 2014. In the year 2024, [a new site](https://stagyrite.github.io/Perl-1.0/ "Stagyrite #124; Perl 1") has been created. It provides my Perl Geek Code, as well as the discussions. Nevertheless, you should take a look at [the code](https://github.com/Stagyrite/Perl-1.0 "Stagyrite/Perl-1.0: 🐪 Perl Kit, Version 1.0"), if interested. Knowledge of Perl programming and compilers would be helpful in this particular task.

## A reason of being

**Q: Is there any reason of being for this project? Can you tell us what is it all about?**

**A:** I'd call developing the Perl 1 compiler my historical approach to the Perl programming language. I want to learn Perl and Raku (Perl 6), and therefore I have to choose a way. These are the personal reasons for the project. Its reason of being is that compilers should be fresh (e.g., themselves compiling). It's also about something one can call poetry, and I mean poetry when it provides a quick result. It would certainly take longer to refresh some other projects (e.g. [Linux kernel ver. 0.01](https://github.com/zavg/linux-0.01)). In Raku, one can get a result that takes fewer lines of code than in Java, as one can see in [a separate discussion](raku "Stagyrite #124; Perl 1").

## First impression

**Q: Can you give us your first impression of the Perl 1 compiler?**

**A:** My first impression would be that what's in Perl 1 is often bogus. It's from the year 1987, and therefore you must be careful to use it anyhow. Numerical operations can lead to an error unexpected nowadays. Perl 1 isn't written in Perl, contrary to new versions of Perl that are written in Perl. One should know translation methods to understand it better and dig into what [YACC](https://en.wikipedia.org/wiki/Yacc "Yacc - Wikipedia") does. The code would give a pretty good impression to somebody skilled in Perl programming and compilers.

## Real user feedback

**Q: Did you receive any feedback from real users?**

**A:** Yes, I received an email when the project [started to compile again](https://github.com/Stagyrite/Perl-1.0/commit/a080e3707af43e140d5a8ae4e1b6424e99fcf1c6 "Make it compile again. · Stagyrite/Perl-1.0@a080e37"). At the point of stating the obvious, the whole development process was done in the year 1997. Nevertheless, the development continues, as Perl 1 doesn't compile without warnings. There have been [a social media post](https://twitter.com/effconia/status/1765400696537354351 "Maciej Matiaszowski on X: &quot;https://t.co/7Bo0uCaBKT&quot; / X") about this project, but I don't try to maintain any contact.

## Background in Perl programming

**Q: What's your background in Perl programming?**

**A:** I had a Perl course when I studied Computer Science at the [University of Wrocław](https://www.ii.uni.wroc.pl/ "Instytut Informatyki Uniwersytetu Wrocławskiego"). Later I used multiple scripting languages during my studies to solve mathematical assignments. When at work, I tried modern languages like [Ruby](https://www.ruby-lang.org/en/ "Ruby Programming Language"), [Python](https://www.python.org/ "Welcome to Python.org"), and [Scala](https://www.scala-lang.org/ "The Scala Programming Language"). Those are similar to Perl, although I still use Java for practical text extraction. My [Perl Geek Code](https://stagyrite.github.io/Perl-1.0/#perl-geek-code "Stagyrite &#124; Perl 1") is turned into tooltiped links with a Java project, although the code was based on [a Perl converter](https://www.xmltwig.org/pgc/ "The Perl Geek Code").

## Starting Perl

**Q: What would you recommend to a person who wants to learn Perl?**

**A:** If you need to learn Perl, a full academic course is what you need. In the particular case of a person who likes to learn Perl, I'd recommend installing a Linux operating system. I'd also give her some books about Perl and Raku to read. One can also join an online paid course.

My approach is historical because I also try the Perl 1 compiler, although I don't recommend it to everyone. It's also related to learning a foreign language because I got books in German. I want to learn German, and therefore I read them.

⬛⚛🍅👺

