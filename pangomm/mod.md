 * Copy directory MSVC_Net2013 to MSVC_2015
 * Load pangomm.sln in Visual Studio 2015 to convert the projects to the new tool set

 * In `MSVC_2015\pangomm-version-paths.props`, replace:
	* `<VSVer>12</VSVer>` with `<VSVer>14</VSVer>`
	* `<GlibEtcInstallRoot>$(SolutionDir)\..\..\vs$(VSVer)\$(Platform)</GlibEtcInstallRoot>` with `<GlibEtcInstallRoot>$(SolutionDir)\..\..\..\..\..\gtk\$(Platform)\$(Configuration)</GlibEtcInstallRoot>`
	* `<CopyDir>$(GlibEtcInstallRoot)</CopyDir>` with `<CopyDir>..\..\pangomm-rel</CopyDir>`
	* `<ReleaseDllSuffix>-vc$(VSVer)0-$(ApiMajorVersion)_$(ApiMinorVersion)</ReleaseDllSuffix>` with `<ReleaseDllSuffix>-$(ApiMajorVersion).$(ApiMinorVersion)</ReleaseDllSuffix>`
	* `<DebugDllSuffix>-vc$(VSVer)0-d-$(ApiMajorVersion)_$(ApiMinorVersion)</DebugDllSuffix>` with `<DebugDllSuffix>-$(ApiMajorVersion).$(ApiMinorVersion)</DebugDllSuffix>`

 * In `MSVC_2015\pangomm-build-defines.props`, replace:
	* `<CPPDepLibsRelease>glibmm-vc$(VSVer)0-2_4.lib;cairomm-vc$(VSVer)0-1_0.lib;sigc-vc$(VSVer)0-2_0.lib</CPPDepLibsRelease>` with `<CPPDepLibsRelease>glibmm-2.4.lib;cairomm-1.0.lib;sigc-2.0.lib</CPPDepLibsRelease>`
	* `<CPPDepLibsDebug>glibmm-vc$(VSVer)0-d-2_4.lib;cairomm-vc$(VSVer)0-d-1_0.lib;sigc-vc$(VSVer)0-d-2_0.lib</CPPDepLibsDebug>` with `<CPPDepLibsDebug>glibmm-2.4.lib;cairomm-1.0.lib;sigc-2.0.lib</CPPDepLibsDebug>`
	* `<ForcedIncludeFiles>msvc_recommended_pragmas.h;%(ForcedIncludeFiles)</ForcedIncludeFiles>` with `<ForcedIncludeFiles>%(ForcedIncludeFiles)</ForcedIncludeFiles>`
	* `<AdditionalIncludeDirectories>.\pangomm;..\pango;$(GlibEtcInstallRoot)\include\glibmm-2.4;$(GlibEtcInstallRoot)\lib\glibmm-2.4\include;$(GlibEtcInstallRoot)\include\cairomm-1.0;$(GlibEtcInstallRoot)\lib\cairomm-1.0\include;$(GlibEtcInstallRoot)\include\sigc++-2.0;$(GlibEtcInstallRoot)\lib\sigc++-2.0\include;$(GlibEtcInstallRoot)\include\pango-1.0;$(GlibEtcInstallRoot)\include\glib-2.0;$(GlibEtcInstallRoot)\lib\glib-2.0\include;$(GlibEtcInstallRoot)\include;%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>` with `<AdditionalIncludeDirectories>.\pangomm;..\pango;$(GlibEtcInstallRoot)\include\glibmm-2.4;$(GlibEtcInstallRoot)\lib\glibmm-2.4\include;$(GlibEtcInstallRoot)\include\cairomm-1.0;$(GlibEtcInstallRoot)\lib\cairomm-1.0\include;$(GlibEtcInstallRoot)\include\sigc++-2.0;$(GlibEtcInstallRoot)\lib\sigc++-2.0\include;$(GlibEtcInstallRoot)\include\pango-1.0;$(GlibEtcInstallRoot)\include\glib-2.0;$(GlibEtcInstallRoot)\lib\glib-2.0\include;$(GlibEtcInstallRoot)\include;$(GlibEtcInstallRoot)\include\cairo;%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>`

 * In `MSVC_2015\pangomm-install.props`, replace:
	* `copy $(BinDir)\pangomm-vc$(VSVer)0-$(ApiMajorVersion)_$(ApiMinorVersion).dll $(CopyDir)\bin` with `copy $(BinDir)\pangomm-$(ApiMajorVersion).$(ApiMinorVersion).dll $(CopyDir)\bin`
	* `copy $(BinDir)\pangomm-vc$(VSVer)0-$(ApiMajorVersion)_$(ApiMinorVersion).lib $(CopyDir)\lib` with `copy $(BinDir)\pangomm-$(ApiMajorVersion).$(ApiMinorVersion).lib $(CopyDir)\lib`

 * In `MSVC_2015\glibmm-install.props`, add:
`
copy $(BinDir)\pangomm-$(ApiMajorVersion).$(ApiMinorVersion).pdb $(CopyDir)\bin
`