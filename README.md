<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>revers-api-test</artifactId>
    <version>1.0-SNAPSHOT</version>

    <properties>
        <maven-compiler.version>3.8.1</maven-compiler.version>
        <maven-surefire-plugin.version>3.0.0-M5</maven-surefire-plugin.version>

        <allure-cucumber6-jvm.version>2.13.8</allure-cucumber6-jvm.version>
        <allure-maven.version>2.8</allure-maven.version>
        <!--ОТЧЕТ ALLURE-->
        <allure.version>2.13.8</allure.version>

        <maven.compiler.source>8</maven.compiler.source>
        <maven.compiler.target>8</maven.compiler.target>
    </properties>

    <dependencies>
        <!-- RestAssured 4.0.0 -->
        <dependency>
            <groupId>io.rest-assured</groupId>
            <artifactId>rest-assured</artifactId>
            <version>4.3.3</version>
        </dependency>

        <!-- JUnit 4.12 -->
        <dependency>
            <groupId>junit</groupId>
            <artifactId>junit</artifactId>
            <version>4.12</version>
        </dependency>

        <!--        &lt;!&ndash; Allure JUnit 4 &ndash;&gt;-->
        <dependency>
            <groupId>io.qameta.allure</groupId>
            <artifactId>allure-junit4</artifactId>
            <version>2.13.5</version>
        </dependency>

        <!--        &lt;!&ndash; Allure RestAssured &ndash;&gt;-->
        <dependency>
            <groupId>io.qameta.allure</groupId>
            <artifactId>allure-rest-assured</artifactId>
            <version>2.20.1</version>
        </dependency>
    </dependencies>

    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-compiler-plugin</artifactId>
                <version>${maven-compiler.version}</version>
                <configuration>
                    <encoding>UTF-8</encoding>
                    <source>1.8</source>
                    <target>1.8</target>
                </configuration>
            </plugin>

            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-surefire-plugin</artifactId>
                <version>${maven-surefire-plugin.version}</version>
                <configuration>
                    <rerunFailingTestsCount>2</rerunFailingTestsCount>
                    <perCoreThreadCount>false</perCoreThreadCount>
                    <threadCount>20</threadCount>
                    <parallel>methods</parallel>
                    <testFailureIgnore>true</testFailureIgnore>
                    <argLine>
                        -javaagent:"${settings.localRepository}/org/aspectj/aspectjweaver/1.9.4/aspectjweaver-1.9.4.jar"
                    </argLine>
                    <systemPropertyVariables>
                        <stand>${properties}</stand>
                    </systemPropertyVariables>
                </configuration>

                <dependencies>
                    <dependency>
                        <groupId>org.aspectj</groupId>
                        <artifactId>aspectjweaver</artifactId>
                        <version>1.9.4</version>
                    </dependency>
                </dependencies>
            </plugin>

            <plugin>
                <groupId>io.qameta.allure</groupId>
                <artifactId>allure-maven</artifactId>
                <version>2.10.0</version>
                <configuration>
                    <resultsDirectory>allure-results</resultsDirectory>
                </configuration>
            </plugin>

            <plugin>
                <groupId>ru.sbrf.swats</groupId>
                <artifactId>adaptavist-maven-plugin</artifactId>
                <version>2.7.1</version>
            </plugin>

        </plugins>
    </build>
</project>
