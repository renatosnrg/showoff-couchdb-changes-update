<!SLIDE section>

# Document Update Handlers #

<!SLIDE bullets>

# Document Update Handlers #

* Functions to create or update a document
* Stored under “updates” design document attribute
* Accept POST/PUT headers
* Accept query string parameters

<!SLIDE small>

# Update Handler #

	@@@ javascript
	{
		updates: {
			"in-place" : function(doc, req) {
			    var field = req.form.field;
			    var value = req.form.value;
			    var message = "set "+field+" to "+value;
			    doc[field] = value;
			    return [doc, message];
			}
		}
	}

	http://127.0.0.1:5984/<database>/_design/<designdoc>/
	_update/in-place/<mydocId>?field=title&value=test
	
<!SLIDE smaller>

# Request #

	@@@ javascript
	{
	  "info": {
	    "db_name": "loot",
	    /* and many more */
	    "committed_update_seq": 27
	  },
	  "id": null,
	  "uuid": "7f8a0e3833bcc7161cfab80275221dc1",
	  "method": "POST",
	  "path": ["loot", "_design", "haul", "_update", "new"],
	  "query": {},
	  "headers": {"Accept": "application/xml,application/xhtml+xml,
		text/html;q=0.9,text/plain;q=0.8,image/png,*/*;q=0.5" 
		/* and many more */},
	  "body": "name=Jeff",
	  "peer": "127.0.0.1",
	  "form": {"name": "Jeff"},
	  "cookie": {},
	  "userCtx": {"db": "loot", "name": null, "roles": []}
	}
	
<!SLIDE small>

# Response #

	@@@ javascript
	Javascript Object:
	
		var resp =  {
		  "headers" : {
		    "Content-Type" : "application/xml"
		  },
		  "body" : doc.xml
		};
	

	Or plain text:
	
		<p>Update function complete!</p>