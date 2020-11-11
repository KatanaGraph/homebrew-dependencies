# homebrew-katana-dependencies

`brew tap KatanaGraph/dependencies`

If you encounter an issue with a new verison of a `brew` package that won't be resolved immediately, determine the offending package from the build failure and do the following:

Use `brew info <offending>` to find the github link to the .rb file that defines the version

Go to that link and use the `history` to find the most recent non-offending version of the file

Create a copy of the desired file in the `Formla` directory

In the main repo, modify `.github/workflows/setup_macos.sh` to reference `KatanaGraph/dependencies/<offending>` instead of `<offending>`

The runner machines will be out of sync at this point. Run `brew remove <offending>` on each of them to clear out the old package, then run `setup_macos.sh`. It may take a few passes at this, as some dependencies of the offending package may have also been updated.
