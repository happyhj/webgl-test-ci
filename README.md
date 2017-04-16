## WebGL-Test-CI
an example of how we run WebGL test on CI(continuous integration).

CircleCI

[![CircleCI](https://circleci.com/gh/socialtables/webgl-test-ci.svg?style=svg&circle-token=823a8a192f2ef57e987371e7918c5c37a126cedd)](https://circleci.com/gh/socialtables/webgl-test-ci)


TravisCI

[![Build Status](https://travis-ci.com/socialtables/webgl-test-ci.svg?token=ttyGPvHTywxXgN8yBeaM&branch=master)](https://travis-ci.com/socialtables/webgl-test-ci)

One of the pain point for running WebGL test on CI is most CIs don't have GPU support, especially for client side rendering. For server side rendering, we could use [headless-gl](https://github.com/stackgl/headless-gl). The testing we are running here is focus on client side WebGL rendering and mostly for image comparison.


#### Enviroments
* Electron

	We use electron as our client side rendering for WebGL. When we run Electron, we pass a chromium flag **--ignore-gpu-blacklist** to make sure our WebGL test can run in an non-gpu environment.

* Docker

	Dcoker is used to make sure the environment we run the test are the same on local and on CI.

* CircleCI

	We use CircleCI here as the CI example. As long as the CI supports Docker, our test should run fine.

* Webpack

	We use webpack to bundle our test client.


#### Run

``` npm run test ```

Everytime we run the test, we will run our test inside Docker, which is same as when we run our test on CI. The images we generate inside Docker will copy out to our local using shared volume.

For image comparison, there are multiple libraries could do that.
