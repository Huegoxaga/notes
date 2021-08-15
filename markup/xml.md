# XML

XML is plain text and is similar to html coding, so reviewing or editing the configuration files is relatively simple. XML uses custom tags to define objects or elements. Basic XML formatting rules All XML elements must have a closing tag XML tags are case sensitive Where multiple tags exist, they must be properly nested **bold and italic** not bold and italic&lt;/b&gt; XML Documents Must Have a Root Element

 ..... XML elements can have attributes in name/value pairs just like in HTML. In XML, the attribute values must always be quoted &lt;user name=“Joe"&gt; Comments in XML are similar to that of HTML. 

XPath

xPath nodename Selects all nodes with the name "nodename" / Selects from the root node // Selects nodes in the document from the current node no matter where they are . Selects the current node .. Selects the parent of the current node @ Selects attributes Selects all nodes using wild cards \| connect or combine selections. node\[1\] select first child node of “node”, starting from 1. node\[last\(\)-1\] select second last child node. node\[position\(\)35.00\] select node with price tag has value greater than 35.00

Examples:

bookstore Selects all nodes with the name "bookstore" /bookstore Selects the root element bookstore Note: If the path starts with a slash \( / \) it always represents an absolute path to an element!  
bookstore/book Selects all book elements that are children of bookstore //book Selects all book elements no matter where they are in the document bookstore//book Selects all book elements that are descendant of the bookstore element, no matter where they are under the bookstore element //@lang Selects all attributes that are named lang //title\[@lang\] Selects all the title elements that have an attribute named lang //title\[@lang='en'\] Selects all the title elements that have a "lang" attribute with a value of "en"

