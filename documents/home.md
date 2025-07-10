# Adaptive

Adaptive is a new take on Kotlin Multiplatform, a greenfield development with the goal
to let us comfortably write full-stack, pure-Kotlin applications without relying
on third-party, platform-dependent libraries.

I know that writing everything myself is a controversial topic, and many will
say: "Don't reinvent the wheel."

While there's some truth to that, let me ask you:

* Do today's 40-ton trucks run on the wooden wheels of medieval wagons?
* Why are there 3 million packages on NPM?

Currently, Adaptive is under the initial development, not ready for the broader
public. It only includes what I’ve needed so far, I’ve taken some shortcuts,
and—to be honest—I’ve made some bad decisions along the way that I haven’t fixed yet.

That said, it works, and the list of features already implemented is really-really long.

## Adaptive is independent

Actually, in more than one sense.

Everything you see on this site uses these, and only these, runtime dependencies:

* kotlinx.coroutines
* kotlinx.datetime
* kotlinx.io
* Ktor + logback (Ktor needs logging facade)

What's more, all the features are designed to work on Android, iOS and Desktop as well. (Though
some implementations are missing for those platforms).

That's it. No Compose, no React, no other platform-dependent third party libraries. Just what
the given platform offers, Kotlin Multiplatform and Adaptive.

In addition, the UI layouts are platform-independent, all calculations are performed by
Kotlin code, so the result should look the very same everywhere.

## Adaptive is natural

One of the main goals of the project is to be able to write code naturally, and the
code should be easy to read, it should show intention, instead of syntax.

This is achieved with the support of a Kotlin compiler plugin (see: [kotlin-compiler-plugin](def://))
that does most of the heavy lifting.

This code shows some concepts:

```kotlin
@Adaptive
fun selectInputPlaygroundForm(
    form: AdatFormViewBackend<SelectPlaygroundConfig>
) {

    val template = SelectPlaygroundConfig()

    localContext(form) {
    
        column {
            gap { 16.dp } .. padding { 16.dp }
        
            intEditor { template.optionCount } .. width { 200.dp }
            markdownHint("300ish is fine, at 1000 it starts to be slow in Safari")
        
            booleanEditor { template.isInConstraintError }
            booleanEditor { template.isDisabled }
         
            intEditor { template.selectItem }
            markdownHint("pre-select the item with this index")
        }
    }
}
```

## Adaptive is truly multi-platform (well, will be)

As I write this the about 90% of the code is in `commonMain`.

Adaptive works well on browser. I had a working proof-of-concept for
Android and iOS (haven't checked it for a while), most probably Desktop
will work as well.

This is a screenshot of a browser, an Android simulator and an iOS simulator
running the exact same code next to each other.

![demo](https://raw.githubusercontent.com/spxbhuhb/adaptive-site-resources/refs/heads/main/images/good_morning.webp)

The project is structured so that adding other platforms and/or some useful UI 
targets such as image, PDF or Docx is rather easy.

---