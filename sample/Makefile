CAPSTAN_IMAGE_NAME=sample

all: target/lein-skummet-sample-0.0.1-SNAPSHOT-jar-with-dependencies.jar

target/lein-skummet-sample-0.0.1-SNAPSHOT-jar-with-dependencies.jar: target/classes/sample/core.class pom.xml
	mvn assembly:single

target/classes/sample/core.class:
	lein skummet compile

pom.xml:
	lein pom
	patch pom.xml < pom-uberjar.patch

.PHONY: all run clean capstan-build capstan-run capstan-build-vbox capstan-run-vbox

run: target/lein-skummet-sample-0.0.1-SNAPSHOT-jar-with-dependencies.jar
	java -jar ./target/lein-skummet-sample-0.0.1-SNAPSHOT-jar-with-dependencies.jar

clean:
	lein clean
	rm pom.xml

capstan-build:
	capstan build -v ${CAPSTAN_IMAGE_NAME}

capstan-run:
	capstan run ${CAPSTAN_IMAGE_NAME}

capstan-build-vbox:
	capstan build -v -p vbox ${CAPSTAN_IMAGE_NAME}

capstan-run-vbox:
	capstan run -p vbox ${CAPSTAN_IMAGE_NAME}

