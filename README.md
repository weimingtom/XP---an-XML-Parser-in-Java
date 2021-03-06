# XP---an-XML-Parser-in-Java
James Clark XP Java implementation

XP - an XML Parser in Java
Version 0.5

Copyright (c) 1997, 1998 James Clark
See the file copying.txt for copying permission.

XP is an XML 1.0 parser written in Java. It is fully conforming: it detects all non well-formed documents. It is currently not a validating XML processor. However it can parse all external entities: external DTD subsets, external parameter entities and external general entities.

XP can be downloaded from ftp://ftp.jclark.com/pub/xml/xp.zip. This is a beta-test version.

It has the following design goals:

    Conformance and correctness. XP is designed to be 100% conformant to the XML 1.0 specification.
    High performance. XP aims to be the fastest conformant XML parser in Java.
    Layered structure. In addition to a normal high-level parser API, XP provides a low-level API that supports the construction of different kinds of XML parser (such as incremental parsers). 

A few caveats:

    It is not intended to work with JDK 1.0; it relies on JDK 1.1 features.
    It is designed more for applications that applets; thus reducing class file size was given relatively low priority.
    It is intended more for delivery of documents than for authoring, so error handling is brutal. 

XP supports the following encodings:

    UTF-8
    UTF-16
    ISO-8859-1
    US-ASCII 

XP consists of the following Java packages:

com.jclark.xml
    consists of the interface Version which defines a String constant string specifying the XP version 
com.jclark.xml.tok
    a low-level API which is designed to support the construction of a wide variety of different kinds of XML parser; the main class is com.jclark.xml.tok.Encoding which represents a possible encoding of a parsed XML entity and provides operations on byte arrays that represent all or part of an entity in that encoding 
com.jclark.xml.parse
    a parser with a callback style API; this is layered on top of com.jclark.xml.tok. This has three parallel subpackages; you must use com.jclark.xml.parse together with one of the subpackages according to the type of exceptions that your callbacks throw:

    com.jclark.xml.parse.io
        use this if your callbacks throw java.io.IOException; this provides the same interface as version 0.2 of XP 
    com.jclark.xml.parse.awt
        use this if your callbacks throw java.awt.AWTException 
    com.jclark.xml.parse.base
        use this if your callbacks throw some other kind of exception; alternatively you can copy and modify the code that implements com.jclark.xml.parser.awt to provide an exception type-safe wrapper for the kind of exception thrown by your callbacks 

com.jclark.xml.sax
    a SAX 1.0 driver implemented on top of com.jclark.xml.parse 
com.jclark.xml.output
    support for XML output; this builds on top of the JDK 1.1 Writer class 
com.jclark.xml.apps
    some simple example applications; Time which reports the time taken to parse XML documents; Normalize which outputs a normalized form of XML 

See the XP API documentation (generated by javadoc) for details.

James Clark 
