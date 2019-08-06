# try.peachpie.io

This repository integrates our forks of MirrorSharp and SharpLab in order to produce the contents of [try.peachpie.io](https://try.peachpie.io).
After every commit into this repository, CI performs the following tasks:

1. Clones this repository including the recursive submodules.
2. Compiles all the projects in the ```mirrorsharp``` submodule and publishes the resulting NuGet packages into the ```.nugs``` folder. Notice that the Peachpie version, the package version suffix and the package output path are stored in ```Directory.Build.props```.
3. Compiles the ```WebApp``` project (with its dependencies) in the ```sharplab``` submodule. The recent MirrorSharp NuGets are used thanks to ```NuGet.config```.
4. Uses ```dotnet publish``` to create the resulting website.
4. Publishes the website to the staging slot of try.peachpie.io (the swap must be performed manually).
