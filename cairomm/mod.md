 * Copy directory MSVC_Net2013 to MSVC_2015
 * Load cairomm.sln in Visual Studio 2015 to convert the projects to the new tool set

 * In `MSVC_2015\cairomm-version-paths.props`, replace:
	* `<VSVer>12</VSVer>` with `<VSVer>14</VSVer>`
	* `<GlibEtcInstallRoot>$(SolutionDir)\..\..\vs$(VSVer)\$(Platform)</GlibEtcInstallRoot>` with `<GlibEtcInstallRoot>$(SolutionDir)\..\..\..\..\..\gtk\$(Platform)\$(Configuration)</GlibEtcInstallRoot>`
	* `<CopyDir>$(GlibEtcInstallRoot)</CopyDir>` with `<CopyDir>..\..\cairomm-rel</CopyDir>`
	* `<ReleaseDllSuffix>-vc$(VSVer)0-$(ApiMajorVersion)_$(ApiMinorVersion)</ReleaseDllSuffix>` with `<ReleaseDllSuffix>-$(ApiMajorVersion).$(ApiMinorVersion)</ReleaseDllSuffix>`
	* `<DebugDllSuffix>-vc$(VSVer)0-d-$(ApiMajorVersion)_$(ApiMinorVersion)</DebugDllSuffix>` with `<DebugDllSuffix>-$(ApiMajorVersion).$(ApiMinorVersion)</DebugDllSuffix>`

 * In `MSVC_2015\cairomm-build-defines.props`, replace:
	* `<CPPDepLibsRelease>sigc-vc$(VSVer)0-2_0.lib</CPPDepLibsRelease>` with `<CPPDepLibsRelease>sigc-2.0.lib</CPPDepLibsRelease>`
	* `<CPPDepLibsDebug>sigc-vc$(VSVer)0-d-2_0.lib</CPPDepLibsDebug>` with `<CPPDepLibsDebug>sigc-2.0.lib</CPPDepLibsDebug>`
	* `<ForcedIncludeFiles>msvc_recommended_pragmas.h;%(ForcedIncludeFiles)</ForcedIncludeFiles>` with `<ForcedIncludeFiles>%(ForcedIncludeFiles)</ForcedIncludeFiles>`
	* `<AdditionalIncludeDirectories>.\cairomm;..;$(GlibEtcInstallRoot)\include\sigc++-2.0;$(GlibEtcInstallRoot)\lib\sigc++-2.0\include;$(GlibEtcInstallRoot)\include;%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>` with `<AdditionalIncludeDirectories>.\cairomm;..;$(GlibEtcInstallRoot)\include\sigc++-2.0;$(GlibEtcInstallRoot)\lib\sigc++-2.0\include;$(GlibEtcInstallRoot)\include;$(GlibEtcInstallRoot)\include\cairo;%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>`
