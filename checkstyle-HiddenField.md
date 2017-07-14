Pattern: Check that a local variable or a parameter does not shadow a field that is defined in the same class

Issue: -

## Description

Checks that a local variable or a parameter does not shadow a field that is defined in the same class. 

## Examples

To configure the check: 
    
    
    <module name="HiddenField"/>
            

To configure the check so that it checks local variables but not parameters: 
    
    
    <module name="HiddenField">
        <property name="tokens" value="VARIABLE_DEF"/>
    </module>
            

To configure the check so that it ignores the variables and parameters named "test": 
    
    
    <module name="HiddenField">
        <property name="ignoreFormat" value="^test$"/>
    </module>
            
    
    
    class SomeClass
    {
        private List<String> test;
    
        private void addTest(List<String> test) // no violation
        {
            this.test.addAll(test);
        }
    
        private void foo()
        {
            final List<String> test = new ArrayList<>(); // no violation
            ...
        }
    }
            

To configure the check so that it ignores constructor parameters: 
    
    
    <module name="HiddenField">
        <property name="ignoreConstructorParameter" value="true"/>
    </module>
            

To configure the check so that it ignores the parameter of setter methods: 
    
    
    <module name="HiddenField">
        <property name="ignoreSetter" value="true"/>
    </module>
            

To configure the check so that it ignores the parameter of setter methods recognizing setter as returning either `void` or a class in which it is declared: 
    
    
    <module name="HiddenField">
        <property name="ignoreSetter" value="true"/>
        <property name="setterCanReturnItsClass" value="true"/>
    </module>

## Further Reading

* [checkstyle - HiddenField](http://checkstyle.sourceforge.net/config_coding.html#HiddenField)