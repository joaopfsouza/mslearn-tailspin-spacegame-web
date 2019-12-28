# SonarCloud

## Variables
```
SONAR_PROJECT_KEY=space-game-web-jax
SONAR_ORGANIZATION=jax
SONAR_LOGIN=8d2502d6c9c4024c5d22707d545dd51822ff5735
```

## Prepare SonarCloud
```
MSYS2_ARG_CONV_EXCL="*" $HOME/.dotnet/tools/dotnet-sonarscanner begin \
  /k:"$SONAR_PROJECT_KEY" \
  /d:sonar.host.url="https://sonarcloud.io" \
  /d:sonar.login="$SONAR_LOGIN" \
  /d:sonar.cs.opencover.reportsPaths="./Tailspin.SpaceGame.Web.Tests/TestResults/Coverage/coverage.opencover.xml" \
  /d:sonar.exclusions="**/wwwroot/lib/**/*" \
  /o:"$SONAR_ORGANIZATION"
```

## Run Build
```
dotnet build --no-incremental --configuration Release
````
## Run Test
```
MSYS2_ARG_CONV_EXCL="*" dotnet test --no-build \
  --configuration Release \
  /p:CollectCoverage=true \
  /p:CoverletOutputFormat="cobertura%2copencover" \
  /p:CoverletOutput=./TestResults/Coverage/
```
## End Analyzes
```
MSYS2_ARG_CONV_EXCL="*" $HOME/.dotnet/tools/dotnet-sonarscanner end /d:sonar.login="$SONAR_LOGIN"
```

[Learn path security](https://docs.microsoft.com/en-us/learn/modules/scan-for-vulnerabilities/4-scan-locally)