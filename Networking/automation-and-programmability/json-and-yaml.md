# JSON, YAML and XML

<mark style="color:blue;">**JSON**</mark>, <mark style="color:blue;">**YAML**</mark> and <mark style="color:blue;">**XML**</mark> are all data formats which are simply a way to store and exchange data in a structured format.

* JavaScript Object Notation (JSON)
* eXtensible Markup Language (XML)
* YAML Ain’t Markup Language (YAML)

The data format that is selected will depend on the format that is used by the application, tool, or script that you are using. Many systems will be able to support more than one data format, which allows the user to choose their preferred one.

## Data Format Rules

Data formats have rules and structure similar to what we have with programming and written languages. Each data format will have specific characteristics:

* Syntax, which includes the types of brackets used, such as \[ ], ( ), { }, the use of white space, or indentation, quotes, commas, and more.
* How objects are represented, such as characters, strings, lists, and arrays.
* How key/value pairs are represented. The key is usually on the left side and it identifies or describes the data. The value on the right is the data itself and can be a character, string, number, list or another type of data.

## JSON

<details>

<summary>What is JSON?</summary>

JSON (JavaScript Object Notation) is a lightweight, text-based data interchange format that uses a key-value pair structure for representing structured data.

</details>

* JSON is a very popular format used by web services and [APIs](rest-apis/) to provide public data.
* This is because it is easy to parse and can be used with most modern programming languages, including Python.

### JSON Syntax Rules

These are some of the characteristics of JSON:

* It uses a hierarchical structure and contains nested values.
* It uses braces { } to hold objects and square brackets \[ ] hold arrays.
* Its data is written as key/value pairs.

In JSON, the data known as an object is one or more key/value pairs enclosed in braces { }. The syntax for a JSON object includes:

* Keys must be strings within double quotation marks " ".
* Values must be a valid JSON data type (string, number, array, Boolean, null, or another object).
* Keys and values are separated by a colon.
* Multiple key/value pairs within an object are separated by commas.
* Whitespace is not significant.

At times a key may contain more than one value. This is known as an array. An array in JSON is an ordered list of values. Characteristics of arrays in JSON include:

* The key followed by a colon and a list of values enclosed in square brackets \[ ].
* The array is an ordered list of values.
* The array can contain multiple value types including a string, number, Boolean, object or another array inside the array.
* Each value in the array is separated by a comma.

```json5
{
  "addresses": [
    {
      "ip": "172.16.0.2",
      "netmask": "255.255.255.0"
    },
    {
      "ip": "172.16.0.3",
      "netmask": "255.255.255.0"
    },
    {
      "ip": "172.16.0.4",
      "netmask": "255.255.255.0"
    }
  ]
}
```

The addresses object contains an array of IP addresses and subnet masks objects.

## YAML

<details>

<summary>What is YAML?</summary>

YAML (YAML Ain’t Markup Language) is a human-readable data serialisation format that uses indentation and a minimalist syntax to represent hierarchical data.

</details>

Some of the characteristic of YAML include:

* It is like JSON and is considered a superset of JSON.
* It has a minimalist format making it easy to both read and write.
* It uses indentation to define its structure, without the use of brackets or commas.
* In YAML, a hyphen is used to separate each element in a list.

```yaml
ietf-interfaces:interface:
  name: GigabitEthernet2
  description: Wide Area Network
  enabled: true
  ietf-ip:ipv4:
    address:
    - ip: 172.16.0.2
      netmask: 255.255.255.0
    - ip: 172.16.0.3
      netmask: 255.255.255.0
    - ip: 172.16.0.4
      netmask: 255.255.255.0
```

## XML

<details>

<summary>What is XML?</summary>

XML (eXtensible Markup Language) is a flexible, text-based markup language that uses a hierarchical structure of nested tags to define and store data in a human-readable and machine-readable format.

</details>

Some of the characteristics of XML include:

* It is like HTML , which is the standardized markup language for creating web pages and web applications.
* It is self-descriptive. It encloses data within a related set of tags: **\<tag>data\</tag>**
* Unlike HTML, XML uses no predefined tags or document structure.
* XML objects are one or more key/value pairs, with the beginning tag used as the name of the key: **\<key>value\</key>**

```xml
<?xml version="1.0" encoding="UTF-8" ?>
<ietf-interfaces:interface>
  <name>GigabitEthernet2</name>
  <description>Wide Area Network</description>
  <enabled>true</enabled>
  <ietf-ip:ipv4>
    <address>
      <ip>172.16.0.2</ip>
      <netmask>255.255.255.0</netmask>
    </address>
    <address>
      <ip>172.16.0.3</ip>
      <netmask>255.255.255.0</netmask>
    </address>
    <address>
      <ip>172.16.0.4</ip>
      <netmask>255.255.255.0</netmask>
    </address>
  </ietf-ip:ipv4>
</ietf-interfaces:interface>
```

