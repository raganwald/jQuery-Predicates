jQuery Predicates
===

[jQuery Predicates][pred] adds two new methods to jQuery: **exists** returns true if the selection is not empty. For example, `$('.foo:visible').exists()` returns true if there are any elements of class `foo` that are also visible. **do\_not\_exist** returns true if the selection is empty. For example, `$('input.invalid').do_not_exist()` returns true if there are no `input` elements with class `invalid`. For convenience, there are synonyms `.exist()` and `.does_not_exist()`, so your code can give a hint as to whether you expect there to be one or many elements.

So you can write this:

    outstanding_tasks = $('.task.outstanding')

    if (outstanding_tasks.exist())
      update_to_do_list(outstanding_tasks);
    
Or perhaps this:

    while (outstanding_tasks.do_not_exist()) {
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

p.s. jQuery Predicates plays well with [jQuery Combinators][comb]'s `.ergo(...)` and `.when(..)` methods.

[comb]: http://github.com/raganwald/jQuery-Combinators
[pred]: http://github.com/raganwald/jQuery-Predicates