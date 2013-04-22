Stuff to fix fast
=================

For this v0 we are running on one json entity per line. This
need to change to, sequence of json separated by whitespace, line break
or nothing at all. This problem might be better fixed using a lexer.

Concept
=======

JSON documents in. JSON documents out.

Should support "one json per line" mode and "json stream" mode.

We use node to keep things fast. We should keep things as fast and simple
as possible so I'll delay the use of parsers and lexers for now that
things are still simple.

Extract elements
----------------

    jawk 'return d.apiKey'
    jawk 'return [d.apiKey, d.businessId]'
    jawk 'return {apikey: d.apiKey, businessId: d.businessId}'

Modify elements
---------------

    jawk 'd.apiKey = "modified"; return d'
    jawk 'd.businessId += "_PRD"; return d'

For v2
------

AWK notation

    jawk '(d.stuff=="something") { return d }'
    jawk '{SUM+=d.price;} END { return "Average Price: " + SUM/NR }'
