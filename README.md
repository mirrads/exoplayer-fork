Cloning the repository and depending on the modules locally is required when
using some ExoPlayer extension modules. It's also a suitable approach if you
want to make local changes to ExoPlayer, or if you want to use a development
branch.

First, clone the repository into a local directory and checkout the desired
branch:

```sh
git clone https://github.com/sneltyn/exoplayer-fork.git
git checkout master
```

Next, add the following to your project's `settings.gradle` file, replacing
`path/to/exoplayer-fork` with the path to your local copy:

```gradle
gradle.ext.exoplayerRoot = 'path/to/exoplayer-fork'
gradle.ext.exoplayerModulePrefix = 'exoplayer-'
apply from: new File(gradle.ext.exoplayerRoot, 'core_settings.gradle')
```

You should now see the ExoPlayer modules appear as part of your project. You can
depend on them as you would on any other local module, for example (This is already added in the **Mirrads** app):

```gradle
implementation project(':exoplayer-library-core')
implementation project(':exoplayer-library-dash')
implementation project(':exoplayer-library-ui')
```

