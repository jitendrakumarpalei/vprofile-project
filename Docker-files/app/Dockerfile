FROM openjdk:11 AS BUILD_IMAGE 
RUN apt update && apt install maven -y 
RUN git clone https://github.com/jitendrakumarpalei/vprofile-project.git
RUN cd vprofile-project && checkout docker && mvn install

FROM tomcat:9-jre11-temurin-noble
LABEL "project"="vprofile"
LABEL "Author"="Jitu"
RUN --from=BUILD_IMAGE vprofile-project/target/vprofile-v2.war /usr/local/tomcat/webapps/ROOT.war

EXPOSE 8080
CMD ["catalina.sh""run"]

