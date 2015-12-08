##Content architecture check

**Getting Started navigation**

- [x] Link at top of doc
  
      ![Part links](https://github.com/rackerlabs/docs-common/blob/master/rst/getting-started-content-architecture/QE-images/GS-part-links.png)
  
- [ ] Content hierarchy for top-sections looks like one of these two models, with GS title in nav
  
      ![Nav with curl](https://github.com/rackerlabs/docs-common/blob/master/rst/getting-started-content-architecture/QE-images/GS-nav-curl-only.png) 
      ![Nav with curl](https://github.com/rackerlabs/docs-common/blob/master/rst/getting-started-content-architecture/QE-images/GS-nav-with-client.png) 

##Content check

**Use cases and examples**

- [x] Compare use case (topics) in migrated content to original content on docs.rackspace.com to identify any missing content
      
      *Notes:* Moved setup notifications above create a notification.  
               Removed the Additional resources topic -- another one already in the About API section.

- [ ] Use case H1 topics use imperative, H2 topics use gerund

      ![Use case titles](https://github.com/rackerlabs/docs-common/blob/master/rst/getting-started-content-architecture/QE-images/GS-use-case-titles.png) 
      
      *Notes:* Get Kelly's input. 


**Getting Started common content**

- [x ]  Prerequisites include config environment variables (late change)
       
       ![Gen API authl](https://github.com/rackerlabs/docs-common/blob/master/rst/getting-started-content-architecture/QE-images/GS-prereqs.png) 
       

- [x]  GS intro topic that follows boiler plate, might have extra content depending on product.

       ![Gen API authl](https://github.com/rackerlabs/docs-common/blob/master/rst/getting-started-content-architecture/QE-images/GS-intro.png) 
       

- [x]  Uses common Get Credentials topic ==> Save your API Key, Save your Account number are heading levels.

       ![Get Credsl](https://github.com/rackerlabs/docs-common/blob/master/rst/getting-started-content-architecture/QE-images/GS-getcreds.png) 


- [x]  Send API requests content follows template (some docs have only cURL, some have cURL and CLI)
      
       *Note:*  Title in Monitoring is "Send a request to the API`` -- that is more technically accurate. Should become standard. 
                Not sure if it should be Send a request or Send requests to the API  -- Ask Kelly. 

- [x]  Authenticate uses [common content](https://developer.rackspace.com/docs/cloud-big-data/v2/developer-guide/#document-getting-started/authenticate) 



**General API section**

- [x] Authentication section contains short section referencing GS auth example and Identity doc. 
      See [example](https://developer.rackspace.com/docs/cloud-big-data/v2/developer-guide/#document-general-api-info/authentication-gen-api)

- [x] Service access endpoints topic comes immediately after the authentication topic in General API info. 

- [x] Service access endpoints topic has link to authentication response in the Review Auth response section of this Getting Started Guide.  (Link should not point to General API auth topic or Identity documentation).

- [x] How to use cURL topic not included in the General API section (info provided in common auth section)


##Copy check

**Check links**

- [ ] Run link check on page.

- [ ] Look for malformed internal and external cross-references

- [ ] Look for link references that aren't linked, or links that refer to html topics from docs.rackspace.com

- [ ] Look for missing punctuation when link is at end of sentence.  
          (Leave a space between the end of link and the punctuation. ```This is a :ref:`test <refid>` .```

**Code samples**

- [ ] Make sure spacing is OK -- as good as it can be.

- [ ] Examples use environment variables -- ``$ENDPOINT``, ``$TENANT_ID``, and ``$AUTH_TOKEN``  (just mark it if not used, not critical but prefereable.)

- [ ] Paragraph text not merged into code samples.

**Inline markup**

- [ ] Look for stray ` or * symbols or funny spacing

- [ ] Find Bold, italic, or inline literal rendering issues

- [ ] Look for stray | or html leftovers  (margin: 0 ... )

**Tables**

- [ ] Check formatting and inline markup for weird stuff

- [ ] Tables have titles 

**Lists**

- [ ] Look for strange indenting or bolding (ragged margins make Sphinx think things are dl lists.)

