 * Copy directory MSVC_Net2013 to MSVC_2015
 * Load glibmm.sln in Visual Studio 2015 to convert the projects to the new tool set

 * In `MSVC_2015\glibmm-version-paths.props`, replace:
	* `<VSVer>12</VSVer>` with `<VSVer>14</VSVer>`
	* `<GlibEtcInstallRoot>$(SolutionDir)\..\..\vs$(VSVer)\$(Platform)</GlibEtcInstallRoot>` with `<GlibEtcInstallRoot>$(SolutionDir)\..\..\..\..\..\gtk\$(Platform)\$(Configuration)</GlibEtcInstallRoot>`
	* `<CopyDir>$(GlibEtcInstallRoot)</CopyDir>` with `<CopyDir>..\..\glibmm-rel</CopyDir>`
	* `<ReleaseDllSuffix>-vc$(VSVer)0-$(ApiMajorVersion)_$(ApiMinorVersion)</ReleaseDllSuffix>` with `<ReleaseDllSuffix>-$(ApiMajorVersion).$(ApiMinorVersion)</ReleaseDllSuffix>`
	* `<DebugDllSuffix>-vc$(VSVer)0-d-$(ApiMajorVersion)_$(ApiMinorVersion)</DebugDllSuffix>` with `<DebugDllSuffix>-$(ApiMajorVersion).$(ApiMinorVersion)</DebugDllSuffix>`

 * In `MSVC_2015\glibmm-build-defines.props`, replace:
	* `<CPPDepLibsRelease>sigc-vc$(VSVer)0-2_0.lib</CPPDepLibsRelease>` with `<CPPDepLibsRelease>sigc-2.0.lib</CPPDepLibsRelease>`
	* `<CPPDepLibsDebug>sigc-vc$(VSVer)0-d-2_0.lib</CPPDepLibsDebug>` with `<CPPDepLibsDebug>sigc-2.0.lib</CPPDepLibsDebug>`
	* `<ForcedIncludeFiles>msvc_recommended_pragmas.h;%(ForcedIncludeFiles)</ForcedIncludeFiles>` with `<ForcedIncludeFiles>%(ForcedIncludeFiles)</ForcedIncludeFiles>`
	* `<AdditionalIncludeDirectories>.\glibmm;..;..\glib;$(GlibEtcInstallRoot)\include\sigc++-2.0;$(GlibEtcInstallRoot)\lib\sigc++-2.0\include;$(GlibEtcInstallRoot)\include\gio-win32-2.0;$(GlibEtcInstallRoot)\include\glib-2.0;$(GlibEtcInstallRoot)\lib\glib-2.0\include;$(GlibEtcInstallRoot)\include;%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>` with `<AdditionalIncludeDirectories>.\glibmm;.\giomm;..;..\glib;..\gio;$(GlibEtcInstallRoot)\include\sigc++-2.0;$(GlibEtcInstallRoot)\lib\sigc++-2.0\include;$(GlibEtcInstallRoot)\include\gio-win32-2.0;$(GlibEtcInstallRoot)\include\glib-2.0;$(GlibEtcInstallRoot)\lib\glib-2.0\include;$(GlibEtcInstallRoot)\include;%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>`

 * In `MSVC_2015\glibmm-install.props`, replace:
	* `copy $(BinDir)\glibmm-vc$(VSVer)0-$(ApiMajorVersion)_$(ApiMinorVersion).dll $(CopyDir)\bin` with `copy $(BinDir)\glibmm-$(ApiMajorVersion).$(ApiMinorVersion).dll $(CopyDir)\bin`
	* `copy $(BinDir)\giomm-vc$(VSVer)0-$(ApiMajorVersion)_$(ApiMinorVersion).dll $(CopyDir)\bin` with `copy $(BinDir)\giomm-$(ApiMajorVersion).$(ApiMinorVersion).dll $(CopyDir)\bin`
	* `copy $(BinDir)\glibmm-vc$(VSVer)0-$(ApiMajorVersion)_$(ApiMinorVersion).lib $(CopyDir)\lib` with `copy $(BinDir)\glibmm-$(ApiMajorVersion).$(ApiMinorVersion).lib $(CopyDir)\lib`
	* `copy $(BinDir)\giomm-vc$(VSVer)0-$(ApiMajorVersion)_$(ApiMinorVersion).lib $(CopyDir)\lib` with `copy $(BinDir)\giomm-$(ApiMajorVersion).$(ApiMinorVersion).lib $(CopyDir)\lib`

 * In `MSVC_2015\glibmm-install.props`, add:
`
copy $(BinDir)\glibmm.pdb $(CopyDir)\bin\glibmm-$(ApiMajorVersion).$(ApiMinorVersion).pdb
copy $(BinDir)\giomm.pdb $(CopyDir)\bin\giomm-$(ApiMajorVersion).$(ApiMinorVersion).pdb
`