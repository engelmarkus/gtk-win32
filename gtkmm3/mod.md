 * Copy directory MSVC_Net2013 to MSVC_2015
 * Load gtkmm.sln in Visual Studio 2015 to convert the projects to the new tool set

 * In `MSVC_2015\gtkmm-version-paths.props`, replace:
	* `<VSVer>12</VSVer>` with `<VSVer>14</VSVer>`
	* `<GlibEtcInstallRoot>$(SolutionDir)\..\..\vs$(VSVer)\$(Platform)</GlibEtcInstallRoot>` with `<GlibEtcInstallRoot>$(SolutionDir)\..\..\..\..\..\gtk\$(Platform)\$(Configuration)</GlibEtcInstallRoot>`
	* `<CopyDir>$(GlibEtcInstallRoot)</CopyDir>` with `<CopyDir>..\..\gtkmm3-rel</CopyDir>`
	* `<ReleaseDllSuffix>-vc$(VSVer)0-$(ApiMajorVersion)_$(ApiMinorVersion)</ReleaseDllSuffix>` with `<ReleaseDllSuffix>-$(ApiMajorVersion).$(ApiMinorVersion)</ReleaseDllSuffix>`
	* `<DebugDllSuffix>-vc$(VSVer)0-d-$(ApiMajorVersion)_$(ApiMinorVersion)</DebugDllSuffix>` with `<DebugDllSuffix>-$(ApiMajorVersion).$(ApiMinorVersion)</DebugDllSuffix>`

 * In `MSVC_2015\gtkmm-build-defines.props`, replace:
	* `<CPPDepLibsRelease>pangomm-vc$(VSVer)0-1_4.lib;giomm-vc$(VSVer)0-2_4.lib;glibmm-vc$(VSVer)0-2_4.lib;cairomm-vc$(VSVer)0-1_0.lib;sigc-vc$(VSVer)0-2_0.lib</CPPDepLibsRelease>` with `<CPPDepLibsRelease>pangomm-1.4.lib;giomm-2.4.lib;glibmm-2.4.lib;cairomm-1.0.lib;sigc-2.0.lib</CPPDepLibsRelease>`
	* `<CPPDepLibsDebug>pangomm-vc$(VSVer)0-d-1_4.lib;giomm-vc$(VSVer)0-d-2_4.lib;glibmm-vc$(VSVer)0-d-2_4.lib;cairomm-vc$(VSVer)0-d-1_0.lib;sigc-vc$(VSVer)0-d-2_0.lib</CPPDepLibsDebug>` with `<CPPDepLibsDebug>pangomm-1.4.lib;giomm-2.4.lib;glibmm-2.4.lib;cairomm-1.0.lib;sigc-2.0.lib</CPPDepLibsDebug>`
	* `<ForcedIncludeFiles>msvc_recommended_pragmas.h;%(ForcedIncludeFiles)</ForcedIncludeFiles>` with `<ForcedIncludeFiles>%(ForcedIncludeFiles)</ForcedIncludeFiles>`
	* `<AdditionalIncludeDirectories>.\gdkmm;..;..\gdk;$(GlibEtcInstallRoot)\include\pangomm-1.4;$(GlibEtcInstallRoot)\lib\pangomm-1.4\include;$(GlibEtcInstallRoot)\include\giomm-2.4;$(GlibEtcInstallRoot)\lib\giomm-2.4\include;$(GlibEtcInstallRoot)\include\glibmm-2.4;$(GlibEtcInstallRoot)\lib\glibmm-2.4\include;$(GlibEtcInstallRoot)\include\cairomm-1.0;$(GlibEtcInstallRoot)\lib\cairomm-1.0\include;$(GlibEtcInstallRoot)\include\sigc++-2.0;$(GlibEtcInstallRoot)\lib\sigc++-2.0\include;$(GlibEtcInstallRoot)\include\gtk-3.0;$(GlibEtcInstallRoot)\include\gdk-pixbuf-2.0;$(GlibEtcInstallRoot)\include\pango-1.0;$(GlibEtcInstallRoot)\include\gio-win32-2.0;$(GlibEtcInstallRoot)\include\glib-2.0;$(GlibEtcInstallRoot)\lib\glib-2.0\include;$(GlibEtcInstallRoot)\include;%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>` with `<AdditionalIncludeDirectories>.\gdkmm;..;..\gdk;$(GlibEtcInstallRoot)\include\pangomm-1.4;$(GlibEtcInstallRoot)\lib\pangomm-1.4\include;$(GlibEtcInstallRoot)\include\giomm-2.4;$(GlibEtcInstallRoot)\lib\giomm-2.4\include;$(GlibEtcInstallRoot)\include\glibmm-2.4;$(GlibEtcInstallRoot)\lib\glibmm-2.4\include;$(GlibEtcInstallRoot)\include\cairomm-1.0;$(GlibEtcInstallRoot)\lib\cairomm-1.0\include;$(GlibEtcInstallRoot)\include\sigc++-2.0;$(GlibEtcInstallRoot)\lib\sigc++-2.0\include;$(GlibEtcInstallRoot)\include\gtk-3.0;$(GlibEtcInstallRoot)\include\gdk-pixbuf-2.0;$(GlibEtcInstallRoot)\include\pango-1.0;$(GlibEtcInstallRoot)\include\gio-win32-2.0;$(GlibEtcInstallRoot)\include\glib-2.0;$(GlibEtcInstallRoot)\lib\glib-2.0\include;$(GlibEtcInstallRoot)\include;$(GlibEtcInstallRoot)\include\cairo;$(GlibEtcInstallRoot)\include\atk-1.0;%(AdditionalIncludeDirectories)</AdditionalIncludeDirectories>`

 * In `MSVC_2015\gtkmm-install.props`, replace:
	* `copy $(SolutionDir)$(Configuration)\$(Platform)\bin\*-vc$(VSVer)0-*$(ApiMajorVersion)_$(ApiMinorVersion).dll $(CopyDir)\bin` with `copy $(SolutionDir)$(Configuration)\$(Platform)\bin\*-$(ApiMajorVersion).$(ApiMinorVersion).dll $(CopyDir)\bin`
	* `copy $(SolutionDir)$(Configuration)\$(Platform)\bin\gdkmm-vc$(VSVer)0-*$(ApiMajorVersion)_$(ApiMinorVersion).lib $(CopyDir)\lib` with `copy $(SolutionDir)$(Configuration)\$(Platform)\bin\gdkmm-$(ApiMajorVersion).$(ApiMinorVersion).lib $(CopyDir)\lib`
	* `copy $(SolutionDir)$(Configuration)\$(Platform)\bin\gtkmm-vc$(VSVer)0-*$(ApiMajorVersion)_$(ApiMinorVersion).lib $(CopyDir)\lib` with `copy $(SolutionDir)$(Configuration)\$(Platform)\bin\gtkmm-$(ApiMajorVersion).$(ApiMinorVersion).lib $(CopyDir)\lib`

 * In `MSVC_2015\gtkmm-install.props`, add:
