var POST_URL = "DISCORD WEBHOOK LINK HERE";
function onSubmit(e) {
    var form = FormApp.getActiveForm();
    var allResponses = form.getResponses();
    var latestResponse = allResponses[allResponses.length - 1];
    var response = latestResponse.getItemResponses();
    var items = [];
    var tickAnswers = "";
    for (var i = 0; i < response.length; i++) {
        var question = response[i].getItem().getTitle();
        var answer = response[i].getResponse();
        try {
            var parts = answer.match(/[\s\S]{1,1024}/g) || [];
        } catch (e) {
            var parts = answer;
        }
        if (answer == "") {
            continue;
        }
        for (var j = 0; j < parts.length; j++) 
        {
            tickAnswers += parts[j].toString();
            if(j != (parts.length - 1)) {
                 tickAnswers += ", ";
            }
        }
        items.push({
             "name": question,
             "value": tickAnswers,
             "inline": false
             });
        tickAnswers = "";
    }
  function logmytime(date)
{
// var hours = date.getUTCHours(); // This is UTC hours to test if let's say if we are coding in the middle of the night
  var hours = date.getHours();  //This should be my hours
  var minutes = date.getMinutes(); //This should be my minutes 
  var ampm = hours >= 12 ? 'pm' : 'am';  // Tldr , i put ? to reflect back if 12 is am or pm
  hours = hours % 12;
  hours = hours ? hours : 12; // the hour 0 should be 12 am , you know if what happens if its 00?
  minutes = minutes < 10 ? '0'+minutes : minutes;
  var actualtime = hours + ':' + minutes + ' ' + ampm;
  return actualtime;
}

function logmyyear(date)
{

  var month = date.getMonth()+1;  //This should be my month , because getMonth only can get (0-11) so +1 for offset
  var day = date.getDate(); //This should be my day 
  var year = date.getFullYear(); //This should be my year.

  var actualyear = day + '/' + month  + '/' + year;
  return actualyear;
}


d = logmyyear(new Date) + ' ' +logmytime(new Date);
    var options = {
        "method": "post",
        "headers": {
            "Content-Type": "application/json",
        },
        "contentType": "application/json",
        "payload": JSON.stringify({
            "content": null, // This is not an empty string
            "embeds": [{
                "title": "AvalonSG Member Application Details",
                "fields": items,
                "footer": {
                    "text": "Sent on " + d
                }
            }]
        })
    };
    UrlFetchApp.fetch(POST_URL, options);
};
