<div id="table-of-contents">
<h2>Table of Contents</h2>
<div id="text-table-of-contents">
<ul>
<li><a href="#orgheadline3">1. What is DPLA</a>
<ul>
<li><a href="#orgheadline1">1.1. The Digital Public Library of America</a></li>
<li><a href="#orgheadline2">1.2. Aggregates metadata from digital collections presented in their portal at </a></li>
</ul>
</li>
<li><a href="#orgheadline8">2. The Hub model</a>
<ul>
<li><a href="#orgheadline4">2.1. Hubs supply DPLA with metadata</a></li>
<li><a href="#orgheadline7">2.2. 2 types of hub</a>
<ul>
<li><a href="#orgheadline5">2.2.1. content hubs</a></li>
<li><a href="#orgheadline6">2.2.2. service hubs</a></li>
</ul>
</li>
</ul>
</li>
<li><a href="#orgheadline10">3. What is ESDN</a>
<ul>
<li><a href="#orgheadline9">3.1. Empire State Digital Network</a></li>
</ul>
</li>
<li><a href="#orgheadline11">4. What is our workflow</a></li>
<li><a href="#orgheadline12">5. What is Repox</a></li>
<li><a href="#orgheadline16">6. How does Repox work</a>
<ul>
<li><a href="#orgheadline13">6.1. harvests OAI feeds</a></li>
<li><a href="#orgheadline14">6.2. XSLT</a></li>
<li><a href="#orgheadline15">6.3. makes them available to DPLA as an OAI feed</a></li>
</ul>
</li>
<li><a href="#orgheadline18">7. What do we have in the works</a>
<ul>
<li><a href="#orgheadline17">7.1. Our own portal</a></li>
</ul>
</li>
</ul>
</div>
</div>

# What is DPLA<a id="orgheadline3"></a>

## The Digital Public Library of America<a id="orgheadline1"></a>

## Aggregates metadata from digital collections presented in their portal at [<http://dp.la>](http://dp.la)<a id="orgheadline2"></a>

# The Hub model<a id="orgheadline8"></a>

## Hubs supply DPLA with metadata<a id="orgheadline4"></a>

## 2 types of hub<a id="orgheadline7"></a>

### content hubs<a id="orgheadline5"></a>

-   large digital collections that provide metadata for their own content, such as NYPL or BHL

### service hubs<a id="orgheadline6"></a>

-   Hubs that act as a conduit for DPLA ingestion, such as ESDN

# What is ESDN<a id="orgheadline10"></a>

## Empire State Digital Network<a id="orgheadline9"></a>

-   NY state service hub
-   ESDN coordinates metadata harvest, transformation, and ingest for NY state
    ESDN provides services to state regional council members seeking to get their metadata into
    DPLA
-   formed in 2013
-   second generation hub
    -   most of the first generation of DPLA hubs were digital collections
        websites that provided OAI feeds from their content management
        systems
    -   ESDN part of a "second wave" of hubs
    -   pure aggregators
        -   we don't host any content ourselves
        -   we have no public-facing properties
        -   at the present time we just harvest metadata, transform it into
            a format suitable for ingest into DPLA which they harvest

# What is our workflow<a id="orgheadline11"></a>

-   regional council members contact their council's ESDN liaison
-   the liaison procures a letter giving permission to ingest their metadata
-   The provider's contact person contacts Chris Stanton, ESDN's Metadata Specialist
-   Chris works with the provider to normalize and standardize their data
-   Their data is mapped to the ESDN Metadata Application Profile (MAP)
    -   a variant of MODS
    -   which is itself mapped to the DPLA MAP
-   it's an iterative process
-   it's a very manual process
    -   often there will be multiple rounds of writing and rewriting the transforms
    -   tweaking the output
    -   trying to strike a balance between asking the provider to tweak data and writing horrendous special cases
    -   mostly dependent on how consistently the data has been entered into the CMS
    -   minor inconsistencies can be written around
    -   major inconsistencies require the provider to go back and edit the data
    -   However, the date field is always insane
        -   roman numerals
        -   CONTENTdm timespans: 1932;1933;1934;1935;1936 to represent 1932-1936
        -   People will put anything and their dog in the date field - tweet
-   Once the data has been sufficiently massaged it is ingested on a semi-regular basis by DPLA
-   Once ingested DPLA performs additional transformations and enrichments
    -   ESDN was a pilot project for DPLA's new ingestion system [Heidrun](http://github.com/dpla/heidrun)
-   The result is then QAd
    -   sometimes we need to go back and make additional tweaks
-   The records then finally go live on DPLA

# What is Repox<a id="orgheadline12"></a>

-   Repox is OAI aggregator software
-   originally written for the Europeana project
-   appeared to have been abandoned in 2014
-   used by a number of the "second wave" of hubs
-   support community has sprung up around it
-   has a number of quirks
    -   everyone hates it
    -   everyone uses it
-   recently development has been revived
-   DPLA has been rumored to be be working on an aggregator appliance
    -   the fabled and greatly desired "Repox killer"
    -   part of the Hybox project
    -   rumors of its birth are greatly exaggerated

# How does Repox work<a id="orgheadline16"></a>

## harvests OAI feeds<a id="orgheadline13"></a>

-   we define "data sets" that specify the incoming and outgoing formats depending on the CMS in use
-   we then write XSL stylesheets that transform the incoming to the outgoing format
-   we associate those stylesheets with the data set
-   when DPLA requests data the outgoing format is sent

## XSLT<a id="orgheadline14"></a>

-   we built on the great work done at NCDHC
    -   we forked their Github repository of XSLT style-sheets for use with Repox
-   NCDHC is a single CONTENTdm repository, so their stylesheets were written for use with Cdm
-   Since ESDN harvests metadata from a number of different CMSes we use an include model that provides base templates
-   our repository is on Github at [<http://github.com/esdnhub/dpla-custom-repox-xslt>](http://github.com/esdnhub/dpla-custom-repox-xslt)

## makes them available to DPLA as an OAI feed<a id="orgheadline15"></a>

# What do we have in the works<a id="orgheadline18"></a>

## Our own portal<a id="orgheadline17"></a>

-   Plans to work on a NY state wide search portal
-   sort of a "tiny DPLA" for NY state
-   our partners need reporting and statistics tools
-   we attempted to build a basic tool - the "collstool"
    -   based on Repox output
    -   implemented in Jekyll
    -   difficult to achieve using only MODS data in XML
    -   ungainly, manual process that output inaccurate results
    -   source available at [<http://github.com/ESDNHub/collstool>](http://github.com/ESDNHub/collstool)
-   Development work has just begun
    -   Built on the Hydra platform
    -   consuming ESDN data from the DPLA API
        -   with additional enrichments
            -   Sub-collection info
            -   Council info
            -   reporting capabilities
    -   Initial release expected later this summer
