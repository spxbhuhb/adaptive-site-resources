# Adaptive

Adaptive is a Kotlin Multiplatform software suite containing:

* KMP libraries for full-stack, reactive software development
* development tools to build applications with those libraries
* complete applications built with those tools

It is somewhat of a personal project for now. I actually like to write
documentation, examples and such, but they are not well organized yet.

You can get a glimpse of the actual features Adaptive offers if you open
the cookbook from the left icon bar (the dining icon).

> 
> Adaptive is **work in progress**, this site usually lags a bit behind
> the current state. 
> 
> While the technology seems to be solid, and it is actually possible to
> build working applications with Adaptive, it would take considerable
> effort to keep up with the changes.
> 
> If you love Kotlin and you want to experiment a bit around, you are
> welcome to do so, but please keep in mind that this project is nowhere
> close to mature and changes constantly.
> 

You can check the [GitHub repo](https://github.com/spxbhuhb/adaptive) (especially the
`doc` directory) for more details.

## Main features

The links do not work yet.

### Core

- [dependency minimum](#dependency-minimum)
- [complete application framework](#complete-application-framework)
- [reactive, truly multiplatform UI](#reactive-truly-multiplatform-ui)
- [multiplatform resources](#multiplatform-resources)
- client-server communication with simple function calls (RPC)
- independent serialization (Json and Protobuf)
- enhanced data classes

Projects:

- `core` - core definitions and classes
- `gradle-plugin` - Gradle plugin for Adaptive
- `kotlin-plugin` - Kotlin compiler plugin for Adaptive
- `ui` - low level UI primitives, layouts, platform-dependent features

### Libraries

Projects:

- `lib-app` - application level components (see [complete application frameworks](#complete-application-framework))
- `lib-auth` - authentication and authorization (principals, users, passwords, roles)
- `lib-document` - document rendering, markdown processing
- `lib-chart` - charting
- `lib-email` - email sending
- `lib-graphics` - low level graphics: Canvas and SVG
- `lib-ktor` - Ktor integration
- `lib-ui` - UI components, some quite sophisticated
- `lib-value` - Value store concept, pluggable persistence, publish/subscribe pattern

### Grove

Grove is an application which contains software development tools for Adaptive.

It is in a preliminary phase, but it already features a UI fragment designer which
could be used to build UI fragments with a graphical editor.

### IoT

Aio (Adaptive IoT) is an application for IoT. It is a fully working application with
tools to define areas, devices, charting, histories etc.

It is under active development.

## Dependency minimum

Applications built with Adaptive typically have these dependencies:

- `kotlinx.coroutines`
- `kotlinx.datetime`
- `kotlinx.io`

If you build a web server based application you can add Ktor, but that
is actually optional, you can build a fully working application without it.

Some server side modules might have a few other dependencies, email sending
for example depends on Java mail, but there are very few of those.

If you check `libs.versions.toml` you'll see other dependencies, such as
the Kotlin compiler, testing utilities, Android stuff. These are OS level
and/or testing libraries which cannot be avoided with reasonable effort.

Dependency minimum is **hard** to maintain, but my intention is to do so.
I've spent considerable effort to reach this and I think it will pay
dividends on the long run, when I add AI support to Adaptive.

## Complete application framework

The `lib-app` library provides a framework to for full-stack applications.

You can build server and client side applications with some of the usual
components (such as user and role management, authentication and authorization)
provided out-of-the-box.

## Reactive, truly multiplatform UI

Adaptive features its very own, reactive, multiplatform UI implementation, inspired
by Svelte. It does not depend on Compose, React or whatever.

It is truly multiplatform as it does not have different versions such as Compose for
Desktop, Compose for Web, etc.

Adaptive offers a unified UI programming interface on **all** the platforms. My approach
is that while screen size and capabilities (such as touch) matter, the actual platform
should not.

The best example for this is mobile and web. When the user looks at the application in
a web browser running on mobile, I want to use the **very same** UI component.

> 
> While all the above is true, I haven't finished all the platform dependent components
> for mobile and I actually haven't added desktop yet.
> 
> That said, there **are** a few components implemented for both iOS and Android and I've
> successfully ran the Good Morning demo (check the cookbook) on all platforms.
> 

### Deterministic layouts

Adaptive provides UI layouts which are all calculated by the library itself. No platform
dependent layout calculations are used (not even on Web).

As a result, if you see something on the web written with Adaptive you can be sure that it
looks the same on all platforms. Therefore, you can build all of your application on the
web and then just compile it for mobile.

What's more, it would be quite possible to use these for image, PDF or HTML export.

### Multiplatform resources

Inspired by (and to be honest, initially copied from) Compose Resources, Adaptive has its
own resource management. The Gradle plugin collects, compiles and packs the resources
of your application, so you can use them very easily.

This topic needs some work, especially string management and localization which I feel is lacking.