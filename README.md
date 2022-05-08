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
Apache Maven 3.8.5 (3599d3414f046de2324203b78ddcf9b5e4388aa0)
Maven home: /home/developer/lib/maven-3
Java version: 17.0.3, vendor: Eclipse Adoptium, runtime: /home/developer/lib/jdk-17.0.3+7
Default locale: en_US, platform encoding: UTF-8
OS name: "linux", version: "5.16.0-0.bpo.4-amd64", arch: "amd64", family: "unix"

developer@computer:~/workspace/com_github_kimholan_soapui$ java --version
openjdk 17.0.3 2022-04-19
OpenJDK Runtime Environment Temurin-17.0.3+7 (build 17.0.3+7)
OpenJDK 64-Bit Server VM Temurin-17.0.3+7 (build 17.0.3+7, mixed mode, sharing)
```

Build log:
```
developer@computer:~/workspace/com_github_kimholan_soapui$ mvn clean install -P 'assembly' -DskipTests
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
[INFO] Building SoapUI project 5.7.1-mangosteen                           [1/4]
[INFO] --------------------------------[ pom ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:3.1.0:clean (default-clean) @ soapui-project ---
[INFO] Deleting /home/developer/workspace/com_github_kimholan_soapui (includes = [*.log], excludes = [])
[INFO] 
[INFO] --- maven-install-plugin:2.4:install (default-install) @ soapui-project ---
[INFO] Installing /home/developer/workspace/com_github_kimholan_soapui/pom.xml to /home/developer/.m2/repository/com/smartbear/soapui/soapui-project/5.7.1-mangosteen/soapui-project-5.7.1-mangosteen.pom
[INFO] 
[INFO] --------------------< com.smartbear.soapui:soapui >---------------------
[INFO] Building SoapUI 5.7.1-mangosteen                                   [2/4]
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:3.1.0:clean (default-clean) @ soapui ---
[INFO] Deleting /home/developer/workspace/com_github_kimholan_soapui/soapui/target
[INFO] Deleting /home/developer/workspace/com_github_kimholan_soapui/soapui (includes = [*.log], excludes = [])
[INFO] 
[INFO] --- xmlbeans-maven-plugin:2.3.5-sb-fixed:xmlbeans (default) @ soapui ---
[INFO] 
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ soapui ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] Copying 438 resources
[INFO] Copying 5419 resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.8.1:compile (default-compile) @ soapui ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 3382 source files to /home/developer/workspace/com_github_kimholan_soapui/soapui/target/classes
[INFO] /home/developer/workspace/com_github_kimholan_soapui/soapui/src/main/java/org/apache/http/localserver/ServerTestBase.java: Some input files use or override a deprecated API.
[INFO] /home/developer/workspace/com_github_kimholan_soapui/soapui/src/main/java/org/apache/http/localserver/ServerTestBase.java: Recompile with -Xlint:deprecation for details.
[INFO] /home/developer/workspace/com_github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/tools/SoapUITestCaseRunner.java: Some input files use or override a deprecated API that is marked for removal.
[INFO] /home/developer/workspace/com_github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/tools/SoapUITestCaseRunner.java: Recompile with -Xlint:removal for details.
[INFO] /home/developer/workspace/com_github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/support/AbstractMockService.java: Some input files use unchecked or unsafe operations.
[INFO] /home/developer/workspace/com_github_kimholan_soapui/soapui/src/main/java/com/eviware/soapui/impl/support/AbstractMockService.java: Recompile with -Xlint:unchecked for details.
[INFO] 
[INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ soapui ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] Copying 56 resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.8.1:testCompile (default-testCompile) @ soapui ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 143 source files to /home/developer/workspace/com_github_kimholan_soapui/soapui/target/test-classes
[INFO] /home/developer/workspace/com_github_kimholan_soapui/soapui/src/test/java/com/eviware/soapui/utils/StubbedDialogs.java: Some input files use or override a deprecated API.
[INFO] /home/developer/workspace/com_github_kimholan_soapui/soapui/src/test/java/com/eviware/soapui/utils/StubbedDialogs.java: Recompile with -Xlint:deprecation for details.
[INFO] /home/developer/workspace/com_github_kimholan_soapui/soapui/src/test/java/com/eviware/soapui/support/ModelItemNamerTest.java: Some input files use unchecked or unsafe operations.
[INFO] /home/developer/workspace/com_github_kimholan_soapui/soapui/src/test/java/com/eviware/soapui/support/ModelItemNamerTest.java: Recompile with -Xlint:unchecked for details.
[INFO] 
[INFO] --- maven-surefire-plugin:3.0.0-M3:test (default-test) @ soapui ---
[INFO] Tests are skipped.
[INFO] 
[INFO] --- maven-jar-plugin:3.1.2:jar (default-jar) @ soapui ---
[INFO] Building jar: /home/developer/workspace/com_github_kimholan_soapui/soapui/target/soapui-5.7.1-mangosteen.jar
[INFO] 
[INFO] --- maven-jar-plugin:3.1.2:test-jar (default) @ soapui ---
[INFO] Building jar: /home/developer/workspace/com_github_kimholan_soapui/soapui/target/soapui-5.7.1-mangosteen-tests.jar
[INFO] 
[INFO] --- maven-install-plugin:2.4:install (default-install) @ soapui ---
[INFO] Installing /home/developer/workspace/com_github_kimholan_soapui/soapui/target/soapui-5.7.1-mangosteen.jar to /home/developer/.m2/repository/com/smartbear/soapui/soapui/5.7.1-mangosteen/soapui-5.7.1-mangosteen.jar
[INFO] Installing /home/developer/workspace/com_github_kimholan_soapui/soapui/pom.xml to /home/developer/.m2/repository/com/smartbear/soapui/soapui/5.7.1-mangosteen/soapui-5.7.1-mangosteen.pom
[INFO] Installing /home/developer/workspace/com_github_kimholan_soapui/soapui/target/soapui-5.7.1-mangosteen-tests.jar to /home/developer/.m2/repository/com/smartbear/soapui/soapui/5.7.1-mangosteen/soapui-5.7.1-mangosteen-tests.jar
[INFO] 
[INFO] ---------------< com.smartbear.soapui:soapui-installer >----------------
[INFO] Building SoapUI installer 5.7.1-mangosteen                         [3/4]
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:3.1.0:clean (default-clean) @ soapui-installer ---
[INFO] Deleting /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/target
[INFO] Deleting /home/developer/workspace/com_github_kimholan_soapui/soapui-installer (includes = [*.log], excludes = [])
[INFO] 
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ soapui-installer ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] Copying 2 resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.8.1:compile (default-compile) @ soapui-installer ---
[INFO] No sources to compile
[INFO] 
[INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ soapui-installer ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/src/test/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.8.1:testCompile (default-testCompile) @ soapui-installer ---
[INFO] No sources to compile
[INFO] 
[INFO] --- maven-surefire-plugin:2.12.4:test (default-test) @ soapui-installer ---
[INFO] Tests are skipped.
[INFO] 
[INFO] --- exec-maven-plugin:1.6.0:java (default) @ soapui-installer ---
[INFO] 
[INFO] --- maven-jar-plugin:2.4:jar (default-jar) @ soapui-installer ---
[INFO] Building jar: /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/target/soapui-installer-5.7.1-mangosteen.jar
[INFO] 
[INFO] --- maven-assembly-plugin:3.1.1:single (default) @ soapui-installer ---
[INFO] Reading assembly descriptor: src/main/assembly/dist.xml
[INFO] Reading assembly descriptor: src/main/assembly/dist-standalone.xml
[INFO] Reading assembly descriptor: src/main/assembly/windows-bin.xml
[INFO] Reading assembly descriptor: src/main/assembly/linux-bin.xml
[INFO] Reading assembly descriptor: src/main/assembly/mac-bin.xml
[WARNING] The assembly descriptor contains a filesystem-root relative reference, which is not cross platform compatible /
[WARNING] The assembly descriptor contains a filesystem-root relative reference, which is not cross platform compatible /
[WARNING] Failed to build parent project for org.openjfx:javafx-base:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-base:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-base:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-controls:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-graphics:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-controls:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-controls:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-graphics:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-base:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-graphics:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-graphics:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-media:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-media:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-media:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-web:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-controls:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-media:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-web:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-web:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-swing:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-swing:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-swing:jar:17
Downloading from netbeans: http://bits.netbeans.org/nexus/content/groups/netbeans/org/apache/xerces/xml-apis/2.9.1/xml-apis-2.9.1.pom
Downloading from netbeans: http://bits.netbeans.org/nexus/content/groups/netbeans/com/btr/proxy-vole/20131209/proxy-vole-20131209.pom
Downloading from netbeans: http://bits.netbeans.org/nexus/content/groups/netbeans/com/jayway/jsonpath/json-path/2.4.0-fixed/json-path-2.4.0-fixed.pom
Downloading from netbeans: http://bits.netbeans.org/nexus/content/groups/netbeans/org/sonatype/install4j/i4jruntime/5.1.14/i4jruntime-5.1.14.pom
[INFO] Copying files to /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.7.1-mangosteen-dist
[WARNING] Assembly file: /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.7.1-mangosteen-dist is not a regular file (it may be a directory). It cannot be attached to the project build for installation or deployment.
[WARNING] The assembly descriptor contains a filesystem-root relative reference, which is not cross platform compatible /
[WARNING] The assembly descriptor contains a filesystem-root relative reference, which is not cross platform compatible /
[WARNING] Failed to build parent project for org.openjfx:javafx-base:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-base:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-base:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-controls:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-graphics:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-controls:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-controls:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-graphics:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-base:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-graphics:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-graphics:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-media:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-media:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-media:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-web:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-controls:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-media:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-web:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-web:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-swing:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-swing:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-swing:jar:17
[INFO] Copying files to /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.7.1-mangosteen-dist-standalone
[WARNING] Assembly file: /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.7.1-mangosteen-dist-standalone is not a regular file (it may be a directory). It cannot be attached to the project build for installation or deployment.
[WARNING] The assembly descriptor contains a filesystem-root relative reference, which is not cross platform compatible /
[WARNING] The assembly descriptor contains a filesystem-root relative reference, which is not cross platform compatible /
[WARNING] Failed to build parent project for org.openjfx:javafx-base:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-controls:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-graphics:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-graphics:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-base:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-media:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-web:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-controls:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-media:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-swing:jar:17
[INFO] Building zip: /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.7.1-mangosteen-windows-bin.zip
[WARNING] The assembly descriptor contains a filesystem-root relative reference, which is not cross platform compatible /
[WARNING] The assembly descriptor contains a filesystem-root relative reference, which is not cross platform compatible /
[WARNING] Failed to build parent project for org.openjfx:javafx-base:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-graphics:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-controls:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-base:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-graphics:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-media:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-controls:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-media:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-web:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-swing:jar:17
[INFO] Building tar: /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.7.1-mangosteen-linux-bin.tar.gz
[WARNING] The assembly descriptor contains a filesystem-root relative reference, which is not cross platform compatible /
[WARNING] The assembly descriptor contains a filesystem-root relative reference, which is not cross platform compatible /
[WARNING] Failed to build parent project for org.openjfx:javafx-base:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-graphics:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-controls:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-base:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-graphics:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-media:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-controls:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-media:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-web:jar:17
[WARNING] Failed to build parent project for org.openjfx:javafx-swing:jar:17
[INFO] Building zip: /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.7.1-mangosteen-mac-bin.zip
[INFO] 
[INFO] --- maven-install-plugin:2.4:install (default-install) @ soapui-installer ---
[INFO] Installing /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/target/soapui-installer-5.7.1-mangosteen.jar to /home/developer/.m2/repository/com/smartbear/soapui/soapui-installer/5.7.1-mangosteen/soapui-installer-5.7.1-mangosteen.jar
[INFO] Installing /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/pom.xml to /home/developer/.m2/repository/com/smartbear/soapui/soapui-installer/5.7.1-mangosteen/soapui-installer-5.7.1-mangosteen.pom
[INFO] Installing /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.7.1-mangosteen-windows-bin.zip to /home/developer/.m2/repository/com/smartbear/soapui/soapui-installer/5.7.1-mangosteen/soapui-installer-5.7.1-mangosteen-windows-bin.zip
[INFO] Installing /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.7.1-mangosteen-linux-bin.tar.gz to /home/developer/.m2/repository/com/smartbear/soapui/soapui-installer/5.7.1-mangosteen/soapui-installer-5.7.1-mangosteen-linux-bin.tar.gz
[INFO] Installing /home/developer/workspace/com_github_kimholan_soapui/soapui-installer/target/assemblies/SoapUI-5.7.1-mangosteen-mac-bin.zip to /home/developer/.m2/repository/com/smartbear/soapui/soapui-installer/5.7.1-mangosteen/soapui-installer-5.7.1-mangosteen-mac-bin.zip
[INFO] 
[INFO] --------------< com.smartbear.soapui:soapui-system-test >---------------
[INFO] Building SoapUI system test 5.7.1-mangosteen                       [4/4]
[INFO] --------------------------------[ jar ]---------------------------------
[INFO] 
[INFO] --- maven-clean-plugin:3.1.0:clean (default-clean) @ soapui-system-test ---
[INFO] Deleting /home/developer/workspace/com_github_kimholan_soapui/soapui-system-test/target
[INFO] Deleting /home/developer/workspace/com_github_kimholan_soapui/soapui-system-test (includes = [*.log], excludes = [])
[INFO] 
[INFO] --- maven-resources-plugin:2.6:resources (default-resources) @ soapui-system-test ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] skip non existing resourceDirectory /home/developer/workspace/com_github_kimholan_soapui/soapui-system-test/src/main/resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.8.1:compile (default-compile) @ soapui-system-test ---
[INFO] No sources to compile
[INFO] 
[INFO] --- maven-resources-plugin:2.6:testResources (default-testResources) @ soapui-system-test ---
[INFO] Using 'UTF-8' encoding to copy filtered resources.
[INFO] Copying 81 resources
[INFO] 
[INFO] --- maven-compiler-plugin:3.8.1:testCompile (default-testCompile) @ soapui-system-test ---
[INFO] Changes detected - recompiling the module!
[INFO] Compiling 26 source files to /home/developer/workspace/com_github_kimholan_soapui/soapui-system-test/target/test-classes
[INFO] /home/developer/workspace/com_github_kimholan_soapui/soapui-system-test/src/test/java/com/smartbear/soapui/other/rest/oauth2/AddParamActionTest.java: Some input files use or override a deprecated API.
[INFO] /home/developer/workspace/com_github_kimholan_soapui/soapui-system-test/src/test/java/com/smartbear/soapui/other/rest/oauth2/AddParamActionTest.java: Recompile with -Xlint:deprecation for details.
[INFO] 
[INFO] --- maven-surefire-plugin:3.0.0-M3:test (default-test) @ soapui-system-test ---
[INFO] Tests are skipped.
[INFO] 
[INFO] --- maven-jar-plugin:3.1.2:jar (default-jar) @ soapui-system-test ---
[WARNING] JAR will be empty - no content was marked for inclusion!
[INFO] Building jar: /home/developer/workspace/com_github_kimholan_soapui/soapui-system-test/target/soapui-system-test-5.7.1-mangosteen.jar
[INFO] 
[INFO] --- maven-jar-plugin:3.1.2:test-jar (default) @ soapui-system-test ---
[INFO] Building jar: /home/developer/workspace/com_github_kimholan_soapui/soapui-system-test/target/soapui-system-test-5.7.1-mangosteen-tests.jar
[INFO] 
[INFO] --- maven-install-plugin:2.4:install (default-install) @ soapui-system-test ---
[INFO] Installing /home/developer/workspace/com_github_kimholan_soapui/soapui-system-test/target/soapui-system-test-5.7.1-mangosteen.jar to /home/developer/.m2/repository/com/smartbear/soapui/soapui-system-test/5.7.1-mangosteen/soapui-system-test-5.7.1-mangosteen.jar
[INFO] Installing /home/developer/workspace/com_github_kimholan_soapui/soapui-system-test/pom.xml to /home/developer/.m2/repository/com/smartbear/soapui/soapui-system-test/5.7.1-mangosteen/soapui-system-test-5.7.1-mangosteen.pom
[INFO] Installing /home/developer/workspace/com_github_kimholan_soapui/soapui-system-test/target/soapui-system-test-5.7.1-mangosteen-tests.jar to /home/developer/.m2/repository/com/smartbear/soapui/soapui-system-test/5.7.1-mangosteen/soapui-system-test-5.7.1-mangosteen-tests.jar
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for SoapUI project 5.7.1-mangosteen:
[INFO] 
[INFO] SoapUI project ..................................... SUCCESS [  0.116 s]
[INFO] SoapUI ............................................. SUCCESS [ 21.654 s]
[INFO] SoapUI installer ................................... SUCCESS [ 10.690 s]
[INFO] SoapUI system test ................................. SUCCESS [  0.274 s]
[INFO] ------------------------------------------------------------------------
[INFO] BUILD SUCCESS
[INFO] ------------------------------------------------------------------------
[INFO] Total time:  32.781 s
[INFO] Finished at: 2022-05-08T09:22:51+02:00
[INFO] ------------------------------------------------------------------------

