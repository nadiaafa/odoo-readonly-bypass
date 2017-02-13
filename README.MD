#Dealing Readonly attributes with onchange function – Odoo#

came across the situation where we have to change field value on onchange function and keep some field readonly.
With core its not possible to bypass that functionality, either we have to make those fields as a function or related fields.

And then ASCONE SA/NV came as rescuer for those who were struggling for that functionalities, 
with their module Read Only Bypass which provides a solution to the problem of the interaction between 'readonly'
attribute and 'on_change' attribute when used together.

How to use this functionality:

Install the module.

To change that behavior you have to set context in xml file on "ir.actions.act_window":
```xml
<record id="sale.action_quotations" model="ir.actions.act_window">
<field name="context">{'readonly_by_pass': True}</field>
</record>```

or by telling fields allowed to change:


```xml 
<record id="sale.action_quotations" model="ir.actions.act_window">
<field name=”context”>
{'readonly_by_pass': ['readonly_field_1', 'readonly_field_2',]}
</field>
</record>```

On one2many fields, you can also pass the context in the field definition:


```xml 
<field name="one2many_field" context="{'readonly_by_pass': True}"/>```
