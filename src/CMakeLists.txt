add_executable(init
	bootchart.c
	builtins.c
	devices.c
	init.c
	logo.c
	parser.c
	property_service.c
	util.c
)

target_compile_definitions(init PRIVATE BOOTCHART=1)

target_link_libraries(init bsd internal)
