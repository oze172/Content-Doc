#### Parser Content
```Java
{
Name = json-bro-tls
  Product = Bro
  DataType = "authentication-successful"
  Conditions = [ """version":"TLS""", """"id.orig_h":""", """"id.resp_h":"""]
  Fields = ${BroParserTemplates.json-bro-activity.Fields}[
    """"established":({outcome}[^,]+)""",
    """"server_name":"({auth_server}[^"]+)""",
    """({auth_method}TLS)"""
  ]
}
```