# Build instructions for mac (based on .github/workflows/ci.yml):

## Downlod and install Android Studio
https://developer.android.com/studio

Go to Settings->Languages & Frameworks -> Android SDK and intall Android 4.4 (API level 19).

export ANDROID_HOME=~/Library/Android/sdk

## Get an old gradle version:
GRADLE_VERSION=6.7.1
wget https://services.gradle.org/distributions/gradle-${GRADLE_VERSION}-all.zip
unzip gradle-${GRADLE_VERSION}-all.zip

## Install GraphViz
brew install graphviz

## Use java11
brew install openjdk@11
export JAVA_HOME=/opt/homebrew/Cellar/openjdk@11/11.0.26/

## Build and install into a custom maven repository:
./gradle-${GRADLE_VERSION}/bin/gradle check

In case of errors about jxmpp-jid remove ~/.m2/repository/org/jxmpp

./gradle-${GRADLE_VERSION}/bin/gradle publishToMavenLocal -Dmaven.repo.local=~/git/jitsi-maven-repository/snapshots/
