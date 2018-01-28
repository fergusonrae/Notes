# What is it?

Extensible Markup Lange (XML) is a markup language, like HTML. It is used in particular to describe data.

It is known as being self-describing, meaning the structure of the data is embedded with the data. The format can be used by anyone.

It is a simpler/easier subset of the Standard Generalized Markup Language.

---

Most of this information has come from the below

**Cite:** https://www.w3schools.com/xml

---



# Examples

Below is an example of xml structure.

```xml
# From https://www.w3schools.com/xml/default.asp

<?xml version="1.0" encoding="UTF-8"?>
<note>
  <to>Tove</to>
  <from>Jani</from>
  <heading>Reminder</heading>
  <body>Don't forget me this weekend!</body>
</note>
```

And a second, slightly more complex example

```xml
<?xml version="1.0" encoding="UTF-8"?>
<breakfast_menu>
<food>
    <name>Belgian Waffles</name>
    <price>$5.95</price>
    <description>
   Two of our famous Belgian Waffles with plenty of real maple syrup
   </description>
    <calories>650</calories>
</food>
<food>
    <name>Strawberry Belgian Waffles</name>
    <price>$7.95</price>
    <description>
    Light Belgian waffles covered with strawberries and whipped cream
    </description>
    <calories>900</calories>
</food>
<food>
    <name>Homestyle Breakfast</name>
    <price>$6.95</price>
    <description>
    Two eggs, bacon or sausage, toast, and our ever-popular hash browns
    </description>
    <calories>950</calories>
</food>
</breakfast_menu>
```



# Structure

The basic building block is called an element and is definied by tags with a beginning and an ending tag. These elements can be nested. It does not have pre-defined tags though. Tags are defined by the user and are case sensitive.

The document is formed as an element tree. Starting at a root element and branching from root to child elements. All elements can have sub elements called child elements. But, there can only be one root that is the parent of all other elements.

! [Tree Structure Image] (https://www.w3schools.com/xml/nodetree.gif)

What this structure looks like in code

```xml
<?xml version="1.0" encoding="UTF-8"?> # This is called the XML prolog, it's optional
<bookstore>
  <book category="cooking"> # Attribute values must have quotes around them
    <title lang="en">Everyday Italian</title>
    <author>Giada De Laurentiis</author>
    <year>2005</year>
    <price>30.00</price>
  </book>
  <book category="children">
    <title lang="en">Harry Potter</title>
    <author>J K. Rowling</author>
    <year>2005</year>
    <price>29.99</price>
  </book>
  <book category="web">
    <title lang="en">Learning XML</title>
    <author>Erik T. Ray</author>
    <year>2003</year>
    <price>39.95</price>
  </book>
</bookstore>
```



# Element Quirks

Elements will keep all spaces. Multiple spaces in a row will not be truncated and will be left as multiple spaces.

Naming rules

* Case-sensitive
* Must start with letter or underscore
* Cannot
  * Start with "xml" any case
  * Contain spaces
* Avoid hyphens, periods, and colons
* Are usually camel case

# Using Character Entities

There are 5 pre-defined entity references in XML. In order to use some characters in XML elements, you need to replace them with these entity references or have errors.

|  `&lt;`   |  <   |   less than    |
| :-------: | :--: | :------------: |
|  `&gt;`   |  >   |  greater than  |
|  `&amp;`  |  &   |   ampersand    |
| `&apos;`  |  '   |   apostrophe   |
| `&quote;` |  "   | quotation mark |



# Commenting Out

```xml
<!-- This is a comment -->
```



# Schema - XSD

A schema describes the structure of an xml document. The XML Schema language is also referred to as XML Schema Definition. It is writter in XML.

``` xml
# This one is an XSD Example
# https://www.w3schools.com/xml/schema_intro.asp

<?xml version="1.0"?>
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema">

<xs:element name="note">
  <xs:complexType>
    <xs:sequence>
      <xs:element name="to" type="xs:string"/>
      <xs:element name="from" type="xs:string"/>
      <xs:element name="heading" type="xs:string"/>
      <xs:element name="body" type="xs:string"/>
    </xs:sequence>
  </xs:complexType>
</xs:element>

</xs:schema>
```

The greatest strength of XML Schemas is the support for data types. You can easily define, validate, convert, and describe data types.

To use the schema, you can reference it.

```xml
<?xml version="1.0"?>

<note
xmlns="https://www.w3schools.com"
xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
xsi:schemaLocation="https://www.w3schools.com/xml/note.xsd">
  <to>Tove</to>
  <from>Jani</from>
  <heading>Reminder</heading>
  <body>Don't forget me this weekend!</body>
</note>
```

