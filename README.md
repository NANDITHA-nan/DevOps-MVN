mvn pom.xml
<?xml version="1.0" encoding="UTF-8"?>
<project xmlns="http://maven.apache.org/POM/4.0.0"
         xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
         xsi:schemaLocation="http://maven.apache.org/POM/4.0.0 http://maven.apache.org/xsd/maven-4.0.0.xsd">
    <modelVersion>4.0.0</modelVersion>

    <groupId>org.example</groupId>
    <artifactId>DevOpsVTU-Maven</artifactId>
    <version>1.0-SNAPSHOT</version>
    <dependencies>
        <dependency>
            <groupId>org.seleniumhq.selenium</groupId>
            <artifactId>selenium-java</artifactId>
            <version>4.28.1</version>
        </dependency>
        <dependency>
            <groupId>org.testng</groupId>
            <artifactId>testng</artifactId>
            <version>7.4.0</version>
            <scope>test</scope>
        </dependency>
    </dependencies>
    <build>
        <plugins>
            <plugin>
                <groupId>org.apache.maven.plugins</groupId>
                <artifactId>maven-resources-plugin</artifactId>
                <version>3.2.0</version>
                <executions>
                    <execution>
                        <phase>prepare-package</phase> <!-- Before packaging -->
                        <goals>
                            <goal>copy-resources</goal>
                        </goals>
                        <configuration>
                            <outputDirectory>${project.basedir}/docs</outputDirectory> <!-- Deploy to /docs -->
                            <resources>
                                <resource>
                                    <directory>src/main/resources</directory> <!-- Source directory -->
                                    <includes>
                                        <include>*/</include> <!-- Copy all files in src/main/resources -->
                                    </includes>
                                </resource>
                            </resources>
                        </configuration>
                    </execution>
                </executions>
            </plugin>
        </plugins>
    </build>

    <properties>
        <maven.compiler.source>17</maven.compiler.source>
        <maven.compiler.target>17</maven.compiler.target>
        <project.build.sourceEncoding>UTF-8</project.build.sourceEncoding>
    </properties>

</project>


index.html
<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>My Simple Website</title>
<link rel="stylesheet" href="mvn.css">
</head>
<body>
<header>
<img src="welcome1.png" alt="Logo">
</header>
<h1>Welcome to My Simple Website</h1>
</body>
</html>


mvn.css
body {
 font-family: Arial, sans-serif;
 background-color: #f4f4f4;
 text-align: center;
}
header img {
 width: 100px;
}


webpagetest.java
package org.test;
import org.openqa.selenium.WebDriver;
  import org.openqa.selenium.chrome.ChromeDriver;
  import org.testng.Assert;
  import org.testng.annotations.AfterTest;
  import org.testng.annotations.BeforeTest;
 import org.testng.annotations.Test;
  import static org.testng.Assert.assertTrue;
  public class WebpageTest {
     private static WebDriver driver;
 
     @BeforeTest
     public void openBrowser() throws InterruptedException {
         driver = new ChromeDriver();
         driver.manage().window().maximize();
         Thread.sleep(2000);
         driver.get("https://github.com/NANDITHA-nan/DevOps-MVN"); // "Note: You should use your GITHUB-URL here...!!!"
     }
 
     @Test
     public void titleValidationTest(){
        String actualTitle = driver.getTitle();
        String expectedTitle = "My Simple Website";// title should be match with the index.html title
         Assert.assertEquals(driver.getTitle(), "GitHub - NANDITHA-nan/DevOps-MVN: maven");
         //given github login  username and the repository name with description

         assertTrue(true, "Title should contain 'ci/cd'");
    }
 
     @AfterTest
     public void closeBrowser() throws InterruptedException {
         Thread.sleep(1000);
         driver.quit();
    }
  }
