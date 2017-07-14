Pattern: Multiple occurrences of the same string literal within a single file

Issue: -

## Description

Checks for multiple occurrences of the same string literal within a single file. 

Rationale: Code duplication makes maintenance more difficult, so it can be better to replace the multiple occurrences with a constant. 

## Examples

To configure the check: 
    
    
    <module name="MultipleStringLiterals"/>
            

To configure the check so that it allows two occurrences of each string: 
    
    
    <module name="MultipleStringLiterals">
        <property name="allowedDuplicates" value="2"/>
    </module>
            

To configure the check so that it ignores ", " and empty strings: 
    
    
    <module name="MultipleStringLiterals">
        <property name="ignoreStringsRegexp" value='^(("")|(", "))$'/>
    </module>
            

To configure the check so that it flags duplicate strings in all syntactical contexts, even in annotations like `@SuppressWarnings("unchecked")`: 
    
    
    <module name="MultipleStringLiterals">
        <property name="ignoreOccurrenceContext" value=""/>
    </module>

## Further Reading

* [checkstyle - MultipleStringLiterals](http://checkstyle.sourceforge.net/config_coding.html#MultipleStringLiterals)