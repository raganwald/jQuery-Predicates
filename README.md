jQuery Predicates
===

[jQuery Predicates][pred] adds two new methods to jQuery:

* **exists** returns true if the selection is not empty. For example, `$('.preference-pane:visible').exists()` returns true if the preference pane is visible.
* **do\_not\_exist** returns true if the selection is empty. For example, `$('input.invalid').do_not_exist()` returns true if there are no `input` elements with class `invalid`.

For your convenience, there are synonyms `.exist()` and `.does_not_exist()`, so your code can give a hint as to whether you expect there to be one or many elements. So you can write this:

    outstanding_tasks = $('.task.outstanding')

    if (outstanding_tasks.exist())
      update_to_do_list(outstanding_tasks);
    
Or perhaps this:

    while ($('.notification-banner').does_not_exist()) {
      // ...
    }

See for yourself:

    ;(function (jq_fn) {		
    	jq_fn.exists = function () {
    		return !!(this.length);
    	};
    	jq_fn.exist = jq_fn.exists;
    	jq_fn.do_not_exist = function () {
    		return !(this.length);
    	};
    	jq_fn.does_not_exist = jq_fn.do_not_exist;
    })(jQuery.fn);
    
If you don't want to use jQuery Predicates, by all means continue testing for `$('.foo:visible').length` or `$('input.invalid').length == 0`. But wouldn't you agree that it's more elegant to have code that says exactly what it means?

p.s. jQuery Predicates plays well with [jQuery Combinators][comb]'s `.ergo(...)` and `.when(..)` methods.

p.p.s I'm writing a book called [CoffeeScript Ristretto](http://leanpub.com/coffeescript-ristretto). Check it out!

[comb]: http://github.com/raganwald/jQuery-Combinators
[pred]: http://github.com/raganwald/jQuery-Predicates