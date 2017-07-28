# jasmine-slack-reporter

Send jasmine2 / protractor results to Slack

## Protractor usage:

Add to conf.js file
```
 onPrepare: function() {
    var webRep = require('jasmine-slack-reporter');   
    browser.getProcessedConfig().then(function(config) {
        var browserName = config.capabilities.browserName;
        jasmine.getEnv().addReporter(new webRep.WebReporter({
          projectName:'Project 1',
          module:'Module 1',          
          environment : 'Stage',
          slackUrl : 'https://hooks.slack.com/services/ASDF1234/ASDF1234/ABCDEFGHIJKLMNOPQRSTUVWXYZ',
          channel : '#testChannel'
        }));
    }); 
}

```

## jasmine usage 

Create jasmine.js 
```
const Jasmine = require('jasmine');
const webRep = require('jasmine-slack-reporter');

const jasmine = new Jasmine();

jasmine.addReporter(new webRep.WebReporter({
        projectName:'API - Jasmine',
        module:'API',
        url: 'http://demo.qaconsole.com/testruns',
        environment : 'Production',        
      }));

jasmine.loadConfigFile('./spec/support/jasmine.json'); // load jasmine.json configuration
jasmine.execute();
```
Run with node
```
node jasmine.js
```