`
copy $(SolutionDir)$(Configuration)\$(Platform)\bin\*-$(ApiMajorVersion).$(ApiMinorVersion).pdb $(CopyDir)\bin
`

 * In `MSVC_2015\gtkmm.vcxproj`, replace:
	* twice `<AdditionalDependencies>atkmm-vc$(VSVer)0-d-1_6.lib;$(CPPDepLibsDebug);%(AdditionalDependencies)</AdditionalDependencies>` with `<AdditionalDependencies>atkmm-1.6.lib;$(CPPDepLibsDebug);%(AdditionalDependencies)</AdditionalDependencies>`
	* twice `<AdditionalDependencies>atkmm-vc$(VSVer)0-1_6.lib;$(CPPDepLibsRelease);%(AdditionalDependencies)</AdditionalDependencies>` with `<AdditionalDependencies>atkmm-1.6.lib;$(CPPDepLibsRelease);%(AdditionalDependencies)</AdditionalDependencies>`

 * In `MSVC_2015\gtkmm3-demo.vcxproj`, replace:
	* twice `<AdditionalDependencies>atkmm-vc$(VSVer)0-d-1_6.lib;$(CPPDepLibsDebug);%(AdditionalDependencies)</AdditionalDependencies>` with `<AdditionalDependencies>atkmm-1.6.lib;$(CPPDepLibsDebug);%(AdditionalDependencies)</AdditionalDependencies>`
	* twice `<AdditionalDependencies>atkmm-vc$(VSVer)0-1_6.lib;$(CPPDepLibsRelease);%(AdditionalDependencies)</AdditionalDependencies>` with `<AdditionalDependencies>atkmm-1.6.lib;$(CPPDepLibsRelease);%(AdditionalDependencies)</AdditionalDependencies>`


* Info on the patch for gendef.cc:
In the Windows 10 SDK, all the printf-like functions are inline functions declared and defined in stdio.h.
However, if the compiler decides not to inline them because of the "/Od" switch (i. e. when compiling in debug mode),
gendef will list these printf functions as exports in the exports file that is used to generate the dll (this makes it impossible to simply link against "legacy_stdio_definitions.lib", which would fix the issue otherwise).
This will lead to undefined references, so the patch makes sure that these functions are omitted from the file.
See https://msdn.microsoft.com/en-us/library/bb531344.aspx and C:\Program Files (x86)\Windows Kits\10\Include\10.0.10240.0\ucrt\stdio.h.