```

Assembly contents
=================

The assembly built contains the following JARS:

```
developer@computer:~/workspace/com_github_kimholan_soapui$ tar tvf ./soapui-installer/target/assemblies/SoapUI-5.7.1-mangosteen-linux-bin.tar.gz  |grep jar | sed -e 's|^.* SoapUI-||' |  sort 
5.7.1-mangosteen/bin/soapui-5.7.1-mangosteen.jar
5.7.1-mangosteen/lib/accessors-smart-1.2.jar
5.7.1-mangosteen/lib/activation-1.1.jar
5.7.1-mangosteen/lib/android-json-0.0.20131108.vaadin1.jar
5.7.1-mangosteen/lib/animal-sniffer-annotations-1.11.jar
5.7.1-mangosteen/lib/ant-1.10.8.jar
5.7.1-mangosteen/lib/ant-antlr-1.10.8.jar
5.7.1-mangosteen/lib/ant-junit-1.10.8.jar
5.7.1-mangosteen/lib/ant-launcher-1.10.8.jar
5.7.1-mangosteen/lib/antlr4-runtime-4.9.2.jar
5.7.1-mangosteen/lib/aopalliance-repackaged-2.6.1.jar
5.7.1-mangosteen/lib/bcmail-jdk15on-1.70.jar
5.7.1-mangosteen/lib/bcpkix-jdk15on-1.70.jar
5.7.1-mangosteen/lib/bcprov-jdk15on-1.70.jar
5.7.1-mangosteen/lib/bcutil-jdk15on-1.70.jar
5.7.1-mangosteen/lib/binding-2.0.1.jar
5.7.1-mangosteen/lib/btf-1.2.jar
5.7.1-mangosteen/lib/cal10n-api-0.8.1.jar
5.7.1-mangosteen/lib/commons-beanutils-1.9.4.jar
5.7.1-mangosteen/lib/commons-cli-1.2.jar
5.7.1-mangosteen/lib/commons-codec-1.10.jar
5.7.1-mangosteen/lib/commons-collections-3.2.2.jar
5.7.1-mangosteen/lib/commons-csv-1.1.jar
5.7.1-mangosteen/lib/commons-fileupload-1.4.jar
5.7.1-mangosteen/lib/commons-httpclient-3.1.jar
5.7.1-mangosteen/lib/commons-io-2.4.jar
5.7.1-mangosteen/lib/commons-lang-2.4.jar
5.7.1-mangosteen/lib/commons-lang3-3.4.jar
5.7.1-mangosteen/lib/commons-logging-1.1.1.jar
5.7.1-mangosteen/lib/cssparser-0.9.5.jar
5.7.1-mangosteen/lib/dom4j-1.6.1.jar
5.7.1-mangosteen/lib/ezmorph-1.0.5.jar
5.7.1-mangosteen/lib/FastInfoset-1.2.16.jar
5.7.1-mangosteen/lib/flex-messaging-common-1.0.jar
5.7.1-mangosteen/lib/flex-messaging-core-1.0.jar
5.7.1-mangosteen/lib/flex-messaging-opt-1.0.jar
5.7.1-mangosteen/lib/flex-messaging-proxy-1.0.jar
5.7.1-mangosteen/lib/flex-messaging-remoting-1.0.jar
5.7.1-mangosteen/lib/forms-1.0.7.jar
5.7.1-mangosteen/lib/google-http-client-1.21.0.jar
5.7.1-mangosteen/lib/google-oauth-client-1.21.0.jar
5.7.1-mangosteen/lib/graphql-java-17.3.jar
5.7.1-mangosteen/lib/groovy-3.0.6.jar
5.7.1-mangosteen/lib/groovy-ant-3.0.6.jar
5.7.1-mangosteen/lib/groovy-astbuilder-3.0.6.jar
5.7.1-mangosteen/lib/groovy-cli-picocli-3.0.6.jar
5.7.1-mangosteen/lib/groovy-console-3.0.6.jar
5.7.1-mangosteen/lib/groovy-datetime-3.0.6.jar
5.7.1-mangosteen/lib/groovy-dateutil-3.0.6.jar
5.7.1-mangosteen/lib/groovy-docgenerator-3.0.6.jar
5.7.1-mangosteen/lib/groovy-groovydoc-3.0.6.jar
5.7.1-mangosteen/lib/groovy-groovysh-3.0.6.jar
5.7.1-mangosteen/lib/groovy-jmx-3.0.6.jar
5.7.1-mangosteen/lib/groovy-json-3.0.6.jar
5.7.1-mangosteen/lib/groovy-jsr223-3.0.6.jar
5.7.1-mangosteen/lib/groovy-macro-3.0.6.jar
5.7.1-mangosteen/lib/groovy-nio-3.0.6.jar
5.7.1-mangosteen/lib/groovy-servlet-3.0.6.jar
5.7.1-mangosteen/lib/groovy-sql-3.0.6.jar
5.7.1-mangosteen/lib/groovy-swing-3.0.6.jar
5.7.1-mangosteen/lib/groovy-templates-3.0.6.jar
5.7.1-mangosteen/lib/groovy-test-3.0.6.jar
5.7.1-mangosteen/lib/groovy-test-junit5-3.0.6.jar
5.7.1-mangosteen/lib/groovy-testng-3.0.6.jar
5.7.1-mangosteen/lib/groovy-xml-3.0.6.jar
5.7.1-mangosteen/lib/guava-14.0.jar
5.7.1-mangosteen/lib/hamcrest-core-1.3.jar
5.7.1-mangosteen/lib/hermes-1.14.jar
5.7.1-mangosteen/lib/hk2-api-2.6.1.jar
5.7.1-mangosteen/lib/hk2-locator-2.6.1.jar
5.7.1-mangosteen/lib/hk2-utils-2.6.1.jar
5.7.1-mangosteen/lib/htmlunit-2.7.jar
5.7.1-mangosteen/lib/htmlunit-core-js-2.7.jar
5.7.1-mangosteen/lib/httpclient-4.5.5.jar
5.7.1-mangosteen/lib/httpclient-cache-4.5.5.jar
5.7.1-mangosteen/lib/httpcore-4.4.9.jar
5.7.1-mangosteen/lib/httpcore-nio-4.4.9.jar
5.7.1-mangosteen/lib/httpmime-4.5.5.jar
5.7.1-mangosteen/lib/i4jruntime-5.1.14.jar
5.7.1-mangosteen/lib/istack-commons-runtime-3.0.8.jar
5.7.1-mangosteen/lib/jackson-annotations-2.13.0.jar
5.7.1-mangosteen/lib/jackson-core-2.13.0.jar
5.7.1-mangosteen/lib/jackson-coreutils-1.8.jar
5.7.1-mangosteen/lib/jackson-databind-2.13.0.jar
5.7.1-mangosteen/lib/jackson-dataformat-xml-2.10.1.jar
5.7.1-mangosteen/lib/jackson-dataformat-yaml-2.11.1.jar
5.7.1-mangosteen/lib/jackson-datatype-joda-2.10.1.jar
5.7.1-mangosteen/lib/jackson-jaxrs-base-2.10.1.jar
5.7.1-mangosteen/lib/jackson-jaxrs-json-provider-2.10.1.jar
5.7.1-mangosteen/lib/jackson-jaxrs-xml-provider-2.10.1.jar
5.7.1-mangosteen/lib/jackson-module-jaxb-annotations-2.10.1.jar
5.7.1-mangosteen/lib/jakarta.activation-1.2.1.jar
5.7.1-mangosteen/lib/jakarta.activation-api-1.2.1.jar
5.7.1-mangosteen/lib/jakarta.annotation-api-1.3.5.jar
5.7.1-mangosteen/lib/jakarta.inject-2.6.1.jar
5.7.1-mangosteen/lib/jakarta.validation-api-2.0.2.jar
5.7.1-mangosteen/lib/jakarta.ws.rs-api-2.1.6.jar
5.7.1-mangosteen/lib/jakarta.xml.bind-api-2.3.2.jar
5.7.1-mangosteen/lib/java-dataloader-3.1.0.jar
5.7.1-mangosteen/lib/javafx-base-17.jar
5.7.1-mangosteen/lib/javafx-base-17-linux.jar
5.7.1-mangosteen/lib/javafx-controls-17.jar
5.7.1-mangosteen/lib/javafx-controls-17-linux.jar
5.7.1-mangosteen/lib/javafx-graphics-17.jar
5.7.1-mangosteen/lib/javafx-graphics-17-linux.jar
5.7.1-mangosteen/lib/javafx-media-17.jar
5.7.1-mangosteen/lib/javafx-media-17-linux.jar
5.7.1-mangosteen/lib/javafx-swing-17-linux.jar
5.7.1-mangosteen/lib/javafx-web-17-linux.jar
5.7.1-mangosteen/lib/javaparser-core-3.16.1.jar
5.7.1-mangosteen/lib/javassist-3.16.1-GA.jar
5.7.1-mangosteen/lib/jaxb-runtime-2.3.2.jar
5.7.1-mangosteen/lib/jaxen-1.1-beta-8.jar
5.7.1-mangosteen/lib/jcifs-1.2.9.jar
5.7.1-mangosteen/lib/jcommander-1.78.jar
5.7.1-mangosteen/lib/jdom-1.0.jar
5.7.1-mangosteen/lib/jersey-client-2.29.1.jar
5.7.1-mangosteen/lib/jersey-common-2.29.1.jar
5.7.1-mangosteen/lib/jersey-container-servlet-core-2.29.1.jar
5.7.1-mangosteen/lib/jersey-hk2-2.29.1.jar
5.7.1-mangosteen/lib/jersey-media-jaxb-2.29.1.jar
5.7.1-mangosteen/lib/jersey-media-multipart-2.29.1.jar
5.7.1-mangosteen/lib/jersey-server-2.29.1.jar
5.7.1-mangosteen/lib/jettison-1.2.jar
5.7.1-mangosteen/lib/jetty-6.1.26.jar
5.7.1-mangosteen/lib/jetty-util-6.1.26.jar
5.7.1-mangosteen/lib/jline-2.14.6.jar
5.7.1-mangosteen/lib/jms-1.1.jar
5.7.1-mangosteen/lib/joda-time-2.9.9.jar
5.7.1-mangosteen/lib/jopt-simple-5.0.3.jar
5.7.1-mangosteen/lib/js-1.7R2.jar
5.7.1-mangosteen/lib/json-20090211.jar
5.7.1-mangosteen/lib/jsonassert-1.5.0.jar
5.7.1-mangosteen/lib/json-lib-2.2.2-jdk15.jar
5.7.1-mangosteen/lib/json-path-2.4.0-fixed.jar
5.7.1-mangosteen/lib/json-schema-core-1.2.8.jar
5.7.1-mangosteen/lib/json-schema-validator-2.2.8.jar
5.7.1-mangosteen/lib/json-smart-2.3.jar
5.7.1-mangosteen/lib/jsr173_api-1.0.jar
5.7.1-mangosteen/lib/jsr305-1.3.9.jar
5.7.1-mangosteen/lib/jtidy-r872-jdk15.jar
5.7.1-mangosteen/lib/junit-4.13.1.jar
5.7.1-mangosteen/lib/junit-jupiter-api-5.7.0.jar
5.7.1-mangosteen/lib/junit-jupiter-engine-5.7.0.jar
5.7.1-mangosteen/lib/junit-platform-commons-1.7.0.jar
5.7.1-mangosteen/lib/junit-platform-engine-1.7.0.jar
5.7.1-mangosteen/lib/junit-platform-launcher-1.7.0.jar
5.7.1-mangosteen/lib/l2fprod-common-directorychooser-7.3.jar
5.7.1-mangosteen/lib/l2fprod-common-fontchooser-7.3.jar
5.7.1-mangosteen/lib/libphonenumber-8.0.0.jar
5.7.1-mangosteen/lib/log4j-api-2.17.1.jar
5.7.1-mangosteen/lib/log4j-core-2.17.1.jar
5.7.1-mangosteen/lib/log4j-slf4j-impl-2.17.1.jar
5.7.1-mangosteen/lib/looks-2.2.0.jar
5.7.1-mangosteen/lib/mail-1.4.jar
5.7.1-mangosteen/lib/mailapi-1.4.3.jar
5.7.1-mangosteen/lib/maven-plugin-api-2.0.jar
5.7.1-mangosteen/lib/miglayout-core-11.0.jar
5.7.1-mangosteen/lib/miglayout-swing-11.0.jar
5.7.1-mangosteen/lib/mimepull-1.9.11.jar
5.7.1-mangosteen/lib/msg-simple-1.1.jar
5.7.1-mangosteen/lib/nekohtml-1.9.14.jar
5.7.1-mangosteen/lib/not-going-to-be-commons-ssl-0.3.20.jar
5.7.1-mangosteen/lib/opensaml-2.5.1-1.jar
5.7.1-mangosteen/lib/opentest4j-1.2.0.jar
5.7.1-mangosteen/lib/openws-1.4.2-1.jar
5.7.1-mangosteen/lib/org.apache.oltu.oauth2.client-0.31.jar
5.7.1-mangosteen/lib/org.apache.oltu.oauth2.common-0.31.jar
5.7.1-mangosteen/lib/org.apache.oltu.oauth2.httpclient4-0.31.jar
5.7.1-mangosteen/lib/osgi-resource-locator-1.0.3.jar
5.7.1-mangosteen/lib/picocli-4.5.1.jar
5.7.1-mangosteen/lib/proxy-vole-20131209.jar
5.7.1-mangosteen/lib/qdox-1.12.1.jar
5.7.1-mangosteen/lib/reactive-streams-1.0.2.jar
5.7.1-mangosteen/lib/reflections-0.9.9-RC1.jar
5.7.1-mangosteen/lib/rhino-1.7R4.jar
5.7.1-mangosteen/lib/rsyntaxtextarea-2.5.0.jar
5.7.1-mangosteen/lib/sac-1.3.jar
5.7.1-mangosteen/lib/saxon-9.1.0.8j.jar
5.7.1-mangosteen/lib/saxon-9.jar
5.7.1-mangosteen/lib/saxon-dom-9.1.0.8j.jar
5.7.1-mangosteen/lib/serializer-2.7.2.jar
5.7.1-mangosteen/lib/servlet-api-2.5-20081211.jar
5.7.1-mangosteen/lib/slf4j-api-1.7.25.jar
5.7.1-mangosteen/lib/slf4j-ext-1.7.22.jar
5.7.1-mangosteen/lib/snakeyaml-1.30.jar
5.7.1-mangosteen/lib/stax2-api-3.1.4.jar
5.7.1-mangosteen/lib/stax-ex-1.8.1.jar
5.7.1-mangosteen/lib/swagger-annotations-1.6.2.jar
5.7.1-mangosteen/lib/swagger-core-1.6.2.jar
5.7.1-mangosteen/lib/swagger-inflector-1.0.19.jar
5.7.1-mangosteen/lib/swagger-jaxrs-1.6.0.jar
5.7.1-mangosteen/lib/swagger-jersey2-jaxrs-1.6.0.jar
5.7.1-mangosteen/lib/swagger-models-1.6.2.jar
5.7.1-mangosteen/lib/swagger-parser-1.0.54.jar
5.7.1-mangosteen/lib/swingx-soapui.jar
5.7.1-mangosteen/lib/testng-7.3.0.jar
5.7.1-mangosteen/lib/txw2-2.3.2.jar
5.7.1-mangosteen/lib/uri-template-0.9.jar
5.7.1-mangosteen/lib/woodstox-core-5.0.3.jar
5.7.1-mangosteen/lib/ws-commons-util-1.0.2.jar
5.7.1-mangosteen/lib/wsdl4j-1.6.2-fixed.jar
5.7.1-mangosteen/lib/wss4j-1.6.17.jar
5.7.1-mangosteen/lib/xalan-2.7.2.jar
5.7.1-mangosteen/lib/xercesImpl-2.12.0.jar
5.7.1-mangosteen/lib/xml-apis-1.4.01.jar
5.7.1-mangosteen/lib/xml-apis-2.9.1.jar
5.7.1-mangosteen/lib/xmlbeans-3.1.1-sb-fixed.jar
5.7.1-mangosteen/lib/xmlbeans-xpath-2.6.0.jar
5.7.1-mangosteen/lib/xmlParserAPIs-2.6.2.jar
5.7.1-mangosteen/lib/xmlpull-1.1.3.1.jar
5.7.1-mangosteen/lib/xmlsec-2.1.7.jar
5.7.1-mangosteen/lib/xmltooling-1.3.2-1.jar
5.7.1-mangosteen/lib/xmlunit-1.2.jar
5.7.1-mangosteen/lib/xom-1.1.jar
5.7.1-mangosteen/lib/xpp3_min-1.1.4c.jar
5.7.1-mangosteen/lib/xstream-1.4.13.jar
```




---

