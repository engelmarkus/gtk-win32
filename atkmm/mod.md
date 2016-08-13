 * Copy directory MSVC_Net2013 to MSVC_2015
 * Load atkmm.sln in Visual Studio 2015 to convert the projects to the new tool set

 * In `MSVC_2015\atkmm-version-paths.props`, replace:
	* `<VSVer>12</VSVer>` with `<VSVer>14</VSVer>`
	* `<GlibEtcInstallRoot>$(SolutionDir)\..\..\vs$(VSVer)\$(Platform)</GlibEtcInstallRoot>` with `<GlibEtcInstallRoot>$(SolutionDir)\..\..\..\..\..\gtk\$(Platform)\$(Configuration)</GlibEtcInstallRoot>`
	* `<CopyDir>$(GlibEtcInstallRoot)</CopyDir>` with `<CopyDir>..\..\atkmm-rel</CopyDir>`
	* `<ReleaseDllSuffix>-vc$(VSVer)0-$(ApiMajorVersion)_$(ApiMinorVersion)</ReleaseDllSuffix>` with `<ReleaseDllSuffix>-$(ApiMajorVersion).$(ApiMinorVersion)</ReleaseDllSuffix>`
	* `<DebugDllSuffix>-vc$(VSVer)0-d-$(ApiMajorVersion)_$(ApiMinorVersion)</DebugDllSuffix>` with `<DebugDllSuffix>-$(ApiMajorVersion).$(ApiMinorVersion)</DebugDllSuffix>`

 * In `MSVC_2015\atkmm-build-defines.props`, replace:
	* `<CPPDepLibsRelease>glibmm-vc$(VSVer)0-2_4.lib;sigc-vc$(VSVer)0-2_0.lib</CPPDepLibsRelease>` with `<CPPDepLibsRelease>glibmm-2.4.lib;sigc-2.0.lib</CPPDepLibsRelease>`
	* `<CPPDepLibsDebug>glibmm-vc$(VSVer)0-d-2_4.lib;sigc-vc$(VSVer)0-d-2_0.lib</CPPDepLibsDebug>` with `<CPPDepLibsDebug>glibmm-2.4.lib;sigc-2.0.lib</CPPDepLibsDebug>`
	* `<ForcedIncludeFiles>msvc_recommended_pragmas.h;%(ForcedIncludeFiles)</ForcedIncludeFiles>` with `<ForcedIncludeFiles>%(ForcedIncludeFiles)</ForcedIncludeFiles>`

 * In `MSVC_2015\atkmm-install.props`, replace:
	* `copy $(BinDir)\atkmm-vc$(VSVer)0-$(ApiMajorVersion)_$(ApiMinorVersion).dll $(CopyDir)\bin` with `copy $(BinDir)\atkmm-$(ApiMajorVersion).$(ApiMinorVersion).dll $(CopyDir)\bin`
	* `copy $(BinDir)\atkmm-vc$(VSVer)0-$(ApiMajorVersion)_$(ApiMinorVersion).lib $(CopyDir)\lib` with `copy $(BinDir)\atkmm-$(ApiMajorVersion).$(ApiMinorVersion).lib $(CopyDir)\lib`

 * In `MSVC_2015\atkmm-install.props`, add:
`
copy $(BinDir)\atkmm-$(ApiMajorVersion).$(ApiMinorVersion).pdb $(CopyDir)\bin
`