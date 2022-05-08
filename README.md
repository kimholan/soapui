Patched - analytics free
========================

Check original repository for the real README.MD.

Modifications:
- JDK17 update / JavaFX17
- Removed all references to analytics
- Added locking to the following classes as it causes SoapUI to free on systems with high core counts:
    - WsdlProjectRunner
    - WsdlTestCaseRunner
- Removed maven plugin from codebase (it just adds overhead in CI/CD)
- Added dependencies for
    - Optional BouncyCastle dependencies
    - snakeyaml
    - jsonassert

Notes
=====

Updated to upstream as of time of writing. SoapUI now 'just builds' on JDK17 in upstream, so there is no
more need to switch around to JDK8 and back due to xmlbeans.

The build in upstream fails as usual if the included tests are run.


Build on Linux
==============

Build environment:
```
developer@computer:~/workspace/com_github_kimholan_soapui$ mvn --version
Apache Maven 3.9.9 (8e8579a9e76f7d015ee5ec7bfcdc97d260186937)
Maven home: /home/developer/lib/maven
Java version: 17.0.12, vendor: Eclipse Adoptium, runtime: /home/developer/lib/jdk-17.0.12+7
Default locale: nl_NL, platform encoding: UTF-8
OS name: "linux", version: "6.9.7+bpo-amd64", arch: "amd64", family: "unix"

developer@computer:~/workspace/com_github_kimholan_soapui$ java --version
openjdk 17.0.12 2024-07-16
OpenJDK Runtime Environment Temurin-17.0.12+7 (build 17.0.12+7)
OpenJDK 64-Bit Server VM Temurin-17.0.12+7 (build 17.0.12+7, mixed mode, sharing)
```

