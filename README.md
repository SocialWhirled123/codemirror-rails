mirrors
==========
Testing custom functions for codemirror-rails gem 

In SocialWhirled App:
	codemirror_textarea_search.js.coffee
		search: ->
	    _this = @
	    $('.code_mirror_search').on 'submit', (e) ->
	      e.preventDefault()
	      search = $(this).find('input#search')
	      _this.doSearch(search.val())
	
		  doSearch: (value) ->
		    CodeMirror.commands.doSearch(@sw, value)
		
Then inside codemirror-rails (vendor>assets>js>codemirror>addons>search>search.js)
	function doSearch(cm,rev){
		dialog....("Search for: " ...)
	
		//Add this:
		dialogValue = cm.getSelection()
		returnDialogValue(dialogValue)
	}
	
	//then
	
	function returnDialogValue(v) {
		$('input.search').html(v);
	}
