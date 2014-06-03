Tricky3 Ajax Pagination
=========


Tricky3 ajax pagination plugin is a plugin that will load previous or next pages in ajax.Important this plugin only loads the html of the next or previous pages. To update content there is a sample callback, you can feel free to modify the callback function to suite your needs.

The pagination wrapper should be unique on the page, you can wrap your paginations elements inside a div and add an id to it to make it unique.

Version
----

1.0


Basic setups
--------------

In theme.liquid, add the codes below.
You can load all pages either when document is ready or on a click event of a link.
```
    {{ "tricky3.ajaxpagination.js" | shopify_asset_url | script_tag }}
    <script type="text/javascript">
	$(function(){
        //options that should be passed.
        var options = {
            PaginationSelector : 'div.paginate', //the pagination selector.
    		CurrentPageSelector : '.current', //the current page selector
			NextPageLinkSelector : '.next a',//the next page selector
			PreviousPageLinkSelector : '.prev a',//the previous page selector
			CallBackWhenNextOrPreviousPageIsLoaded : callBackWhenNextOrPreviousPageIsLoaded,/*the callback that will be executed when a page has loaded*/
			CallBack:function(){}/*the callback that will be executed when all pages have been loaded.*/
        };
        
    
        //Example 1 : when document is ready
		$(PaginationWrapperSelector).AjaxPagination(options);
        
        //Example 2 : On click event of a button
        $(LINKSELECTOR).click(function(){
            $(PaginationWrapperSelector).AjaxPagination(options);
            return false;
        })

	});
    
    //basic CallBackWhenNextOrPreviousPageIsLoaded function...
    var callBackWhenNextOrPreviousPageIsLoaded = function(data){
        /*the most basic dom manipulation that you will be doing obviously will be to append new elements to the page, for example lets say you have a wrapper on the page as below
        <ul id="collection-wrapper">
            <li></li>
            <li></li>
        </ul>
        and you want to append new load <li/> elements from the page that has been loaded in ajax. The code will be like below.
      */
        
		$('ul#collection-wrapper').append($(data).find('ul#collection-wrapper').html());
        
    };
    </script>

```
    