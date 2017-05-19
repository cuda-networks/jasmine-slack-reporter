Send jasmine2 / protractor results to Slack

Usage in protractor:

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


"#integration-tests"