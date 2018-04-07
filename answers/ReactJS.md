#### Explain the upsides and tradeoffs of using the DllPlugin as opposed to CommonChunksPlugin.

##CommonsChunkPlugin rationale
Project author defines a number of application entry points that will produce a bundle each. Typical examples are vendor, polyfills, main, but for example your app could be split in several independent "areas" that makes sense to load separately (like e.g. login, main, settings).

Project author then defines which one of those bundles, or a separate one, should contain code common to all of them. That is tipically 3rd party libraries and your own shared utilities across all entry points.

Then it is plugin responsibility to analyze and collect such common code, then put it in defined bundle. All such analysis and work happens again and again everytime you start a new build, and - in watch mode - when you modify code that is shared and happens to fall into commons bundle.

Such a split is useful both for a development build as well as for a production build. But for dev environment, let's just say that re-building code related to vendors and polyfills might take quite some time and it can be a waste when you're not really changing those parts (assuming 3rd party code you depend on is larger than your own codebase).

##DllPlugin rationale
Given the same environment, for example development, project author creates two webpack configurations where there used to be one. The plugin could be applied to production environment, although it can be said that DllPlugin makes more sense in development (see below).

First webpack build configuration is needed for so-called DLLs, which are kind of close to the commons code seen before, but not exactly. To my understanding, DLLs mostly tend to group 3rd party code (vendor and polyfills) and not your own shared utility code, but again this is more an impression and not a strict rule. Anyway, here project author should group code that changes much less frequently during a normal development session. The idea, in dev environment, is to run this build every once in a while, for example when a dependency changes. And usually it is up to the developer to fire this build when s/he think is needed.

The other webpack build configuration is needed for project own code, or anyway code that changes regularly while doing dev work. This is the actual build that developer will run again and again, or will run in watch mode, and at this point it should be very much quicker as compared to the single build seen in CommonsChunk scenario.
