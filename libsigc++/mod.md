 * Copy directory MSVC_Net2013 to MSVC_2015
 * Load libsigc++2.sln in Visual Studio 2015 to convert the projects to the new tool set

 * In `MSVC_2015\sigc-version-paths.props`, replace:
	* `<VSVer>12</VSVer>` with `<VSVer>14</VSVer>`
	* `<GlibEtcInstallRoot>$(SolutionDir)\..\..\vs$(VSVer)\$(Platform)</GlibEtcInstallRoot>` with `<GlibEtcInstallRoot>$(SolutionDir)\..\..\..\..\..\gtk\$(Platform)</GlibEtcInstallRoot>`
	* `<CopyDir>$(GlibEtcInstallRoot)</CopyDir>` with `<CopyDir>..\..\libsigc++-rel</CopyDir>`
	* `<ReleaseDllSuffix>-vc$(VSVer)0-$(ApiMajorVersion)_$(ApiMinorVersion)</ReleaseDllSuffix>` with `<ReleaseDllSuffix>-$(ApiMajorVersion).$(ApiMinorVersion)</ReleaseDllSuffix>`
	* `<DebugDllSuffix>-vc$(VSVer)0-d-$(ApiMajorVersion)_$(ApiMinorVersion)</DebugDllSuffix>` with `<DebugDllSuffix>-$(ApiMajorVersion).$(ApiMinorVersion)</DebugDllSuffix>`

 * In `MSVC_2015\sigc-build-defines.props`, replace:
	* `<ForcedIncludeFiles>msvc_recommended_pragmas.h;%(ForcedIncludeFiles)</ForcedIncludeFiles>` with `<ForcedIncludeFiles>%(ForcedIncludeFiles)</ForcedIncludeFiles>`
