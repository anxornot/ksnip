find_package(Qt${QT_MAJOR_VERSION}LinguistTools)

set(KSNIP_LANG_TS
	ksnip_ar.ts
	ksnip_bn_BD.ts
	ksnip_ca.ts
	ksnip_cs.ts
	ksnip_da.ts
	ksnip_de.ts
	ksnip_el.ts
	ksnip_es.ts
	ksnip_eu.ts
	ksnip_fa.ts
	ksnip_fi.ts
	ksnip_fr.ts
	ksnip_fr_CA.ts
	ksnip_gl.ts
	ksnip_he.ts
	ksnip_hr.ts
	ksnip_hu.ts
	ksnip_id.ts
	ksnip_it.ts
	ksnip_ja.ts
	ksnip_ko.ts
	ksnip_nl.ts
	ksnip_no.ts
	ksnip_pl.ts
	ksnip_pt.ts
	ksnip_pt_BR.ts
	ksnip_ro.ts
	ksnip_ru.ts
	ksnip_si.ts
	ksnip_sl.ts
	ksnip_sv.ts
	ksnip_tr.ts
	ksnip_uk.ts
	ksnip_zh_CN.ts
	ksnip_zh_Hant.ts)

if (DEFINED UPDATE_TS_FILES)
	if (BUILD_WITH_QT6)
		qt6_create_translation(KSNIP_LANG_QM ${CMAKE_SOURCE_DIR}/translations ${KSNIP_SRCS} ${KSNIP_LANG_TS} OPTIONS "-no-obsolete")
	else ()
		qt5_create_translation(KSNIP_LANG_QM ${CMAKE_SOURCE_DIR}/translations ${KSNIP_SRCS} ${KSNIP_LANG_TS} OPTIONS "-no-obsolete")
	endif ()
else ()
	if (BUILD_WITH_QT6)
		qt6_add_translation(KSNIP_LANG_QM ${KSNIP_LANG_TS})
	else ()
		qt5_add_translation(KSNIP_LANG_QM ${KSNIP_LANG_TS})
	endif ()
endif ()

add_custom_target(translations ALL DEPENDS ${KSNIP_LANG_QM})

install(FILES ${KSNIP_LANG_QM} DESTINATION ${KSNIP_LANG_INSTALL_DIR})

