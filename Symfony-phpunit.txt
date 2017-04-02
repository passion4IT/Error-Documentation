Phpunit test with Symfony:

Error:
    PHP Fatal error:  Class PHPUnit_Util_DeprecatedFeature_Logger contains 1 abstract method and must therefore be 
    declared abstract or implement the remaining methods (PHPUnit_Framework_TestListener::addRiskyTest) in 
    ../vendor/phpunit/phpunit/PHPUnit/Util/DeprecatedFeature/Logger.php on line 59


Description:
    This error is common when you have misconfigured phpunit.xml.dist. This lets your tests to fail unless you apply 
    solution mentioned below.

Solution:
    The solution is quite easy. You just have to remove the colors config value from phpunit.xml.dist.
    e.g.
        your code should look something like this:
            <phpunit xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                xsi:noNamespaceSchemaLocation="http://schema.phpunit.de/4.1/phpunit.xsd"
                backupGlobals="false"
                colors="true"
                bootstrap="app/autoload.php"
            >
    After removal:
            <phpunit xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance"
                xsi:noNamespaceSchemaLocation="http://schema.phpunit.de/4.1/phpunit.xsd"
                backupGlobals="false"
                bootstrap="app/autoload.php"
            >

The tests should pass now, if there is no futher errors in your code.