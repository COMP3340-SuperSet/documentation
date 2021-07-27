Change all model deletion to cascade.

Change differenceOf methods to state of deleted items in postSetEdit.js

Fix Owner middleware which currently only checks until it finds the first owner for the first resource. This means somebody could edit another person's resource by including another resource id which they own. This is conditional on ordering. Middleware should instead be run for each controller call, rather than once per request.
