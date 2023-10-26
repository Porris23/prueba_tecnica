Éste archivo contiene las instrucciones necesarias para montar el proyecto:

Instructions for running the login to Guru99 Bank page scenarios
Requirements

Java 11 or higher
Maven
Cucumber
Selenium
ChromeDriver
Installation

Clone this repository:
git clone https://github.com/usuario/login-to-guru99-bank-page-scenarios

Navigate to the project directory:
cd login-to-guru99-bank-page-scenarios

Build the project:
mvn clean install

Running the scenarios
To run the scenarios, execute the following command:

mvn test
This will execute all of the scenarios in the src/test/resources/features directory.

Generating the JSON report
To generate a JSON report of the scenario execution, add the following plugin to the pom.xml file:

XML
<plugin>
    <groupId>io.cucumber</groupId>
    <artifactId>cucumber-testng</artifactId>
    <version>7.9.0</version>
    <executions>
        <execution>
            <id>generate-json-report</id>
            <phase>post-integration-test</phase>
            <goals>
                <goal>generate</goal>
            </goals>
            <configuration>
                <features>${project.basedir}/src/test/resources/features</features>
                <glue>${project.basedir}/src/test/java/com/example/cucumber</glue>
                <tags>@login_access_to_page, @login_check_fields, @login_successful_login, @login_unsuccessful_login, @login_empty_fields, @login_reset_button</tags>
                <plugin>json:target/cucumber-report.json</plugin>
            </configuration>
        </execution>
    </executions>
</plugin>
Utiliza el código con precaución. Más información
Then, execute the following command to build the project and generate the JSON report:

mvn test
The JSON report will be generated in the target/cucumber-report.json file.

Running individual scenarios
To run individual scenarios, you can use the @id tag. For example, to run the login_access_to_page scenario, you would execute the following command:

mvn test -Dcucumber.options="--name login_access_to_page"
You can also run multiple scenarios by passing a comma-separated list of @id tags to the cucumber.options property. For example, to run the login_access_to_page and login_check_fields scenarios, you would execute the following command:

mvn test -Dcucumber.options="--name login_access_to_page,login_check_fields"
