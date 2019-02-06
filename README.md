# Laravel Application Testing
Functional testing for laravel 5.7+, perhaps even 5.4+, 
[like "interacting with your application" in laravel 5.3](https://laravel.com/docs/5.3/application-testing#interacting-with-your-application) (copied from it). 
It can be simpler to use than laravel browser tests, faster to run, and you can use DatabaseTransactions trait on your tests. 

## How to use

    composer require --dev grray/laravel-application-testing

Put into phpunit.xml (in your project root directory) in section `<php>`

    <env name="APP_URL" value="http://localhost"/>
    
and then put into tests/Feature/HomePageTest.php    
    
    <?php
    
    namespace Tests\Feature;
    
    use LaravelApplicationTesting\InteractsWithPages;
    use Tests\TestCase;
    
    class HomePageTest extends TestCase
    {
        use InteractsWithPages;
    
        public function testBasicExample()
        {
            $this->visit('/')
                 ->click('About Us')
                 ->seePageIs('/about-us');
        }    
    }