This is a chainable weather underground client for node.js

# Install
    npm install wundergroundnode
    var Wunderground = require('wundergroundnode');
    var myKey = '12312314';
    var wunderground = new Wunderground(myKey);

# How To Use
The syntax follows a simple pattern:
    
    wunderground.[resource calls(s)].request(myQuery, callback);
    
The available resource calls are the following (you must include one in your request):

- conditions
- hourlyForecast
- hourlyTenDayForecast
- forecast
- almanac
- yesterday
- geolookup
- astronomy

The documentation for each resource can be found here: http://www.wunderground.com/weather/api/d/docs?d=index. That also covers how to perform queries against their api.

So to get the current conditions you would use the following code:

    wunderground.conditions().request('84111', function(err, response){
        console.log(response);
    }

Where the real fun comes in, however, is when you want more than resource in a single call. This functionality is crucial to save on weather underground costs. So extending the example, lets also get the forecast:

    wunderground.conditions().forecast().request('84111', function(err, response){
        console.log(response);
    }
    
#Running Unit Tests
In order to run unit tests you need to include a file called "devkey" in the test directory. This file must contain only your dev key (no spaces or newlines).

Then simply run this command:

    make test
    
If you have instanbul installed globally you can also run the tests with code coverage results:

    make coverage