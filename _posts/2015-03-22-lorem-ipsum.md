---
layout: post
title: Lorem ipsum dolor sit amet
---

> Morbi a iaculis ipsum. Nullam semper massa consequat, porttitor mi sed, euismod quam. Mauris id elementum est. Donec blandit ornare libero, eget fermentum ipsum cursus a. Praesent ut molestie augue. In id lobortis purus. Cras consequat convallis magna, et pharetra quam mattis vel.

### Etiam tristique at tortor non tempor

Lorem ipsum dolor sit amet, consectetur adipiscing elit. Cras quis erat erat. Donec cursus a quam a pharetra. Nulla bibendum, purus in rutrum semper, nunc lectus porta enim, id mollis tellus velit vitae dui. Duis eget ipsum vehicula, tincidunt mauris nec, scelerisque est. Aliquam gravida sagittis eros, in molestie lacus gravida ac. Etiam tristique at tortor non tempor. Cras eget mi a tellus facilisis rhoncus. Duis eu est sagittis, ornare velit sed, pellentesque lacus. In orci leo, venenatis ac dictum sit amet, congue sit amet sem.

Quisque auctor hendrerit pellentesque. Etiam laoreet, libero quis fringilla placerat, leo arcu dictum arcu, ac tempor turpis purus in risus. Sed suscipit velit diam, ac mollis tortor hendrerit non. Morbi sed fringilla leo. Nulla fringilla tempor neque, sed convallis metus auctor vitae. Ut nec mattis elit, efficitur interdum justo. Mauris vitae mollis ante, sit amet finibus eros. Aliquam dignissim iaculis velit, in facilisis felis semper sed. Mauris id varius urna. Curabitur id orci orci. Duis vel ipsum vel massa malesuada pharetra nec ac odio.

### Mauris pulvinar eu quam vitae pharetra

Sed mollis sodales urna ut faucibus. Sed vitae arcu lacinia, lobortis mauris id, dapibus ligula. Nunc a sem libero. Nunc dictum bibendum enim ac bibendum. Ut id erat tristique, consequat lorem et, consectetur libero. Cras facilisis sit amet nulla nec suscipit. Quisque mollis lorem facilisis risus aliquet tincidunt eu id enim.

{% highlight yaml %} 
	getFilteredList: function(listsCollection, filteredProp) {
		return listsCollection.map(function(list) {
			return {
				id 	  : list.id,
				name  : list.name,
				items : list.items.getElementsWith(filteredProp, true)
			}
		}).filter(function(list) {
			return list.items.length > 0;
		});
	}
{% endhighlight %}

Cras faucibus enim accumsan est suscipit gravida a nec turpis. Duis ac cursus justo. Aenean finibus, ligula vitae pretium feugiat, mauris lectus mattis dolor, eu commodo arcu massa sed neque. Mauris pulvinar eu quam vitae pharetra. Curabitur sit amet commodo nibh. Mauris a iaculis odio. Maecenas vitae leo sed metus tempor tempor.