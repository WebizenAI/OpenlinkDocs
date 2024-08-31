VAL can be configured by manipulating the triples in a set of pre-defined private graphs (see also [Named Graphs Used Throughout VAL](https://docs.openlinksw.com/valdocs/val_internals.html#val_internals_graphs)). Typically there will be user Interfaces which hide these details from the user but it is good to know the details anyway.

# Page Footers

VAL's own `/sparql` integration allows to set a custom page footer. This can be used to for example show social sharing controls via Javascript commands. Each endpoint has its own configuration. The following example shows how the main `/sparql` endpoint of [http://my.openlinksw.com](http://my.openlinksw.com/) can be enhanced with social sharing controls:

sparql

prefix oplcfg: <http://www.openlinksw.com/ontology/configuration#>

with <urn:virtuoso:val:config>

insert {

<http://my.openlinksw.com/sparql> oplcfg:hasFooter [

a oplcfg:HtmlSnippet ;

oplcfg:hasHtmlBody """<script type="text/javascript" src="//s7.addthis.com/js/300/addthis_widget.js#pubid=xa-52ed0731782daa54"></script>

<script type="text/javascript">

addthis.layers({

'theme' : 'transparent',

'share' : {

'position' : 'right',

'services' : 'google,linkedin,twitter,facebook,more'

}

});

</script>"""

] .

}

# Customizing the Standard VAL Authentication Page

VAL allows to somehow customize the `authenicate.vsp` page (see also [Adding VAL Support to a VSP-based Application](https://docs.openlinksw.com/valdocs/val_tutorials.html#val_tutorials_authenticate_vsp)).

## Customize the Logos

Logos displayed on the authentication page can easily be customized per application realm. By default VAL uses the Virtuoso logo as the right image and details about the identity provider on the left.

In order to set the left and right logos for the default realm one can simply insert corresponding triples into the VAL config graph:

sparql

prefix oplcfg: <http://www.openlinksw.com/ontology/configuration#>

prefix oplacl: <http://www.openlinksw.com/ontology/acl#>

insert into <urn:virtuoso:val:config> {

oplacl:DefaultRealm oplcfg:hasLeftLogo <http://path/to/logo.png> .

oplacl:DefaultRealm oplcfg:hasRightLogo <http://path/to/another/logo.png> .

};

Similarly the corresponding anchors (which default to [http://www.openlinksw.com/](http://www.openlinksw.com/) and [http://virtuoso.openlinksw.com/](http://virtuoso.openlinksw.com/)) can be set via:

sparql

prefix oplcfg: <http://www.openlinksw.com/ontology/configuration#>

prefix oplacl: <http://www.openlinksw.com/ontology/acl#>

insert into <urn:virtuoso:val:config> {

oplacl:DefaultRealm oplcfg:hasLeftAnchor <http://me.com/> .

oplacl:DefaultRealm oplcfg:hasRightAnchor <http://me.com/coolstuff> .

};

## Request Access Dialog

There are two modes to how the request access dialog is to be presented: 1. the user needs to press a button to show it (the default), or 2. the dialog is shown automatically as soon as access has been denied for an authenticated person.

This setting is tied to the application realm which means that it does not apply to any other realm.

In order to make the dialog shown automatically in the default realm one sets the following property:

sparql

prefix oplcfg: <http://www.openlinksw.com/ontology/configuration#>

insert into <urn:virtuoso:val:config> {

<urn:virtuoso:val:realms:default> oplcfg:hasRequestAccessDialogMode oplcfg:SimpleRequestAccessDialog

};

In order to restore the default one simply deletes the configuration:

sparql

prefix oplcfg: <http://www.openlinksw.com/ontology/configuration#>

delete from <urn:virtuoso:val:config> {

<urn:virtuoso:val:realms:default> oplcfg:hasRequestAccessDialogMode oplcfg:SimpleRequestAccessDialog

};

# Customizing the ACL Graphs

The [The VAL ACL Rule and Group System](https://docs.openlinksw.com/valdocs/val_acl.html) uses a set of named graphs to store rules, groups, and restrictions. By default VAL uses one graph per application realm and ACL resource type. It uses the default hostname (`HOST` in the example below) of the Virtuoso instance.

**Example:** The default graph which stores the rules in the default realm is the following:

http://HOST/acl/graph/rules/http%3A%2F%2Fwww.openlinksw.com%2Fontology%2Facl%23DefaultRealm

On firsts usage of the API to create a rule, group, or restriction this graph will be created and made private. It will then be stored in the VAL configuration using the oplacl:hasRuleDocument property:

oplacl:DefaultRealm oplacl:hasRuleDocument <http://HOST/acl/graph/rules/http%3A%2F%2Fwww.openlinksw.com%2Fontology%2Facl%23DefaultRealm> .

It is possible to customize these graphs (ideally before the API creates them) which might be desireable for manual ACL resource creation via SPARQL Insert. Since VAL will honor the setting above one can simply add the required triples into the VAL config graph.

**Example:** Given that one wants to change the rule, group, and restriction graphs for the default application realm, the following will do:

sparql

prefix oplacl: <http://www.openlinksw.com/ontology/acl#>

prefix oplres: <http://www.openlinksw.com/ontology/restrictions#>

with <urn:virtuoso:val:config>

insert {

oplacl:DefaultRealm oplacl:hasRuleDocument <urn:acl:rules> ;

oplacl:hasGroupDocument <urn:acl:groups> ;

oplres:hasRestrictionDocument <urn:acl:restrictions> .

};

VAL will honor this settings and store and read all rules, groups, and restrictions from the configured graphs.

Warning

Be aware though that **VAL does not automatically migrate** rules, groups, and restrictions between graphs. This means that changing the graphs will disable existing rules, groups, and restrictions.

It is highly recommended to make these graphs private:

[DB](https://docs.openlinksw.com/valdocs/namespaceDB.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html).RDF_GRAPH_GROUP_INS ('http://www.openlinksw.com/schemas/virtrdf#PrivateGraphs', 'urn:acl:rules');

[DB](https://docs.openlinksw.com/valdocs/namespaceDB.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html).RDF_GRAPH_GROUP_INS ('http://www.openlinksw.com/schemas/virtrdf#PrivateGraphs', 'urn:acl:groups');

[DB](https://docs.openlinksw.com/valdocs/namespaceDB.html).[DBA](https://docs.openlinksw.com/valdocs/namespaceDB_1_1DBA.html).RDF_GRAPH_GROUP_INS ('http://www.openlinksw.com/schemas/virtrdf#PrivateGraphs', 'urn:acl:restrictions');