Build log:
```
[INFO] Scanning for projects...
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Build Order:
[INFO] 
[INFO] SoapUI project                                                     [pom]
[INFO] SoapUI                                                             [jar]
[INFO] SoapUI installer                                                   [jar]
[INFO] SoapUI system test                                                 [jar]
[INFO] 
[INFO] ----------------< com.smartbear.soapui:soapui-project >-----------------
[INFO] Building SoapUI project 5.8.0-annona-squamosa                      [1/4]
[INFO]   from pom.xml
[INFO] --------------------------------[ pom ]---------------------------------
[INFO] 
[INFO] --- clean:3.3.2:clean (default-clean) @ soapui-project ---
[INFO] Deleting /home/developer/workspace/github_kimholan_soapui (includes = [*.log], excludes = [])
[INFO] 
[INFO] --- install:3.1.2:install (default-install) @ soapui-project ---
[INFO] Installing /home/developer/workspace/github_kimholan_soapui/pom.xml to /home/developer/.m2/repository/com/smartbear/soapui/soapui-project/5.8.0-annona-squamosa/soapui-project-5.8.0-annona-squamosa.pom
[INFO] 
[INFO] --------------------< com.smartbear.soapui:soapui >---------------------
[INFO] Building SoapUI 5.8.0-annona-squamosa                              [2/4]
[INFO]   from soapui/pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[WARNING] 1 problem was encountered while building the effective model for org.javassist:javassist:jar:3.16.1-GA during dependency collection step for project (use -X to see details)
[WARNING] 1 problem was encountered while building the effective model for org.javassist:javassist:jar:3.21.0-GA during dependency collection step for project (use -X to see details)
[WARNING] 1 problem was encountered while building the effective model for org.javassist:javassist:jar:3.20.0-GA during dependency collection step for project (use -X to see details)
[INFO] 
[INFO] --- clean:3.3.2:clean (default-clean) @ soapui ---
[INFO] Deleting /home/developer/workspace/github_kimholan_soapui/soapui/target
[INFO] Deleting /home/developer/workspace/github_kimholan_soapui/soapui (includes = [*.log], excludes = [])
[INFO] 
[INFO] --- xmlbeans:2.3.5-sb-fixed:xmlbeans (default) @ soapui ---
[INFO] 
[INFO] --- resources:3.3.1:resources (default-resources) @ soapui ---
[INFO] Copying 438 resources from src/main/resources to target/classes
[INFO] Copying 5419 resources from target/generated-classes/xmlbeans to target/classes
[INFO] The encoding used to copy filtered properties files have not been set. This means that the same encoding will be used to copy filtered properties files as when copying other filtered resources. This might not be what you want! Run your build with --debug to see which files might be affected. Read more at https://maven.apache.org/plugins/maven-resources-plugin/examples/filtering-properties-files.html
[INFO] 
[INFO] --- compiler:3.13.0:compile (default-compile) @ soapui ---
[INFO] Recompiling the module because of changed source code.
[INFO] Compiling 3382 source files with javac [debug target 1.9] to target/classes
[WARNING] bootstrap class path not set in conjunction with -source 8
[INFO] Processing Log4j annotations
[INFO] Annotations processed
[INFO] CAL10NAnnotationProcessor 0.8.1 initialized
[WARNING] Supported source version 'RELEASE_5' from annotation processor 'ch.qos.cal10n.verifier.processor.CAL10NAnnotationProcessor' less than -source '8'
[INFO] Processing Log4j annotations
[INFO] No elements to process
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/loadtest/data/LoadTestStatistics.java:[217,24] Float(float) in java.lang.Float has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/loadtest/data/LoadTestStatistics.java:[223,66] Long(long) in java.lang.Long has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/loadtest/data/LoadTestStatistics.java:[223,80] Long(long) in java.lang.Long has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/loadtest/data/StatisticsHistory.java:[198,24] Long(long) in java.lang.Long has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/support/components/PreviewCorner.java:[138,39] Integer(int) in java.lang.Integer has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/support/components/PreviewCorner.java:[139,40] Integer(int) in java.lang.Integer has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/actions/iface/tools/wsi/WSIAnalyzeAction.java:[253,63] Integer(int) in java.lang.Integer has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/loadtest/assertions/AbstractLoadTestAssertion.java:[158,26] Long(long) in java.lang.Long has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/support/action/swing/SwingActionDelegate.java:[77,43] Integer(int) in java.lang.Integer has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/panels/mockoperation/actions/WSIValidateResponseAction.java:[294,67] Integer(int) in java.lang.Integer has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/panels/request/actions/WSIValidateRequestAction.java:[310,63] Integer(int) in java.lang.Integer has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/panels/teststeps/support/NamedParameterStatement.java:[105,35] Integer(int) in java.lang.Integer has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/submit/filters/AbstractWssRequestFilter.java:[62,64] Integer(int) in java.lang.Integer has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/submit/filters/AbstractWssRequestFilter.java:[75,56] Integer(int) in java.lang.Integer has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/teststeps/assertions/jms/JMSTimeoutAssertion.java:[128,42] Long(long) in java.lang.Long has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/teststeps/assertions/jms/JMSTimeoutAssertion.java:[132,42] Long(java.lang.String) in java.lang.Long has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/security/assertion/CrossSiteScriptAssertion.java:[351,58] Boolean(java.lang.String) in java.lang.Boolean has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/security/ui/MaliciousAttachmentMutationsPanel.java:[302,35] Boolean(boolean) in java.lang.Boolean has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/security/ui/MaliciousAttachmentMutationsPanel.java:[367,39] Boolean(boolean) in java.lang.Boolean has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/security/ui/MaliciousAttachmentMutationsPanel.java:[368,38] Boolean(boolean) in java.lang.Boolean has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/security/support/MaliciousAttachmentListToTableHolder.java:[131,66] Boolean(boolean) in java.lang.Boolean has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/security/support/MaliciousAttachmentFilesListForm.java:[103,78] Boolean(boolean) in java.lang.Boolean has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/security/support/MaliciousAttachmentFilesListForm.java:[112,86] Boolean(boolean) in java.lang.Boolean has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/support/action/swing/SwingMultiActionDelegate.java:[70,43] Integer(int) in java.lang.Integer has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/tools/SoapUITestCaseRunner.java:[632,21] Long(long) in java.lang.Long has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/tools/SoapUITestCaseRunner.java:[635,51] Long(long) in java.lang.Long has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/tools/SoapUISecurityTestRunner.java:[358,22] Long(long) in java.lang.Long has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/tools/SoapUISecurityTestRunner.java:[362,21] Long(long) in java.lang.Long has been deprecated and marked for removal
[WARNING] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/tools/SoapUISecurityTestRunner.java:[365,51] Long(long) in java.lang.Long has been deprecated and marked for removal
[INFO] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/monitor/jettyproxy/ProxyServlet.java: Some input files use or override a deprecated API.
[INFO] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/monitor/jettyproxy/ProxyServlet.java: Recompile with -Xlint:deprecation for details.
[INFO] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/panels/teststeps/AssertionsPanel.java: Some input files use unchecked or unsafe operations.
[INFO] /home/developer/workspace/github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/wsdl/panels/teststeps/AssertionsPanel.java: Recompile with -Xlint:unchecked for details.
[INFO] 
[INFO] --- resources:3.3.1:testResources (default-testResources) @ soapui ---
[INFO] Copying 57 resources from src/test/resources to target/test-classes
[INFO] 
[INFO] --- compiler:3.13.0:testCompile (default-testCompile) @ soapui ---
[INFO] Recompiling the module because of changed dependency.
[INFO] Compiling 143 source files with javac [debug target 1.9] to target/test-classes
[WARNING] bootstrap class path not set in conjunction with -source 8
[INFO] CAL10NAnnotationProcessor 0.8.1 initialized
[WARNING] Supported source version 'RELEASE_5' from annotation processor 'ch.qos.cal10n.verifier.processor.CAL10NAnnotationProcessor' less than -source '8'
[INFO] /home/developer/workspace/github_kimholan_soapui/soapui/src/test/java/com/eviware/soapui/actions/MockAsWarActionTest.java: Some input files use or override a deprecated API.
[INFO] /home/developer/workspace/github_kimholan_soapui/soapui/src/test/java/com/eviware/soapui/actions/MockAsWarActionTest.java: Recompile with -Xlint:deprecation for details.
[INFO] /home/developer/workspace/github_kimholan_soapui/soapui/src/test/java/com/eviware/soapui/impl/GenericPanelBuilderTest.java: Some input files use unchecked or unsafe operations.
[INFO] /home/developer/workspace/github_kimholan_soapui/soapui/src/test/java/com/eviware/soapui/impl/GenericPanelBuilderTest.java: Recompile with -Xlint:unchecked for details.
[INFO] 
[INFO] --- surefire:3.2.5:test (default-test) @ soapui ---
[WARNING]  Parameter 'systemProperties' is deprecated: Use systemPropertyVariables instead.
[INFO] Tests are skipped.
[INFO] 
[INFO] --- jar:3.4.1:jar (default-jar) @ soapui ---
[INFO] Building jar: /home/developer/workspace/github_kimholan_soapui/soapui/target/soapui-5.8.0-annona-squamosa.jar
[INFO] 
[INFO] --- jar:3.4.1:test-jar (default) @ soapui ---
[INFO] Building jar: /home/developer/workspace/github_kimholan_soapui/soapui/target/soapui-5.8.0-annona-squamosa-tests.jar
[INFO] 
[INFO] --- install:3.1.2:install (default-install) @ soapui ---
[INFO] Installing /home/developer/workspace/github_kimholan_soapui/soapui/pom.xml to /home/developer/.m2/repository/com/smartbear/soapui/soapui/5.8.0-annona-squamosa/soapui-5.8.0-annona-squamosa.pom
[INFO] Installing /home/developer/workspace/github_kimholan_soapui/soapui/target/soapui-5.8.0-annona-squamosa.jar to /home/developer/.m2/repository/com/smartbear/soapui/soapui/5.8.0-annona-squamosa/soapui-5.8.0-annona-squamosa.jar
[INFO] Installing /home/developer/workspace/github_kimholan_soapui/soapui/target/soapui-5.8.0-annona-squamosa-tests.jar to /home/developer/.m2/repository/com/smartbear/soapui/soapui/5.8.0-annona-squamosa/soapui-5.8.0-annona-squamosa-tests.jar
[INFO] 
[INFO] ---------------< com.smartbear.soapui:soapui-installer >----------------
[INFO] Building SoapUI installer 5.8.0-annona-squamosa                    [3/4]
[INFO]   from soapui-installer/pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- clean:3.3.2:clean (default-clean) @ soapui-installer ---
[INFO] Deleting /home/developer/workspace/github_kimholan_soapui/soapui-installer/target
[INFO] Deleting /home/developer/workspace/github_kimholan_soapui/soapui-installer (includes = [*.log], excludes = [])
[INFO] 
[INFO] --- resources:3.3.1:resources (default-resources) @ soapui-installer ---
[INFO] Copying 2 resources from src/main/resources to target/classes
[INFO] 
[INFO] --- compiler:3.13.0:compile (default-compile) @ soapui-installer ---
[INFO] No sources to compile
[INFO] 
[INFO] --- resources:3.3.1:testResources (default-testResources) @ soapui-installer ---
[INFO] skip non existing resourceDirectory /home/developer/workspace/github_kimholan_soapui/soapui-installer/src/test/resources
[INFO] 
[INFO] --- compiler:3.13.0:testCompile (default-testCompile) @ soapui-installer ---
[INFO] No sources to compile
[INFO] 
[INFO] --- surefire:3.2.5:test (default-test) @ soapui-installer ---
[INFO] Tests are skipped.
[INFO] 
[INFO] --- exec:3.0.0:java (default) @ soapui-installer ---
[INFO] 
[INFO] --- jar:3.4.1:jar (default-jar) @ soapui-installer ---
[INFO] Building jar: /home/developer/workspace/github_kimholan_soapui/soapui-installer/target/soapui-installer-5.8.0-annona-squamosa.jar
[INFO] 
[INFO] --- assembly:3.7.1:single (default) @ soapui-installer ---
[INFO] Reading assembly descriptor: src/main/assembly/dist.xml
[INFO] Reading assembly descriptor: src/main/assembly/dist-standalone.xml
[INFO] Reading assembly descriptor: src/main/assembly/windows-bin.xml
[INFO] Reading assembly descriptor: src/main/assembly/linux-bin.xml
[INFO] Artifact wsdl4j:wsdl4j:pom:1.6.2-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact wsdl4j:wsdl4j:pom:1.6.2-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-fontchooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-fontchooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xerces:xml-apis:pom:2.9.1 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xerces:xml-apis:pom:2.9.1 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact swingx:swingx:pom:soapui is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact swingx:swingx:pom:soapui is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-proxy:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-proxy:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact thoughtworks:xstream:pom:1.4.13 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact thoughtworks:xstream:pom:1.4.13 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-directorychooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-directorychooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-core:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-core:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact net.sf.saxon:saxon:pom:9 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact net.sf.saxon:saxon:pom:9 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.sonatype.install4j:i4jruntime:pom:5.1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.sonatype.install4j:i4jruntime:pom:5.1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jtidy:jtidy:pom:r872-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jtidy:jtidy:pom:r872-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.btr:proxy-vole:pom:20131209 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.btr:proxy-vole:pom:20131209 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact ezmorph:ezmorph:pom:1.0.5 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact ezmorph:ezmorph:pom:1.0.5 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-remoting:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-remoting:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon-dom:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon-dom:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:servlet-api:pom:2.5-20081211 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:servlet-api:pom:2.5-20081211 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-opt:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-opt:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact hermesjms:hermes:pom:1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact hermesjms:hermes:pom:1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.jayway.jsonpath:json-path:pom:2.4.0-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.jayway.jsonpath:json-path:pom:2.4.0-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-common:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-common:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty-util:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty-util:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact json:json-lib:pom:2.2.2-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact json:json-lib:pom:2.2.2-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xmlbeans:xmlbeans:pom:3.1.1-sb-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xmlbeans:xmlbeans:pom:3.1.1-sb-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Copying files to /home/developer/workspace/github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.8.0-annona-squamosa-dist
[INFO] 332 files copied to /home/developer/workspace/github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.8.0-annona-squamosa-dist
[WARNING] Assembly file: /home/developer/workspace/github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.8.0-annona-squamosa-dist is not a regular file (it may be a directory). It cannot be attached to the project build for installation or deployment.
[INFO] Artifact wsdl4j:wsdl4j:pom:1.6.2-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact wsdl4j:wsdl4j:pom:1.6.2-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-fontchooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-fontchooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xerces:xml-apis:pom:2.9.1 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xerces:xml-apis:pom:2.9.1 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact swingx:swingx:pom:soapui is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact swingx:swingx:pom:soapui is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-proxy:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-proxy:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact thoughtworks:xstream:pom:1.4.13 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact thoughtworks:xstream:pom:1.4.13 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-directorychooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-directorychooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-core:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-core:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact net.sf.saxon:saxon:pom:9 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact net.sf.saxon:saxon:pom:9 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.sonatype.install4j:i4jruntime:pom:5.1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.sonatype.install4j:i4jruntime:pom:5.1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jtidy:jtidy:pom:r872-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jtidy:jtidy:pom:r872-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.btr:proxy-vole:pom:20131209 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.btr:proxy-vole:pom:20131209 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact ezmorph:ezmorph:pom:1.0.5 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact ezmorph:ezmorph:pom:1.0.5 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-remoting:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-remoting:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon-dom:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon-dom:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:servlet-api:pom:2.5-20081211 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:servlet-api:pom:2.5-20081211 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-opt:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-opt:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact hermesjms:hermes:pom:1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact hermesjms:hermes:pom:1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.jayway.jsonpath:json-path:pom:2.4.0-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.jayway.jsonpath:json-path:pom:2.4.0-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-common:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-common:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty-util:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty-util:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact json:json-lib:pom:2.2.2-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact json:json-lib:pom:2.2.2-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xmlbeans:xmlbeans:pom:3.1.1-sb-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xmlbeans:xmlbeans:pom:3.1.1-sb-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Copying files to /home/developer/workspace/github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.8.0-annona-squamosa-dist-standalone
[INFO] 332 files copied to /home/developer/workspace/github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.8.0-annona-squamosa-dist-standalone
[WARNING] Assembly file: /home/developer/workspace/github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.8.0-annona-squamosa-dist-standalone is not a regular file (it may be a directory). It cannot be attached to the project build for installation or deployment.
[INFO] Artifact wsdl4j:wsdl4j:pom:1.6.2-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact wsdl4j:wsdl4j:pom:1.6.2-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-fontchooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-fontchooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xerces:xml-apis:pom:2.9.1 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xerces:xml-apis:pom:2.9.1 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact swingx:swingx:pom:soapui is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact swingx:swingx:pom:soapui is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-proxy:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-proxy:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact thoughtworks:xstream:pom:1.4.13 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact thoughtworks:xstream:pom:1.4.13 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-directorychooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-directorychooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-core:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-core:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact net.sf.saxon:saxon:pom:9 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact net.sf.saxon:saxon:pom:9 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.sonatype.install4j:i4jruntime:pom:5.1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.sonatype.install4j:i4jruntime:pom:5.1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jtidy:jtidy:pom:r872-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jtidy:jtidy:pom:r872-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.btr:proxy-vole:pom:20131209 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.btr:proxy-vole:pom:20131209 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact ezmorph:ezmorph:pom:1.0.5 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact ezmorph:ezmorph:pom:1.0.5 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-remoting:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-remoting:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon-dom:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon-dom:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:servlet-api:pom:2.5-20081211 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:servlet-api:pom:2.5-20081211 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-opt:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-opt:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact hermesjms:hermes:pom:1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact hermesjms:hermes:pom:1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.jayway.jsonpath:json-path:pom:2.4.0-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.jayway.jsonpath:json-path:pom:2.4.0-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-common:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-common:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty-util:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty-util:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact json:json-lib:pom:2.2.2-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact json:json-lib:pom:2.2.2-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xmlbeans:xmlbeans:pom:3.1.1-sb-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xmlbeans:xmlbeans:pom:3.1.1-sb-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Building zip: /home/developer/workspace/github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.8.0-annona-squamosa-windows-bin.zip
[INFO] Artifact wsdl4j:wsdl4j:pom:1.6.2-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact wsdl4j:wsdl4j:pom:1.6.2-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-fontchooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-fontchooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xerces:xml-apis:pom:2.9.1 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xerces:xml-apis:pom:2.9.1 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact swingx:swingx:pom:soapui is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact swingx:swingx:pom:soapui is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-proxy:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-proxy:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact thoughtworks:xstream:pom:1.4.13 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact thoughtworks:xstream:pom:1.4.13 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-directorychooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact l2fprod:l2fprod-common-directorychooser:pom:7.3 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-core:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-core:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact net.sf.saxon:saxon:pom:9 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact net.sf.saxon:saxon:pom:9 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.sonatype.install4j:i4jruntime:pom:5.1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.sonatype.install4j:i4jruntime:pom:5.1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jtidy:jtidy:pom:r872-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jtidy:jtidy:pom:r872-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.btr:proxy-vole:pom:20131209 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.btr:proxy-vole:pom:20131209 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact ezmorph:ezmorph:pom:1.0.5 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact ezmorph:ezmorph:pom:1.0.5 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-remoting:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-remoting:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon-dom:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact saxon:saxon-dom:pom:9.1.0.8j is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:servlet-api:pom:2.5-20081211 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:servlet-api:pom:2.5-20081211 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-opt:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-opt:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact hermesjms:hermes:pom:1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact hermesjms:hermes:pom:1.14 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.jayway.jsonpath:json-path:pom:2.4.0-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact com.jayway.jsonpath:json-path:pom:2.4.0-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-common:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact amf:flex-messaging-common:pom:1.0 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty-util:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact jetty:jetty-util:pom:6.1.26 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact json:json-lib:pom:2.2.2-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact json:json-lib:pom:2.2.2-jdk15 is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xmlbeans:xmlbeans:pom:3.1.1-sb-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Artifact org.apache.xmlbeans:xmlbeans:pom:3.1.1-sb-fixed is present in the local repository, but cached from a remote repository ID that is unavailable in current build context, verifying that is downloadable from [central (https://repo.maven.apache.org/maven2, default, releases)]
[INFO] Building tar: /home/developer/workspace/github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.8.0-annona-squamosa-linux-bin.tar.gz
[INFO] 
[INFO] --- install:3.1.2:install (default-install) @ soapui-installer ---
[INFO] Installing /home/developer/workspace/github_kimholan_soapui/soapui-installer/pom.xml to /home/developer/.m2/repository/com/smartbear/soapui/soapui-installer/5.8.0-annona-squamosa/soapui-installer-5.8.0-annona-squamosa.pom
[INFO] Installing /home/developer/workspace/github_kimholan_soapui/soapui-installer/target/soapui-installer-5.8.0-annona-squamosa.jar to /home/developer/.m2/repository/com/smartbear/soapui/soapui-installer/5.8.0-annona-squamosa/soapui-installer-5.8.0-annona-squamosa.jar
[INFO] Installing /home/developer/workspace/github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.8.0-annona-squamosa-windows-bin.zip to /home/developer/.m2/repository/com/smartbear/soapui/soapui-installer/5.8.0-annona-squamosa/soapui-installer-5.8.0-annona-squamosa-windows-bin.zip
[INFO] Installing /home/developer/workspace/github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.8.0-annona-squamosa-linux-bin.tar.gz to /home/developer/.m2/repository/com/smartbear/soapui/soapui-installer/5.8.0-annona-squamosa/soapui-installer-5.8.0-annona-squamosa-linux-bin.tar.gz
[INFO] 
[INFO] --------------< com.smartbear.soapui:soapui-system-test >---------------
[INFO] Building SoapUI system test 5.8.0-annona-squamosa                  [4/4]
[INFO]   from soapui-system-test/pom.xml
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- clean:3.3.2:clean (default-clean) @ soapui-system-test ---
[INFO] Deleting /home/developer/workspace/github_kimholan_soapui/soapui-system-test/target
[INFO] Deleting /home/developer/workspace/github_kimholan_soapui/soapui-system-test (includes = [*.log], excludes = [])
[INFO] 
[INFO] --- resources:3.3.1:resources (default-resources) @ soapui-system-test ---
[INFO] skip non existing resourceDirectory /home/developer/workspace/github_kimholan_soapui/soapui-system-test/src/main/resources
[INFO] 
[INFO] --- compiler:3.13.0:compile (default-compile) @ soapui-system-test ---
[INFO] No sources to compile
[INFO] 
[INFO] --- resources:3.3.1:testResources (default-testResources) @ soapui-system-test ---
[INFO] Copying 81 resources from src/test/resources to target/test-classes
[INFO] 
[INFO] --- compiler:3.13.0:testCompile (default-testCompile) @ soapui-system-test ---
[INFO] Recompiling the module because of changed dependency.
[INFO] Compiling 26 source files with javac [debug target 1.9] to target/test-classes
[WARNING] bootstrap class path not set in conjunction with -source 8
[INFO] CAL10NAnnotationProcessor 0.8.1 initialized
[WARNING] Supported source version 'RELEASE_5' from annotation processor 'ch.qos.cal10n.verifier.processor.CAL10NAnnotationProcessor' less than -source '8'
[INFO] /home/developer/workspace/github_kimholan_soapui/soapui-system-test/src/test/java/com/eviware/soapui/support/components/EnabledWebViewBasedBrowserComponentTest.java: Some input files use or override a deprecated API.
[INFO] /home/developer/workspace/github_kimholan_soapui/soapui-system-test/src/test/java/com/eviware/soapui/support/components/EnabledWebViewBasedBrowserComponentTest.java: Recompile with -Xlint:deprecation for details.
[INFO] 
[INFO] --- surefire:3.2.5:test (default-test) @ soapui-system-test ---
[INFO] Tests are skipped.
[INFO] 
[INFO] --- jar:3.4.1:jar (default-jar) @ soapui-system-test ---
[WARNING] JAR will be empty - no content was marked for inclusion!
[INFO] Building jar: /home/developer/workspace/github_kimholan_soapui/soapui-system-test/target/soapui-system-test-5.8.0-annona-squamosa.jar
[INFO] 
[INFO] --- jar:3.4.1:test-jar (default) @ soapui-system-test ---
[INFO] Building jar: /home/developer/workspace/github_kimholan_soapui/soapui-system-test/target/soapui-system-test-5.8.0-annona-squamosa-tests.jar
[INFO] 
[INFO] --- install:3.1.2:install (default-install) @ soapui-system-test ---
[INFO] Installing /home/developer/workspace/github_kimholan_soapui/soapui-system-test/pom.xml to /home/developer/.m2/repository/com/smartbear/soapui/soapui-system-test/5.8.0-annona-squamosa/soapui-system-test-5.8.0-annona-squamosa.pom
[INFO] Installing /home/developer/workspace/github_kimholan_soapui/soapui-system-test/target/soapui-system-test-5.8.0-annona-squamosa.jar to /home/developer/.m2/repository/com/smartbear/soapui/soapui-system-test/5.8.0-annona-squamosa/soapui-system-test-5.8.0-annona-squamosa.jar
[INFO] Installing /home/developer/workspace/github_kimholan_soapui/soapui-system-test/target/soapui-system-test-5.8.0-annona-squamosa-tests.jar to /home/developer/.m2/repository/com/smartbear/soapui/soapui-system-test/5.8.0-annona-squamosa/soapui-system-test-5.8.0-annona-squamosa-tests.jar
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for SoapUI project 5.8.0-annona-squamosa:
[INFO] 
[INFO] SoapUI project ..................................... SUCCESS [  0.172 s]
[INFO] SoapUI ............................................. SUCCESS [ 32.849 s]
[INFO] SoapUI installer ................................... SUCCESS [  7.614 s]
[INFO] SoapUI system test ................................. SUCCESS [  0.457 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  41.175 s
[INFO] Finished at: 2025-01-11T09:18:26+01:00
[INFO] ------------------------------------------------------------------------
```

