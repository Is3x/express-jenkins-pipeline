# express-jenkins-pipeline

A deliberately minimal Express service, used as the build target for a Jenkins
CI/CD pipeline exercise. University coursework, 2022.

The application is one route — the point was never the app, it was having
something small and deterministic for a pipeline to build, test and deploy.

## Layout

```
lab4.js        the service: one GET / route, listens on $PORT or 5000
test/test.js   supertest + mocha check of that route's response
script/test    test entry point the pipeline calls
deploy/        deployment stage
```

## Running it

```
npm install
node lab4.js        # http://localhost:5000
./script/test       # mocha against test/test.js
```

## Pipeline

Jenkins ran the stages in order — install dependencies, execute `script/test`,
then deploy on green. The Jenkins job configuration itself lived in the CI
server rather than in this repository, so what is here is the build target and
its test, not the pipeline definition.
