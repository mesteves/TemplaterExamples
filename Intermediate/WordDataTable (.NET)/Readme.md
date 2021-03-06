## Word and DataTable

How DataTable can be used in Word. Header metadata.

Two basic ways to use a single DataTable. When column count is unknown and when column count is known.
Templater will respect the width of the table. When column count is know detailed style can be applied to it.

### Dynamic resize

DataTable can be used in dynamic resize way (sending DataTable to low level API). In this case table will be stretched to match rows and columns in provided DataTable.
To inject column names from DataTable, **:header** metadata must be used; otherwise only data will be imported.

### Standard processing

Templater has built-in processor for DataTable, which *knows* how to process DataTable. In that case more style formatting can be applied on the document.

### merge-nulls metadata

One of the internal metadata (meaning it can't be implemented as a simple plugin) is **merge-nulls**.
It can be used for merging cells when they contain null value.

### Section support + custom handler for removing sections

Templater uses document structure to infer beginning/end of the replicating context.
Along the table/list/page/whole document as of v2.5 Templater supports sections. When all specified tags are inside a section that range will be used as a context.
Example shows how to display special table when there are no rows (since default behavior is just to remove the template row - and leave the header).
Appropriate section will be removed based on the custom metadata and the appropriate handler.
Handler will iterate through all tags with the same name and either invoke collapse of that region or hide the tag.