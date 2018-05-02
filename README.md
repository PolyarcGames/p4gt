                      Perforce Graphic Tools Plug-in Open Source Project [P4GT]


# GETTING STARTED

Components required are:
* P4 API from Perforce FTP site
* P4GT from Perforce Workshop
* proprietary SDKs for any of products:
  + 3ds max 2014*
  + Maya 2014*
  + Softimage 2014*
  + Photoshop CC**
* update Version file

* x64 support only

** a patch must first be applied in order to build plug-in for Photoshop CC
	[see file ..\p4gt\photoshop_cc\PIUFile.cpp.patch for instructions]


----

# INSTALLING CODE

Steps:

IMPORTANT: refer to directory layout below for where to install the P4 API, P4GT, and graphic tool SDKs.

1. sync P4GT from the Perforce Workshop:
	http://workshop.perforce.com/

2. dowload the appropriate P4 API from Perforce FTP site:
	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx86/p4api_vs2005_dyn.zip           {for Visual Studio 2005 Release builds 32-bit}
	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx86/p4api_vs2005_dyn_vsdebug.zip   {for Visual Studio 2005 Debug builds 32-bit}
	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx86/p4api_vs2005_dyn.zip           {for Visual Studio 2005 Release builds 64-bit}
	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx64/p4api_vs2005_dyn_vsdebug.zip   {for Visual Studio 2005 Debug builds 64-bit}

	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx86/p4api_vs2008_dyn.zip           {for Visual Studio 2008 Release builds 32-bit}
	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx86/p4api_vs2008_dyn_vsdebug.zip   {for Visual Studio 2008 Debug builds 32-bit}
	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx64/p4api_vs2008_dyn.zip           {for Visual Studio 2008 Release builds 64-bit}
	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx64/p4api_vs2008_dyn_vsdebug.zip   {for Visual Studio 2008 Debug builds 64-bit}

	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx86/p4api_vs2010_dyn.zip           {for Visual Studio 2010 Release builds 32-bit}
	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx86/p4api_vs2010_dyn_vsdebug.zip   {for Visual Studio 2010 Debug builds 32-bit}
	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx64/p4api_vs2010_dyn.zip           {for Visual Studio 2010 Release builds 64-bit}
	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx64/p4api_vs2010_dyn_vsdebug.zip   {for Visual Studio 2010 Debug builds 64-bit}

	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx86/p4api_vs2012_dyn.zip           {for Visual Studio 2012 Release builds 32-bit}
	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx86/p4api_vs2012_dyn_vsdebug.zip   {for Visual Studio 2012 Debug builds 32-bit}	
	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx64/p4api_vs2012_dyn.zip           {for Visual Studio 2012 Release builds 64-bit}
	* ftp://ftp.perforce.com/perforce/r14.1/bin.ntx64/p4api_vs2012_dyn_vsdebug.zip   {for Visual Studio 2012 Debug builds 64-bit}	


3. install desired SDK(s):
	* 3ds max 2014 / Maya 2014 / Softimage 2014 available from Autodesk 
    + Photoshop CC available from Adobe


----

# BUILDING P4GT PLUG-IN(S)

1. update build version info in file ..\p4-gt\Version

 In theory from this point, simply run these scripts to build and install the plug-ins:      
 .\p4-gt\build_release_os.bat {builds the available plug-ins}                                
 .\p4-gt\p4gt_install_os.bat  {installs the built plug-ins, help file in the graphic tools}  
                                                                                             
 For more details on building read on.                                                       

2. build plug-in(s) for desired graphic tool:

    See build scripts 'build_release_os.bat' and 'build_debug_os.bat' in .\p4-gt\tools directory

	Building P4GT [x86] Release plug-ins via command line:

         *  cd p4-gt\libp4gt
             command:  msbuild.exe libp4gt_os.vcxproj /t:Rebuild /p:Configuration=Release 
             	[artifact produced: .\Release\libp4gt_os.lib]

         *  cd ..\photoshop_cc
             command: msbuild.exe photoshop_os.vcxproj /t:Rebuild /p:Configuration=Release 
                 [distributable artifact produced: .\Release\P4GT-Photoshop.8li]

--

	Building P4GT [x64] Release plug-ins via command line:

         *  cd p4-gt\libp4gt
             command:  msbuild.exe libp4gt_os.vcxproj /t:Rebuild /p:Configuration=Release /p:Platform=x64
             	[artifact produced: .\Release\libp4gt_os.lib]

         *  cd ..\max2014
             command: msbuild.exe max_os.vcxproj /t:Rebuild /p:Configuration=Release /p:Platform=x64
                 [distributable artifact produced: .\Release\P4GT-3dsmax.gup]

         *  cd ..\maya2014
             command: msbuild.exe maya_os.vcxproj /t:Rebuild /p:Configuration=Release /p:Platform=x64
                 [distributable artifact produced: .\Release\P4GT-Maya.mll]

         *  cd ..\softimage2014
             command: msbuild.exe softimage_os.vcxproj /t:Rebuild /p:Configuration=Release /p:Platform=x64
                 [distributable artifact produced: .\Release\P4GT-Softimage.dll]

         *  cd ..\photoshop_cc
             command: msbuild.exe photoshop_os.vcxproj /t:Rebuild /p:Configuration=Release /p:Platform=x64
                 [distributable artifact produced: .\Release\P4GT-Photoshop.8li]

