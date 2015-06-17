This java class retrieves current filters for specified [Oracle Hyperion Essbase](http://www.oracle.com/us/solutions/ent-performance-bi/business-intelligence/essbase/index.html)® server, application or database and formats the output as a `create or replace` MaxL statement command.
Generated MaxL statement includes _Add last_ option (`definition_only`) so user associations are preserved.

All you have to do then is to edit the script and to execute it back through MaxL editor in EAS.

This class can be used also for documentation or for filter backup as it provide a quick way of restoring filters.

### Observations ###

Successfully tested on Essbase server version 11.1.1.3, 11.1.1.4 and 1.1.2.1.102 using the default provider services path.


### Release notes ###

  * 1.4.2 corrected a MaxL syntax error (meta\_read)
  * 1.4.1 corrected a connection bug (-v switch)
  * 1.4   corrected bug on generated MaxL statement
  * 1.3   added filter name filtering option
  * 1.2   corrected a connection bug (2)
  * 1.1   corrected a connection bug
  * 1.0   initial release

### Usage and options ###
```
 -a,--essapp <application>                           application name (optional)
 -d,--essdb <database>                               database name (optional)
 -f,--essfilter <filter>                             filter name (optional)
 -h,--help                                           display this help
 -p,--esspwd <password>                              password
 -s,--esssvr <server>                                Essbase server
 -u,--essusr <user>                                  user login
 -v,--essaps <http://ProviderServer:port/aps/JAPI>   Provider server URL - if not specified
                                                     default URL is used  http://<server>:13080/aps/JAPI
```

### Sample output ###
```
C:\GetMaxlFilters>java -jar GetMaxlFilters.jar -s montcuq.com -u admin -p password69 -a sample -d basic

create or replace filter 'Sample'.'Basic'.'test_sample_basic_1'
 no_access on '@IDESCENDANTS(Measures),@IDESCENDANTS(MARKET)',
 read on 'Sales,Cogs,"New York","Massachusetts"',
 write on 'Sales,"New York"'
 definition_only;

create or replace filter 'Sample'.'Basic'.'test_sample_basic_2'
 no_access on '@IDESCENDANTS(Measures),@IDESCENDANTS(MARKET)',
 read on 'Sales,Cogs,"New York","Massachusetts"',
 write on 'Sales,"New York"'
 definition_only;

create or replace filter 'Sample'.'Basic'.'test_sample_basic_3'
 no_access on '@IDESCENDANTS(Measures),@IDESCENDANTS(MARKET)',
 read on 'Sales,Cogs,"New York","Massachusetts"',
 write on 'Sales,"New York"'
 definition_only;
```

```
C:\GetMaxlFilters>java -jar GetMaxlFilters.jar -s montcuq.com -u admin -p password69 -a sample -d basic -f tes

create or replace filter 'Sample'.'Interntl'.'test_srx'
 no_access on '@IDESCENDANTS("Measures"),@IDESCENDANTS("Market")',
 read on '@IDESCENDANTS("Measures"),@IDESCENDANTS("East")',
 write on '@RELATIVE("Measures",0),@RELATIVE("East",0)'
 definition_only;
```

```
C:\GetMaxlFilters>java -jar GetMaxlFilters.jar -s montcuq.com -u admin -p password69 -a sample -d basic -f tes -v http://montpellier.com:13080/aps/JAPI

create or replace filter 'Sample'.'Interntl'.'test_srx'
 no_access on '@IDESCENDANTS("Measures"),@IDESCENDANTS("Market")',
 read on '@IDESCENDANTS("Measures"),@IDESCENDANTS("East")',
 write on '@RELATIVE("Measures",0),@RELATIVE("East",0)'
 definition_only;
```

### From the same author ###

[jssauditmerger](http://code.google.com/p/jssauditmerger/) - Merge your spreadsheet audit logs for better analysis (Java version)

[ssauditmerger](http://code.google.com/p/ssauditmerger/) - Merge your spreadsheet audit logs for better analysis (PERL version)

[essbaserightlog](http://code.google.com/p/essbaserightlog/) - Parse ANY Oracle Hyperion Essbase® server or application logs and generates a full, custom delimited, output for enhanced analysis (database, spreadsheet) (PERL version)

[jrightlog](http://code.google.com/p/jrightlog/) - Parse ANY Oracle Hyperion Essbase® server or application logs and generates a full, custom delimited, output for enhanced analysis (database, spreadsheet) (Java version)