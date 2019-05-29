=========================================
FogLAMP "asset" C++ Filter plugin
=========================================

Readings data transformation plugin that can include/exclude/rename asset(s)

Example filter config:

	{
	"value": {
		"rules": [{
			"asset_name": "Random1",
			"action": "include"
		}, {
			"asset_name": "Random2",
			"action": "rename",
			"new_asset_name": "Random92"
		}, {
			"asset_name": "Random3",
			"action": "exclude"
		}, {
			"asset_name": "Random4",
			"action": "rename",
			"new_asset_name": "Random94"
		}, {
			"asset_name": "Random5",
			"action": "exclude"
		}, {
			"asset_name": "Random6",
			"action": "rename",
			"new_asset_name": "Random96"
		}, {
			"asset_name": "Random7",
			"action": "include"
		}],
		"defaultAction": "include"
		}
	}

So there is a "rules" list to be specified, in which each rule entry mentions "asset_name" to act upon, the "action" could be "include", "exclude" or "rename". And in case of "rename" action, the "new_asset_name" is also specified.

Also a "defaultAction" can be specified which could have values "include" or "exclude", this is the default action applicable to assets that haven't been explicitly mentioned in "rules" list.


Build
-----
To build FogLAMP "asset" C++ filter plugin:

.. code-block:: console

  $ mkdir build
  $ cd build
  $ cmake ..
  $ make

- By default the FogLAMP develop package header files and libraries
  are expected to be located in /usr/include/foglamp and /usr/lib/foglamp
- If **FOGLAMP_ROOT** env var is set and no -D options are set,
  the header files and libraries paths are pulled from the ones under the
  FOGLAMP_ROOT directory.
  Please note that you must first run 'make' in the FOGLAMP_ROOT directory.

You may also pass one or more of the following options to cmake to override 
this default behaviour:

- **FOGLAMP_SRC** sets the path of a FogLAMP source tree
- **FOGLAMP_INCLUDE** sets the path to FogLAMP header files
- **FOGLAMP_LIB sets** the path to FogLAMP libraries
- **FOGLAMP_INSTALL** sets the installation path of Random plugin

NOTE:
 - The **FOGLAMP_INCLUDE** option should point to a location where all the FogLAMP 
   header files have been installed in a single directory.
 - The **FOGLAMP_LIB** option should point to a location where all the FogLAMP
   libraries have been installed in a single directory.
 - 'make install' target is defined only when **FOGLAMP_INSTALL** is set

Examples:

- no options

  $ cmake ..

- no options and FOGLAMP_ROOT set

  $ export FOGLAMP_ROOT=/some_foglamp_setup

  $ cmake ..

- set FOGLAMP_SRC

  $ cmake -DFOGLAMP_SRC=/home/source/develop/FogLAMP  ..

- set FOGLAMP_INCLUDE

  $ cmake -DFOGLAMP_INCLUDE=/dev-package/include ..
- set FOGLAMP_LIB

  $ cmake -DFOGLAMP_LIB=/home/dev/package/lib ..
- set FOGLAMP_INSTALL

  $ cmake -DFOGLAMP_INSTALL=/home/source/develop/FogLAMP ..

  $ cmake -DFOGLAMP_INSTALL=/usr/local/foglamp ..