Assembly contents
=================

The assembly built contains the following JARS:

```
developer@computer:~/workspace/com_github_kimholan_soapui$ tar tvf ./soapui-installer/target/assemblies/SoapUI-5.7.1-mangosteen-linux-bin.tar.gz  |grep jar | sed -e 's|^.* SoapUI-||' |  sort 
5.8.0-annona-squamosa/bin/soapui-5.8.0-annona-squamosa.jar
5.8.0-annona-squamosa/lib/accessors-smart-1.2.jar
5.8.0-annona-squamosa/lib/activation-1.1.jar
5.8.0-annona-squamosa/lib/android-json-0.0.20131108.vaadin1.jar
5.8.0-annona-squamosa/lib/animal-sniffer-annotations-1.11.jar
5.8.0-annona-squamosa/lib/ant-1.10.12.jar
5.8.0-annona-squamosa/lib/ant-antlr-1.10.12.jar
5.8.0-annona-squamosa/lib/ant-junit-1.10.12.jar
5.8.0-annona-squamosa/lib/ant-launcher-1.10.12.jar
5.8.0-annona-squamosa/lib/aopalliance-repackaged-2.6.1.jar
5.8.0-annona-squamosa/lib/bcmail-jdk15on-1.70.jar
5.8.0-annona-squamosa/lib/bcpkix-jdk15on-1.70.jar
5.8.0-annona-squamosa/lib/bcprov-jdk15on-1.70.jar
5.8.0-annona-squamosa/lib/bcutil-jdk15on-1.70.jar
5.8.0-annona-squamosa/lib/binding-2.0.1.jar
5.8.0-annona-squamosa/lib/btf-1.2.jar
5.8.0-annona-squamosa/lib/cal10n-api-0.8.1.jar
5.8.0-annona-squamosa/lib/commons-beanutils-1.9.4.jar
5.8.0-annona-squamosa/lib/commons-cli-1.2.jar
5.8.0-annona-squamosa/lib/commons-codec-1.10.jar
5.8.0-annona-squamosa/lib/commons-collections-3.2.2.jar
5.8.0-annona-squamosa/lib/commons-csv-1.1.jar
5.8.0-annona-squamosa/lib/commons-fileupload-1.4.jar
5.8.0-annona-squamosa/lib/commons-httpclient-3.1.jar
5.8.0-annona-squamosa/lib/commons-io-2.4.jar
5.8.0-annona-squamosa/lib/commons-lang-2.4.jar
5.8.0-annona-squamosa/lib/commons-lang3-3.4.jar
5.8.0-annona-squamosa/lib/commons-logging-1.1.1.jar
5.8.0-annona-squamosa/lib/cssparser-0.9.5.jar
5.8.0-annona-squamosa/lib/dom4j-1.6.1.jar
5.8.0-annona-squamosa/lib/ezmorph-1.0.5.jar
5.8.0-annona-squamosa/lib/FastInfoset-1.2.16.jar
5.8.0-annona-squamosa/lib/flex-messaging-common-1.0.jar
5.8.0-annona-squamosa/lib/flex-messaging-core-1.0.jar
5.8.0-annona-squamosa/lib/flex-messaging-opt-1.0.jar
5.8.0-annona-squamosa/lib/flex-messaging-proxy-1.0.jar
5.8.0-annona-squamosa/lib/flex-messaging-remoting-1.0.jar
5.8.0-annona-squamosa/lib/forms-1.0.7.jar
5.8.0-annona-squamosa/lib/google-http-client-1.21.0.jar
5.8.0-annona-squamosa/lib/google-oauth-client-1.21.0.jar
5.8.0-annona-squamosa/lib/graphql-java-22.3.jar
5.8.0-annona-squamosa/lib/groovy-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-ant-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-astbuilder-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-cli-picocli-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-console-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-datetime-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-dateutil-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-docgenerator-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-groovydoc-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-groovysh-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-jmx-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-json-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-jsr223-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-macro-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-nio-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-servlet-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-sql-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-swing-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-templates-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-test-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-test-junit5-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-testng-3.0.19.jar
5.8.0-annona-squamosa/lib/groovy-xml-3.0.19.jar
5.8.0-annona-squamosa/lib/guava-14.0.jar
5.8.0-annona-squamosa/lib/hamcrest-core-1.3.jar
5.8.0-annona-squamosa/lib/hermes-1.14.jar
5.8.0-annona-squamosa/lib/hk2-api-2.6.1.jar
5.8.0-annona-squamosa/lib/hk2-locator-2.6.1.jar
5.8.0-annona-squamosa/lib/hk2-utils-2.6.1.jar
5.8.0-annona-squamosa/lib/htmlunit-2.7.jar
5.8.0-annona-squamosa/lib/htmlunit-core-js-2.7.jar
5.8.0-annona-squamosa/lib/httpclient-4.5.5.jar
5.8.0-annona-squamosa/lib/httpclient-cache-4.5.5.jar
5.8.0-annona-squamosa/lib/httpcore-4.4.9.jar
5.8.0-annona-squamosa/lib/httpcore-nio-4.4.9.jar
5.8.0-annona-squamosa/lib/httpmime-4.5.5.jar
5.8.0-annona-squamosa/lib/i4jruntime-5.1.14.jar
5.8.0-annona-squamosa/lib/istack-commons-runtime-3.0.8.jar
5.8.0-annona-squamosa/lib/jackson-annotations-2.13.0.jar
5.8.0-annona-squamosa/lib/jackson-core-2.13.0.jar
5.8.0-annona-squamosa/lib/jackson-coreutils-1.8.jar
5.8.0-annona-squamosa/lib/jackson-databind-2.13.0.jar
5.8.0-annona-squamosa/lib/jackson-dataformat-xml-2.10.1.jar
5.8.0-annona-squamosa/lib/jackson-dataformat-yaml-2.11.1.jar
5.8.0-annona-squamosa/lib/jackson-datatype-joda-2.10.1.jar
5.8.0-annona-squamosa/lib/jackson-jaxrs-base-2.10.1.jar
5.8.0-annona-squamosa/lib/jackson-jaxrs-json-provider-2.10.1.jar
5.8.0-annona-squamosa/lib/jackson-jaxrs-xml-provider-2.10.1.jar
5.8.0-annona-squamosa/lib/jackson-module-jaxb-annotations-2.10.1.jar
5.8.0-annona-squamosa/lib/jakarta.activation-1.2.1.jar
5.8.0-annona-squamosa/lib/jakarta.activation-api-1.2.1.jar
5.8.0-annona-squamosa/lib/jakarta.annotation-api-1.3.5.jar
5.8.0-annona-squamosa/lib/jakarta.inject-2.6.1.jar
5.8.0-annona-squamosa/lib/jakarta.validation-api-2.0.2.jar
5.8.0-annona-squamosa/lib/jakarta.ws.rs-api-2.1.6.jar
5.8.0-annona-squamosa/lib/jakarta.xml.bind-api-2.3.2.jar
5.8.0-annona-squamosa/lib/java-dataloader-3.3.0.jar
5.8.0-annona-squamosa/lib/javafx-base-17.0.12.jar
5.8.0-annona-squamosa/lib/javafx-base-17.0.12-linux.jar
5.8.0-annona-squamosa/lib/javafx-controls-17.0.12.jar
5.8.0-annona-squamosa/lib/javafx-controls-17.0.12-linux.jar
5.8.0-annona-squamosa/lib/javafx-graphics-17.0.12.jar
5.8.0-annona-squamosa/lib/javafx-graphics-17.0.12-linux.jar
5.8.0-annona-squamosa/lib/javafx-media-17.0.12.jar
5.8.0-annona-squamosa/lib/javafx-media-17.0.12-linux.jar
5.8.0-annona-squamosa/lib/javafx-swing-17.0.12-linux.jar
5.8.0-annona-squamosa/lib/javafx-web-17.0.12-linux.jar
5.8.0-annona-squamosa/lib/javaparser-core-3.25.4.jar
5.8.0-annona-squamosa/lib/javassist-3.16.1-GA.jar
5.8.0-annona-squamosa/lib/jaxb-runtime-2.3.2.jar
5.8.0-annona-squamosa/lib/jaxen-1.1-beta-8.jar
5.8.0-annona-squamosa/lib/jcifs-1.2.9.jar
5.8.0-annona-squamosa/lib/jcommander-1.78.jar
5.8.0-annona-squamosa/lib/jdom-1.0.jar
5.8.0-annona-squamosa/lib/jersey-client-2.29.1.jar
5.8.0-annona-squamosa/lib/jersey-common-2.29.1.jar
5.8.0-annona-squamosa/lib/jersey-container-servlet-core-2.29.1.jar
5.8.0-annona-squamosa/lib/jersey-hk2-2.29.1.jar
5.8.0-annona-squamosa/lib/jersey-media-jaxb-2.29.1.jar
5.8.0-annona-squamosa/lib/jersey-media-multipart-2.29.1.jar
5.8.0-annona-squamosa/lib/jersey-server-2.29.1.jar
5.8.0-annona-squamosa/lib/jettison-1.2.jar
5.8.0-annona-squamosa/lib/jetty-6.1.26.jar
5.8.0-annona-squamosa/lib/jetty-util-6.1.26.jar
5.8.0-annona-squamosa/lib/jline-2.14.6.jar
5.8.0-annona-squamosa/lib/jms-1.1.jar
5.8.0-annona-squamosa/lib/joda-time-2.9.9.jar
5.8.0-annona-squamosa/lib/jopt-simple-5.0.3.jar
5.8.0-annona-squamosa/lib/jquery-3.5.1.jar
5.8.0-annona-squamosa/lib/js-1.7R2.jar
5.8.0-annona-squamosa/lib/json-20090211.jar
5.8.0-annona-squamosa/lib/jsonassert-1.5.0.jar
5.8.0-annona-squamosa/lib/json-lib-2.2.2-jdk15.jar
5.8.0-annona-squamosa/lib/json-path-2.4.0-fixed.jar
5.8.0-annona-squamosa/lib/json-schema-core-1.2.8.jar
5.8.0-annona-squamosa/lib/json-schema-validator-2.2.8.jar
5.8.0-annona-squamosa/lib/json-smart-2.3.jar
5.8.0-annona-squamosa/lib/jsr173_api-1.0.jar
5.8.0-annona-squamosa/lib/jsr305-1.3.9.jar
5.8.0-annona-squamosa/lib/jtidy-r872-jdk15.jar
5.8.0-annona-squamosa/lib/junit-4.13.1.jar
5.8.0-annona-squamosa/lib/junit-jupiter-api-5.9.2.jar
5.8.0-annona-squamosa/lib/junit-jupiter-engine-5.9.2.jar
5.8.0-annona-squamosa/lib/junit-platform-commons-1.9.2.jar
5.8.0-annona-squamosa/lib/junit-platform-engine-1.9.2.jar
5.8.0-annona-squamosa/lib/junit-platform-launcher-1.9.2.jar
5.8.0-annona-squamosa/lib/l2fprod-common-directorychooser-7.3.jar
5.8.0-annona-squamosa/lib/l2fprod-common-fontchooser-7.3.jar
5.8.0-annona-squamosa/lib/libphonenumber-8.0.0.jar
5.8.0-annona-squamosa/lib/log4j-api-2.17.1.jar
5.8.0-annona-squamosa/lib/log4j-core-2.17.1.jar
5.8.0-annona-squamosa/lib/log4j-slf4j-impl-2.17.1.jar
5.8.0-annona-squamosa/lib/looks-2.2.0.jar
5.8.0-annona-squamosa/lib/mail-1.4.jar
5.8.0-annona-squamosa/lib/mailapi-1.4.3.jar
5.8.0-annona-squamosa/lib/maven-plugin-api-2.0.jar
5.8.0-annona-squamosa/lib/miglayout-core-11.0.jar
5.8.0-annona-squamosa/lib/miglayout-swing-11.0.jar
5.8.0-annona-squamosa/lib/mimepull-1.9.11.jar
5.8.0-annona-squamosa/lib/msg-simple-1.1.jar
5.8.0-annona-squamosa/lib/nekohtml-1.9.14.jar
5.8.0-annona-squamosa/lib/not-going-to-be-commons-ssl-0.3.20.jar
5.8.0-annona-squamosa/lib/opensaml-2.5.1-1.jar
5.8.0-annona-squamosa/lib/opentest4j-1.2.0.jar
5.8.0-annona-squamosa/lib/openws-1.4.2-1.jar
5.8.0-annona-squamosa/lib/org.apache.oltu.oauth2.client-0.31.jar
5.8.0-annona-squamosa/lib/org.apache.oltu.oauth2.common-0.31.jar
5.8.0-annona-squamosa/lib/org.apache.oltu.oauth2.httpclient4-0.31.jar
5.8.0-annona-squamosa/lib/osgi-resource-locator-1.0.3.jar
5.8.0-annona-squamosa/lib/picocli-4.6.3.jar
5.8.0-annona-squamosa/lib/proxy-vole-20131209.jar
5.8.0-annona-squamosa/lib/qdox-1.12.1.jar
5.8.0-annona-squamosa/lib/reactive-streams-1.0.3.jar
5.8.0-annona-squamosa/lib/reflections-0.9.9-RC1.jar
5.8.0-annona-squamosa/lib/rhino-1.7R4.jar
5.8.0-annona-squamosa/lib/rsyntaxtextarea-2.5.0.jar
5.8.0-annona-squamosa/lib/sac-1.3.jar
5.8.0-annona-squamosa/lib/saxon-9.1.0.8j.jar
5.8.0-annona-squamosa/lib/saxon-9.jar
5.8.0-annona-squamosa/lib/saxon-dom-9.1.0.8j.jar
5.8.0-annona-squamosa/lib/serializer-2.7.2.jar
5.8.0-annona-squamosa/lib/servlet-api-2.5-20081211.jar
5.8.0-annona-squamosa/lib/slf4j-api-1.7.25.jar
5.8.0-annona-squamosa/lib/slf4j-ext-1.7.22.jar
5.8.0-annona-squamosa/lib/snakeyaml-1.30.jar
5.8.0-annona-squamosa/lib/stax2-api-3.1.4.jar
5.8.0-annona-squamosa/lib/stax-ex-1.8.1.jar
5.8.0-annona-squamosa/lib/swagger-annotations-1.6.2.jar
5.8.0-annona-squamosa/lib/swagger-core-1.6.2.jar
5.8.0-annona-squamosa/lib/swagger-inflector-1.0.19.jar
5.8.0-annona-squamosa/lib/swagger-jaxrs-1.6.0.jar
5.8.0-annona-squamosa/lib/swagger-jersey2-jaxrs-1.6.0.jar
5.8.0-annona-squamosa/lib/swagger-models-1.6.2.jar
5.8.0-annona-squamosa/lib/swagger-parser-1.0.54.jar
5.8.0-annona-squamosa/lib/swingx-soapui.jar
5.8.0-annona-squamosa/lib/testng-7.5.jar
5.8.0-annona-squamosa/lib/txw2-2.3.2.jar
5.8.0-annona-squamosa/lib/uri-template-0.9.jar
5.8.0-annona-squamosa/lib/woodstox-core-5.0.3.jar
5.8.0-annona-squamosa/lib/ws-commons-util-1.0.2.jar
5.8.0-annona-squamosa/lib/wsdl4j-1.6.2-fixed.jar
5.8.0-annona-squamosa/lib/wss4j-1.6.17.jar
5.8.0-annona-squamosa/lib/xalan-2.7.2.jar
5.8.0-annona-squamosa/lib/xercesImpl-2.12.0.jar
5.8.0-annona-squamosa/lib/xml-apis-1.4.01.jar
5.8.0-annona-squamosa/lib/xml-apis-2.9.1.jar
5.8.0-annona-squamosa/lib/xmlbeans-3.1.1-sb-fixed.jar
5.8.0-annona-squamosa/lib/xmlbeans-xpath-2.6.0.jar
5.8.0-annona-squamosa/lib/xmlParserAPIs-2.6.2.jar
5.8.0-annona-squamosa/lib/xmlpull-1.1.3.1.jar
5.8.0-annona-squamosa/lib/xmlsec-2.1.7.jar
5.8.0-annona-squamosa/lib/xmltooling-1.3.2-1.jar
5.8.0-annona-squamosa/lib/xmlunit-1.2.jar
5.8.0-annona-squamosa/lib/xom-1.1.jar
5.8.0-annona-squamosa/lib/xpp3_min-1.1.4c.jar
5.8.0-annona-squamosa/lib/xstream-1.4.13.jar
```




---

