
#Create maven projecty
```sh
mvn -B archetype:generate \
 -DarchetypeGroupId=software.amazon.awssdk \
 -DarchetypeArtifactId=archetype-lambda -Dservice=s3 -Dregion=AP_SOUTHEAST_4 \
 -DarchetypeVersion=2.38.1 \
 -DgroupId=com.example.myapp \
 -DartifactId=myapp
```