Parser Plugin Overview
======================

Fluentd has 6 types of plugins: [Input](input-plugin-overview.md),
[Parser](parser-plugin-overview.md), [Filter](filter-plugin-overview.md),
[Output](output-plugin-overview.md), [Formatter](formatter-plugin-overview.md)
and [Buffer](buffer-plugin-overview.md). This article gives an overview of
Parser Plugin.


Overview
--------

Sometimes, the `format` parameter for input plugins (ex:
[in\_tail](/articles/in_tail.md), [in\_syslog](/articles/in_syslog.md), [in\_tcp](/articles/in_tcp.md) and
[in\_udp](/articles/in_udp.md)) cannot parse the user's custom data format (for
example, a context-dependent grammar that can't be parsed with a regular
expression). To address such cases. Fluentd has a pluggable system that
enables the user to create their own parser formats.

How To Use
----------

-   Write a custom format plugin. [See here for more
    information](plugin-development#parser-plugins).
-   From any input plugin that supports the "format" field, call the
    custom plugin by its name.

Here is a simple example to read Nginx access logs using `in_tail` and
`parser_nginx`:

``` {.CodeRay}
<source>
  @type tail
  path /path/to/input/file
  format nginx
  keep_time_key true
</source>
```

List of Built-in Parsers
------------------------

-   [regexp](/articles/parser_regexp.md)
-   [apache2](/articles/parser_apache2.md)
-   [apache\_error](/articles/parser_apache_error.md)
-   [nginx](/articles/parser_nginx.md)
-   [syslog](/articles/parser_syslog.md)
-   [csv](/articles/parser_csv.md)
-   [tsv](/articles/parser_tsv.md)
-   [ltsv](/articles/parser_ltsv.md)
-   [json](/articles/parser_json.md)
-   [multiline](/articles/parser_multiline.md)
-   [none](/articles/parser_none.md)

### 3rd party Parsers

-   [grok](https://github.com/fluent/fluent-plugin-grok-parser)

If you are familiar with grok patterns, grok-parser plugin is useful.
Use `< 1.0.0` versions for fluentd v0.12.

List of Core Input Plugins with Parser support
----------------------------------------------

with `format` parameter.

-   [in\_tail](/articles/in_tail.md)
-   [in\_tcp](/articles/in_tcp.md)
-   [in\_udp](/articles/in_udp.md)
-   [in\_syslog](/articles/in_syslog.md)
-   [in\_http](/articles/in_http.md)


------------------------------------------------------------------------

If this article is incorrect or outdated, or omits critical information,
please [let us know](https://github.com/fluent/fluentd-docs/issues?state=open).
[Fluentd](http://www.fluentd.org/) is a open source project under [Cloud
Native Computing Foundation (CNCF)](https://cncf.io/). All components
are available under the Apache 2 License.