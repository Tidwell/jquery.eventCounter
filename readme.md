Event Counter
Dependancies:  jquery
 
  Sets up an eventCounter [named {counterId}] that counts the number 
  of times {eventType} is fired on $(element) and every {every} times the
  eventType occurs, will fire {onTrigger}
  
  onTrigger gets passed
  	1.  The event
  	2.  The full set of elements that the counter is listening to
 
 	
 	Additional methods:
 	$(elements).eventCounter('destroy' [,counterId])
		removes all tracking from $(elements), or just the tracking from counterId
	$(elements).eventCounter('add', counterId)
		adds $(elements) to the counterId tracking set
 	$(elements).eventCounter('increment', event, counterId)
		increments the event counter with counterId 
	
	//counting clicks on an element and triggering an iframe refresh every 4th click.
	$('.next-button').fn.eventCounter({
	  counterId: 'iframeAd',
	  every: 4,
	  eventType: 'click',
	  onTrigger: function(event, allPossibleTriggers) {
	    $('iframe').contentWindow.location.reload();
	  }
	});
	
	//destroying all tracking on the next button
	$('.next-button').eventCounter('destroy')
	
	//destroying just the iframe counter, leaving any other counters
	$('.next-button').eventCounter('destroy', 'iframeAd')
	
	//adding a previous button to the elements being tracked
	$('.prev-button').eventCounter('add', 'iframeAd');
	
	//you can also not bind to elements and just trigger programatically
	$.fn.eventCounter({settings});
	$.fn.eventCounter('increment', 'click', 'counterId');