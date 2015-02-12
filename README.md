# Renasar Core Library

## Directory Structure

###lib/models
Waterline Models

###lib/protocol
Protocol Objects based on Messaging Service

###lib/scheduler
Scheduler Objects

###lib/services
Standard Service Objects

## Development Notes

Run `grunt watch` to have grunt listen for file changes and run the specs and linter automatically.  Grunt is
configured to use the grunt-notify plugin so it will also provide desktop notifications for test results.

## CI notes

Default clean setup and run with "npm test" is now oriented to immediate
development:


    rm -rf node_modules
    npm install
    npm test

The series for CI systems (Jenkins):

    # verify hint/style
    ./node_modules/.bin/jshint -c .jshintrc --reporter=checkstyle lib index.js > checkstyle-result.xml || true
    ./node_modules/.bin/istanbul cover _mocha -- $(find spec -name '*-spec.js') -R xunit-file --require spec/helper.js
    ./node_modules/.bin/istanbul report cobertura
    ./node_modules/.bin/istanbul report text-summary

