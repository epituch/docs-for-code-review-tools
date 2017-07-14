Pattern: Check that constant names conform to a format specified by the format property

Issue: -

## Description

Validates identifiers for constants (`static`, ` final` fields). 

## Examples

Property `format` in module `ConstantName` is used to specify names to be allowed. The following configuration apart from names allowed by default allows `log` or `logger`: 
    
    
    <module name="ConstantName">
        <property name="format"
                  value="^log(ger)?|[A-Z][A-Z0-9]*(_[A-Z0-9]+)*$"/>
    </module>

## Further Reading

* [checkstyle - ConstantName](http://checkstyle.sourceforge.net/config_naming.html#ConstantName)