# CHANGELOG

## v4.0.9 (2016-05-26)
* WDIO changes:
    * enabled debugging by passing argv to child process (thanks @kurtharriger #1345)

## v4.0.8 (2016-05-25)
* global changes:
    * introduced new error type for waitForXXX timeouts (#1281)
    * doc improvements (wording/content)
    * don't set firefox as default browser if mobile capabilities are detected
    * add offset coords to left/middle/rightclick (#1335)
* WDIO changes:
    * export Launcher API to Webdriver object (#1311)

## v4.0.6 (2016-05-04)
* global changes:
    * docs improvements
    * removed shrinkwrap file

* WDIO changes:
    * fixed bug where onPrepare was called twice and onComplete none (#1197)
    * allow to set services without having them on NPM (#1198)
    * enable custom command chaining (#1218)
    * fixed waitForXXX commands not able to interpret reverse argument (#1209)
    * better support for element as first citizen
    * allow modification of capabilities through services
    * fixed `Unrecognised test [XXX] for suite [YYY]` issue (#1195)
    * better support for log file names in windows (#1226)
    * added testingbot service to cli configurator (#1263)
    * fixed bug where applying user and key as cli argument didn't work (#1264)

## v4.0.5 (2016-03-23)
* global changes:
    * added class name selector for ios and android
    * docs improvements

* multiremote:
    * fixed capability issue (#1220)
    * added helper method `getInstances` to get instance names

## v4.0.4 (2016-02-03)
* global changes:
    * minimum required node version: v0.12.x
    * complete code rewrite into ES2016 conform JavaScript (compiled using Babel)
    * moved 3rd party integrations (reporters, services, framework) into own NPM packages
    * introduced concept of services for the WDIO testrunner (e.g. [wdio-sauce-service](https://github.com/webdriverio/wdio-sauce-service))
    * commands in WDIO are getting executed in a synchronous way using [Fibers](https://www.npmjs.com/package/fibers)
    * added [Grunt](http://gruntjs.com/) as project task manager

* WDIO changes:
    * retry mechanism for failing requests to the Selenium server as well as for [stale element reference](https://w3c.github.io/webdriver/webdriver-spec.html#dfn-error-code) errors
    * commands are running synchronous (can be disabled by setting `sync: false` in wdio.conf.js)
    * better support for [page objects](https://github.com/webdriverio/webdriverio/tree/master/examples/pageobject) with WebdriverIO
    * runs multiple specs per capability at a time (in v3 it was one spec per capability)
    * elements can now be treated as first citizen (no need for selector parameter if element(s) command) was called before
    * limit number of running instances with `maxInstances`
    * no support for callbacks in commands anymore (as last parameter)
    * no support generators anymore (commands are sync anyway through [Fibers](https://www.npmjs.com/package/fibers))
    * added new hooks: beforeSuite, beforeHook, beforeTest, beforeCommand, afterCommand, afterTest, afterHook, afterSuite, onError and beforeFeature, beforeScenario, beforeStep, afterFeature, afterScenario, afterStep (Cucumber framework only)
    * implemented small API for launcher package for better integration in 3rd party packages like grunt/gulp-webdriver
    * new Allure reporter: [wdio-allure-reporter](https://github.com/webdriverio/wdio-allure-reporter), no spec reporter anymore (but in the making: [wdio-spec-reporter](https://github.com/webdriverio/wdio-spec-reporter))
    * TypeScript support (#1060)

* mobile changes:
    * added uiautomator/uiautomation and accessibility id location strategy
    * update [Appium](http://appium.io/) commands for mobile testing

* API changes:
    * added `waitUntil` interval option (#844)
    * added `getUrl` command (#877)
    * better support for unicode characters in setValue/addValue/keys
    * several improvements and bugfixes
    * added `getGridNodeDetails`, `gridProxyDetails` and `gridTestSession` to get information about the Selenium grid and their nodes
    * added `selectByAttribute` to select options by any attribute field

* Multibrowser changes:
    * modified then arguments from having one argument per browser to having one argument as an object with browser names and their results as properties

## v3.4.0 (2015-12-23)
* documentation improvements (#910, #925, #939, #947, #949, #943, #964, #966)
* added selectByName command (#917)
* bugfix: emit test:end in jasmine (#918)

## v3.3.0 (2015-11-24)
* added Unicode support (#850)
* enable passing cli args to runner processes (#851)
* docs improvements (#854, #853, #861, #871)
* elminate Seleniums staleElement errors (#857)
* fixed screenshot file names for Windows user (#868)
* added new command `getUrl` (#877)
* fixed isVisibleWithinViewport helper (#885, #886, #887)
* update Sauce Labs job even when using Sauce Connect (#881)
* fixed switchTab command (#898)

## v3.2.6 (2015-10-31)
* expose sessionId and capabilities to after() hook
* Adds a configuration: option.waitforInterval and a parameter to waitUntil for setting the polling interval for waitUntil.
* support for mocha's 'qunit' interface

## v3.2.5 (2015-10-07)
* make sure edge driver follows standards for querying elements (#762)
* fixed xunit reporter bug (#797, #801)
* fixed indention bug in spec reporter (#800)
* Preserve mocha `this` in testrunner-wrapped generators (#813)
* better Babel support (##816)

## v3.2.4 (2015-09-16)
* bugfixes in xunit reporter
* removed undefined first argument in after hook
* improved error handling in waitFor commands

## v3.2.3 (2015-09-11)
* some minor bugfixes

## v3.2.2 (2015-09-09)
* fixed bug where cli args didn't overwrite config properties
* fixed bug where browser extensions throw E2BIG error
* allow test files with .coffee extension
* better error message if command gets executed w/o session id
* allow usage of custom reporter

## v3.2.1 (2015-09-01)
* command response with null value will be logged again (#738)
* added documentation
* support w3c webdriver draft keys (#744)
* enable multiremote test in wdio test runner (#741)
* kill Selenium session properly when canceling the wdio process (#746)

## v3.2.0 (2015-08-25)
* improved error handling (no error propagation) (#629)
* wdio test runner cli improvements (#704)
* added protocol bindings for contexts (#703)
* make selenium path customizable (#690)
* enable compilers and require in Mocha framework (#660)
* new command `getCommandHistory` (#618)
* allow to ignore undefined steps (#635)
* bugfixes (#631, #637, #669, #684, #699)

## v3.1.0 (2015-07-11)
* better error messages if waitForXXX commands fail
* improved error handling
* set default logging prefs
* allow to intercept jasmine assertions
* check logging types before requesting logs
* minor bugfixes and doc improvements

## v3.0.5 (2015-07-07)
* mocha framework: allow inclusive and exclusive tests

## v3.0.4 (2015-07-07)
* fixed bug where feature files got filtered out in config parser

## v3.0.3 (2015-07-06)
* show also title of pending test (refs #606)

## v3.0.2 (2015-07-06)
* if specFn is undefined we are dealing with a pending function (fixes #606)

## v3.0.1 (2015-07-04)
* lowercase framework string (fixes #601)
* make v3 work with PhantomJS < 2.0 (fixes #594)

## v3.0.0 (2015-06-29)
* rewritten WebdriverIO core to a Monad
* removed ChainIt dependency
* implemented test runner with different reporter and support for Mocha, Jasmine and Cucumber
* added multiremote feature to control multiple instances at the same time
* enable selector chaining
* removed waitFor command (please replace it with waitForExist as it works the same way)
* new commands: [debug](http://webdriver.io/api/utility/debug.html)

## v2.4.5 (2015-01-30)
* return promise result if responseMethod is not a function (see #401)

## v2.4.4 (2015-01-24)
* make PromiseHandler to handle Q promises (see #399)

## v2.4.3 (2015-01-10)
* `saveScreenshot` doesn't require a file path anymore if only the base64 data is required (see #393)
* don't throw an error if error handler is registered (see #385)

## v2.4.2 (2015-01-07)
* fixed bug in PromiseHandler when execute command just got a single function parameter (closes #383)
* make colored logs optional (closes #298)

## v2.4.1 (2014-12-28)
* fixed bug in `selectByValue` and `selectByVisibleText` in which the absolute xPath queried value/text of different select element
* allow more xpath expressions

## v2.4.0 (2014-12-05)
* support for promises A+ (yeah!)
* introduced `waitforTimeout` option so set default timout time for all waitForXXX commands (see #345)
* let selectByValue accept number values (see #369)

## v2.3.0 (2014-10-24)
* added selectByIndex, selectByValue and selectByVisibleText for super easy selecting of options in select elements

## v2.2.3 (2014-09-18)
* support for all selector strategies in getHTML command (closes #302)

## v2.2.2 (2014-09-15)
* consider parent elements in waitForVisible command (closes #293)
* added library User-Agent string to header for statistical reporting (closes #296)
* updated examples

## v2.2.1 (2014-09-05)
* fixed bug in isVisible helper, thanks @fufnf

## v2.2.0 (2014-09-01)
* new commands:
    - [elementIdElement](http://webdriver.io/api/protocol/elementIdElement.html)
    - [elementIdElements](http://webdriver.io/api/protocol/elementIdElements.html)
    - [selectorExecute](http://webdriver.io/api/action/selectorExecute.html)
    - [selectorExecuteAsync](http://webdriver.io/api/action/selectorExecuteAsync.html)
    - [setViewportSize](http://webdriver.io/api/window/setViewportSize.html)
    - [getViewportSize](http://webdriver.io/api/window/getViewportSize.html)
* improved waitfor commands - now with support if all selector strategries (thanks to selectorExecuteAsync and @nickyout)

## v2.1.2 (2014-08-22)
* Fix: log command expecting an object and not a string
* skip close test (still to flaky)

## v2.1.1 (2014-08-20)
* took saveScreenshot functionality back to basic
* removed gm dependency since it causes too many errors when installing

## v2.1.0 (2014-08-11)
* new commands:
    - [isEnabled](http://webdriver.io/api/state/isEnabled.html)
    - [elementIdEnabled](http://webdriver.io/api/protocol/elementIdEnabled.html)
* make ErrorHandler easy accessible

## v2.0.1 (2014-08-10)
* renamed project lib constructor
* fixed isMobile detection in `chooseFile` command

## v2.0.0 (2014-08-10)
* initial release (for older releases check out the [WebdriverJS changelog](https://github.com/webdriverio/webdriverio/blob/webdriverjs/CHANGELOG.md))
