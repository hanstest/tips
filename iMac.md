Install readline
================

```bash
brew install readline
```

This is because of how Homebrew installs Readline. Since OS X ships libedit as libreadline, 
Homebrew tries to avoid conflicts with system software by installing Readline as “keg-only” 
software – that is, it’ll install it within its package-managed filesystem hierarchy beneath 
/usr/local/Cellar, but it won’t link the libraries into /usr/local/lib, so that they won’t 
be visible to software that isn’t explicitly linked against it.

There is an easy and obvious way around this:

```bash
brew link --overwrite --force readline
```

This makes Homebrew link the shared libraries into /usr/local/lib – which Homebrew ordinarily 
refuses to do for packages marked keg-only, like Readline is, hence the scary --force.
