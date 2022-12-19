# Getting Started

### Spring and angular app as a single bundle

* Following this article - https://karthi-net.medium.com/how-to-deploy-angular-6-spring-boot-app-as-single-deployment-unit-a0a122860ce8
<br><br>
* Put the angular app in the same parent folder as spring boot app
<br><br>
* run this command to generate static files in the angular app's folder CMD<br><br>
`ng build --configuration production --aot`

<br>

* Add this plugin in your spring boot app
```xml
            <plugin>
                <artifactId>maven-resources-plugin</artifactId>
                <executions> <execution>
                    <id>copy-resources</id>
                    <phase>validate</phase>
                    <goals><goal>copy-resources</goal></goals>
                    <configuration>
                        <outputDirectory>${project.build.directory}/classes/static/</outputDirectory >
                        <resources>
                            <resource>
                                <directory>../myapp/dist/myapp</directory>
                            </resource>
                        </resources>
                    </configuration>
                </execution>
                </executions>
            </plugin>
```

<br><br>

* run ``` mvn clean package install``` in your spring boot app

<br>
 - your app should be available at localhost:8080
<br>
<br>
<br>

* Follow this article for a better setup - https://marco.dev/deploy-java-angular-one

