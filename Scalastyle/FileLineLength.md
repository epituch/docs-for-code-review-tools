Pattern: Line is too long

Issue: -

## Description

Your source code should not contain very long lines. The default wrapping in most tools disrupts the visual structure of the code, making it more difficult to understand.

## Parameters
<table><tr><th>Name</th><th>Description</th><th>Type</th><th>Default Value</th></tr><tr><td>maxLineLength</td>
        <td>Maximum line length</td>
        <td>integer</td>
        <td>160</td>
      </tr><tr><td>tabSize</td>
        <td>Tab size</td>
        <td>integer</td>
        <td>4</td>
      </tr><tr><td>ignoreImports</td>
        <td>Ignore import statements</td>
        <td>boolean</td>
        <td>false</td>
      </tr></table>

## Example configuration
<pre>&lt;check enabled=&quot;true&quot; class=&quot;org.scalastyle.file.FileLineLengthChecker&quot; level=&quot;warning&quot;&gt;
 &lt;parameters&gt;
  &lt;parameter name=&quot;maxLineLength&quot;&gt;100&lt;/parameter&gt;
  &lt;parameter name=&quot;tabSize&quot;&gt;2&lt;/parameter&gt;
  &lt;parameter name=&quot;ignoreImports&quot;&gt;true&lt;/parameter&gt;
 &lt;/parameters&gt;
&lt;/check&gt;</pre>
<a name="org_scalastyle_file_FileTabChecker" />

## Further Reading

* [Scalastyle - FileLineLength](http://www.scalastyle.org/rules-1.0.0.html#org_scalastyle_file_FileLineLengthChecker)