--

	Building P4GT [x86] Debug plug-ins via command line:

         *  cd p4-gt\libp4gt
             command:  msbuild.exe libp4gt_os.vcxproj /t:Rebuild /p:Configuration=Debug 
             	[artifact produced: .\Debug\libp4gt_os.lib]

         *  cd ..\photoshop_cc
             command: msbuild.exe photoshop_os.vcxproj /t:Rebuild /p:Configuration=Debug 
                 [distributable artifact produced: .\Debug\P4GT-Photoshop.8li]

--

	Building P4GT [x64] Debug plug-ins via command line:

         *  cd p4-gt\libp4gt
             command:  msbuild.exe libp4gt_os.vcxproj /t:Rebuild /p:Configuration=Debug /p:Platform=x64
             	[artifact produced: .\Debug\libp4gt_os.lib]

         *  cd ..\max2014
             command: msbuild.exe max_os.vcxproj /t:Rebuild /p:Configuration=Debug /p:Platform=x64
                 [distributable artifact produced: .\Debug\P4GT-3dsmax.gup]

         *  cd ..\maya2014
             command: msbuild.exe maya_os.vcxproj /t:Rebuild /p:Configuration=Debug /p:Platform=x64
                 [distributable artifact produced: .\Debug\P4GT-Maya.mll]

         *  cd ..\softimage2014
             command: msbuild.exe softimage_os.vcxproj /t:Rebuild /p:Configuration=Debug /p:Platform=x64
                 [distributable artifact produced: .\Debug\P4GT-Softimage.dll]

         *  cd ..\photoshop_cc
             command: msbuild.exe photoshop_os.vcxproj /t:Rebuild /p:Configuration=Debug /p:Platform=x64
                 [distributable artifact produced: .\Debug\P4GT-Photoshop.8li]


----

# DIRECTORY LAYOUT FOR BUILDING P4GT PLUG-IN(S)

P4 API:
<root path>\p4api\dyn\lib.ntx64         {required libs for 64-bit release builds}
                 \dyng\lib.ntx64        {required libs for 64-bit debug builds}
				 \dyn\ntx86             {required libs for 32-bit release builds}
				 \dyng\ntx86			{required libs for 32-bit debug builds}	
                 \include\p4            {required headers}

P4GT and SDKs:
<root path>\p4-gt\htmlhelp              {help libs}
                 \libp4gt               {required files for build P4GT core lib}
                 \max2014               {required only for building 3ds max 2014 plug-in}
                 \maya2014              {required only for building Maya 2014 plug-in}
                 \photoshop_cc          {required only for building Photoshop CC plug-in}
                 \softimage2014
                 \tools                 
                 \sdk                   {placekeeper for targeted proprietary SDKs}
                     \max2014_x64\include
                                 \lib
                     \maya2014_x64\include
                                  \lib
                     \softimage2014_x64\include
                                       \lib\nt-x86-64
                     \photoshop_cc\pluginsdk\photoshopapi\photoshop
                     									 \pica_sp
                     \photoshop_cc\pluginsdk\samplecode\common\includes
                     										  \sources


----

# INSTALLING P4GT PLUG-IN(S)AND SUPPORTING FILES

See install script 'p4gt_install_os.bat'. This script assumes the graphic tool(s) is installed
in the default location(s).

For manual installation:

	3ds max 2014
		copy P4GT-3dsmax.gup into directory "C:\Program Files\Autodesk\3ds Max 2014\plugins"
		
	Maya 2014
		copy P4GT-Maya.mll into directory "C:\Program Files\Autodesk\Maya2014\bin\plug-ins"
		copy files perforceCreateUI.mel and perforceDeleteUI.mel into directory "C:\Program Files\Autodesk\Maya2014\scripts\others"

	Softimage 2014
		copy P4GT-Softimage.dll into directory "C:\Program Files\Autodesk\Softimage 2014\Application\Plugins"
		
	Photoshop CC [64-bit]
		copy P4GT-Photoshop.8li into directory "C:\Program Files\Adobe\Adobe Photoshop CC (64 Bit)\Plug-ins\Automate"

	Photoshop CC [32-bit]
		copy P4GT-Photoshop.8li into directory "C:\Program Files (x86)\Adobe\Adobe Photoshop CC\Plug-ins\Automate"
		
	Registering Help file:
		command: reg add "HKEY_LOCAL_MACHINE\Software\Perforce\P4GT" /V "HelpFilePath" /D <specify path to Perforce help file>\p4gt.chm /F


----

# UNINSTALLING P4GT PLUG-IN(S) AND SUPPORTING FILES

See uninstall script 'p4gt_uninstall_os.bat'. This script assumes the graphic tool(s) is installed
in the default location(s).


----

# SCRIPTS

* .\p4-gt\build_release_os.bat        -- script for building Release plug-ins 
* .\p4-gt\build_debug_os.bat          -- script for building Debug plug-ins 
* .\p4-gt\p4gt_install_os.bat         -- installer script for plug-ins, etc. {before running copy plug-in binaries into .\p4-gt directory}
* .\p4-gt\p4gt_uninstall_os.bat       -- uninstaller script for plug-ins, etc.
* .\p4-gt\tools\UpdateVersion_os.bat  -- used during build process; creates a header file containing build version info
