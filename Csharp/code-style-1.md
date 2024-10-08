# An argument about C# Code style, braces, lines 

![logo](../pix/viiinzzz48.png){: style="float: left"}
*Մι∩z•thedev* · [Follow](mailto:vinz.thedev@gmail.com)
Published in *Coding* · 6 min read · 1 day ago
___
<span style="font-size:2.5em">👏</span>65k <span style="font-size:2.5em">💬</span>321 <span style="font-size:2.5em">🔖</span> <span style="font-size:2.5em">⤴️</span>
___
## brace mis-alignment

I'm just exposing here, a recurrent frustration of the normal code style enacted by default in VS:

```csharp
//lengthy signature sometimes breaks line
void method(int aaaaaaaa, int bbbbbbbb, int cccccccc,........................, int zzzzzzzz)
{

}
```

...and it can become very lengthy for instance:

```csharp
//lengthy signature using all sort of features
[Aspect1][Aspect2] async Task<(TheResult, Error, Count)[]?> method<GenericType1, GenericType2>(int aaaaaaaa, int bbbbbbbb, int cccccccc,........................, int zzzzzzzz, out Foo bar, out Far boo)
{

}
```

I agree : it's a smell, maybe we should encapsulate the many arguments in a new structure... but what the hell if we won't, it's legible to have many arguments, up to the coder to decide ! So a better presentation is to put each arg on a new line, that way at least the method name becomes visible again as a headline, which is very important when scrolling:

```csharp
//lengthy signature sometimes line break
void method( //opening brace
	int aaaaaaaa,
	int bbbbbbbb,
	int cccccccc,
	........................,
	int zzzzzzzz) //closing brace not aligned plus it is stuck to end of line by default : this is visually discordant, impairing understanding
{

}
```

the way I like it is not much liked by linters... however this is the most logical and readable style:

```csharp
//lengthy signature sometimes line break
void method
( //opening brace
	int aaaaaaaa,
	int bbbbbbbb,
	int cccccccc,
	........................,
	int zzzzzzzz
) //and closing brace aligned, signature scope is cristal clear
{

}
```

## multiline vs one-liner

Whereas the one-liner or the multiline method signature can be debated, according to me struct and record really gain into adopting systematically multiline and well aligned brace style:

```csharp
public record
( //opening brace
	int aaaaaaaa,
	int bbbbbbbb,
	int cccccccc = 10000000,
	........................,
	//int zzzzzzzz = 0 //for the moment I disable this arg
{

}
```

See it's easier to enable/disable members in the signature with simple comment `//`, otherwise in a one-liner you'd have to use `/* ... */`... dirty ! It's even more pregnant for conditional compilation `#if ... #endif` you need multiline.

Back to that the heavily overloaded signature readability issue, I really like the method name to detach from the rest for the sake of scroll navigation readability. So I hate to detach lengthy output type but what the hell, till I refacto it, i can break it as well. 

I generally like putting AOP style class/method attributes on their own line as well. I consider AOP goal, indeed is to reduce complexity, so main code is more readable.

```csharp
[Aspect1][Aspect2]
async Task<(TheResult, Error, Count)[]?>
//let me have a line break here as well, look now method name really detach from the rest
method<GenericType1, GenericType2>(...)
{

}
```

## Conclusion

During the development phase, we go through cycles, `grow -> refacto -> shrink`. Especially during the expanded form, I advocate to keep the code  well spaced out - always. Remember your English teacher surely taught you that while writing an essay.

Don't be stingy with ¶ , a byte or two doesn't bite you. 

¶
Use line breaks !  ¶
¶
and keep your parts
(
	and subparts
	(
	
	) well aligned !
)

...and one last thing, don't forget to call the `little animal with funny long hears, long teeth, that likes carrots and can long jump` ... a `Rabbit`; Once everybody is introduced with the `class Rabbit` it's easier and more readable rather than paraphrasing again and again (maybe wronging) Or if you're a carrot seller just call it the `ICarrotEater` that's enough knowledge in this case.
