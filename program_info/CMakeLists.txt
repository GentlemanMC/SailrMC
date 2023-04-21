if(UNIX)
    find_package(PkgConfig)
    if(PkgConfig_FOUND)
        pkg_search_module(SCDOC scdoc)
        if(SCDOC_FOUND)
            pkg_get_variable(SCDOC_SCDOC scdoc scdoc)
        endif()
    endif()
endif()

set(Launcher_CommonName "SailrMC")
set(Launcher_DisplayName "SailrMC")

set(Launcher_Name "${Launcher_CommonName}" PARENT_SCOPE)
set(Launcher_DisplayName "${Launcher_DisplayName}" PARENT_SCOPE)

set(Launcher_Copyright "SailrMC Contributors\\n© 2022-2023 Prism Launcher Contributors\\n© 2021-2022 PolyMC Contributors \\n© 2012-2021 MultiMC Contributors")
set(Launcher_Copyright_Mac "SailrMC Contributors, © Prism Launcher Contributors, © 2021-2022 PolyMC Contributors and © 2012-2021 MultiMC Contributors" PARENT_SCOPE)
set(Launcher_Copyright "${Launcher_Copyright}" PARENT_SCOPE)
set(Launcher_Domain "sailrmc.github.io" PARENT_SCOPE)
set(Launcher_UserAgent "${Launcher_CommonName}/${Launcher_VERSION_NAME}" PARENT_SCOPE)
set(Launcher_ConfigFile "sailrmc.cfg" PARENT_SCOPE)
set(Launcher_Git "https://github.com/SailrMC/SailrMC" PARENT_SCOPE)
set(Launcher_DesktopFileName "org.sailrmc.SailrMC.desktop" PARENT_SCOPE)
set(Launcher_SVGFileName "org.sailrmc.SailrMC.svg" PARENT_SCOPE)

set(Launcher_Desktop "program_info/org.sailrmc.SailrMC.desktop" PARENT_SCOPE)
set(Launcher_mrpack_MIMEInfo "program_info/modrinth-mrpack-mime.xml" PARENT_SCOPE)
set(Launcher_MetaInfo "program_info/org.sailrmc.SailrMC.metainfo.xml" PARENT_SCOPE)
set(Launcher_SVG "program_info/org.sailrmc.SailrMC.svg" PARENT_SCOPE)
set(Launcher_Branding_ICNS "program_info/sailrmc.icns" PARENT_SCOPE)
set(Launcher_Branding_ICO "program_info/sailrmc.ico")
set(Launcher_Branding_ICO "${Launcher_Branding_ICO}" PARENT_SCOPE)
set(Launcher_Branding_WindowsRC "program_info/sailrmc.rc" PARENT_SCOPE)
set(Launcher_Branding_LogoQRC "program_info/sailrmc.qrc" PARENT_SCOPE)

set(Launcher_Portable_File "program_info/portable.txt" PARENT_SCOPE)

configure_file(org.sailrmc.SailrMC.desktop.in org.sailrmc.SailrMC.desktop)
configure_file(org.sailrmc.SailrMC.metainfo.xml.in org.sailrmc.SailrMC.metainfo.xml)
configure_file(sailrmc.rc.in sailrmc.rc @ONLY)
configure_file(sailrmc.manifest.in sailrmc.manifest @ONLY)
configure_file(sailrmc.ico sailrmc.ico COPYONLY)
configure_file(win_install.nsi.in win_install.nsi @ONLY)

if(SCDOC_FOUND)
    set(in_scd "${CMAKE_CURRENT_SOURCE_DIR}/sailrmc.6.scd")
    set(out_man "${CMAKE_CURRENT_BINARY_DIR}/sailrmc.6")
    add_custom_command(
        DEPENDS "${in_scd}"
        OUTPUT "${out_man}"
        COMMAND ${SCDOC_SCDOC} < "${in_scd}" > "${out_man}"
    )
    add_custom_target(man ALL DEPENDS ${out_man})
    set(Launcher_ManPage "program_info/sailrmc.6" PARENT_SCOPE)
endif()
