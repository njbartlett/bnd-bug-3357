JavaFX System Bundle Extension
==============================

This is an OSGi Framework Extension bundle that exports the JavaFX packages from the System Bundle.

Note that in order to work, the OSGi Framework launcher should have visibility of classes in the JRE Endorsed Library path, i.e. the extension classloader. This is the default if the launcher is running from the application classloader.

When running as an Eclipse application, set the parent of the Equinox framework classloader as follows:

	-Dosgi.frameworkParentClassloader=ext

Usage
-----

Bundles using JavaFX can choose to import the packages in the normal way with version ranges. This is more suitable for consumers that generate a MANIFEST.MF using bnd:

	Import-Package: javafx.scene; version="[2.2,3.0)",
	  javafx.scene.paint; version="[2.2,3.0)",
	  javafx.stage; version="[2.2,3.0)",
	  ...


Alternatively the [OSGi Portable Contracts](https://www.osgi.org/portable-java-contract-definitions/) mechanism can be used:

	Require-Capability: 
	  osgi.contract; filter="(&(osgi.contract=JavaFX)(version>=2.2)(!(version>=3.0)))"
	Import-Package: javafx.scene,
	  javafx.scene.paint,
	  javafx.stage,
	  ...
