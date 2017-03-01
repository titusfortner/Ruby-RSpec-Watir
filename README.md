# Ruby Watir Tests
[//]: # "[![Travis Status](https://travis-ci.org/saucelabs-sample-test-frameworks/Ruby-RSpec-Selenium.svg?branch=master)](https://travis-ci.org/saucelabs-sample-test-frameworks/Ruby-RSpec-Selenium)"

## Important Disclaimer
This code is provided on an "AS-IS” basis without warranty of any kind, either express or implied, 
including without limitation any implied warranties of condition, uninterrupted use, merchantability, 
fitness for a particular purpose, or non-infringement. 
Your tests and testing environments may require you to modify this project. 
For questions regarding Sauce Labs integration, please see the [Sauce Labs documentation](https://wiki.saucelabs.com/). 
This project is not maintained by Sauce Labs Support.


## Purpose
This is the recommended place to start if you want to create a new project in Ruby.
If you already have an existing test suite and are just looking to add Sauce Labs 
functionality to that project, or if you need to run tests on a mobile application,
take a look at the [Ruby Example Tests](http://www.notimplementedyet.com) project.
 
 
## Technologies used in this project:

#### RSpec
1. [Pass Information to Saucelabs](https://github.com/titusfortner/Ruby-Watir-Tests/blob/master/spec/spec_helper.rb#L12-L21)
2. [Execute Tests in Parallel](https://github.com/titusfortner/Ruby-Selenium-Examples/blob/master/Rakefile#L26)
3. [Integrate with Applitools](https://github.com/titusfortner/Ruby-Watir-Tests/blob/master/spec/spec_helper.rb#L24-L28)
4. [Watir Drops Example](https://github.com/titusfortner/Ruby-Watir-Tests/blob/master/spec/pages/guinea_pig_page.rb)
5. [Watir Model Example](https://github.com/titusfortner/Ruby-Watir-Tests/blob/master/config/data/watir_model.rb)

### Cucumber
1. [Pass Information to Saucelabs](https://github.com/titusfortner/Ruby-Selenium-Examples/blob/master/features/support/env.rb#L7-L31)
2. [Execute Tests in Parallel](https://github.com/titusfortner/Ruby-Selenium-Examples/blob/master/Rakefile#L35)
3. [Integrate with Applitools](https://github.com/titusfortner/Ruby-Selenium-Examples/blob/master/features/support/env.rb#L33-L37)
4. [Page Object Example](https://github.com/titusfortner/Ruby-Watir-Tests/blob/master/features/support/pages/guinea_pig_page.rb)
5. [Data Magic Example](https://github.com/titusfortner/Ruby-Watir-Tests/blob/master/config/data/data_magic.yml)

## Requirements to Run These Examples

1. Global Dependencies
    * [Install Ruby](https://www.ruby-lang.org/en/documentation/installation/)
    * If on Mac install Ruby with [Homebrew](http://brew.sh/)
    ```
    $ brew install ruby
    ```
    * Install [Rake](http://docs.seattlerb.org/rake/)
    ```
    $ gem install rake
    ```
    * Install bundler (Sudo may be necessary)
    ```
    $ gem install bundler
    ```

2. Sauce Credentials
    * In the terminal export your Sauce Labs Credentials as environmental variables:
    ```
    $ export SAUCE_USERNAME=<your Sauce Labs username>
	$ export SAUCE_ACCESS_KEY=<your Sauce Labs access key>
    ```
    If you don't do this, the Rakefile will complain.

3. Project Dependencies
	* Install packages (Use sudo if necessary)
	```
	$ bundle install
	```
    * Set Build ID (Optional)
    ```
    $ export BUILD_TAG=sauce_automated_build_name
    ```


## Running Tests

1. Run RSpec specs on Sauce in Parallel:
	```
	$ bundle exec rake test_rspec
	```

2. Run Cucumber Features on Sauce in Parallel:
	```
	$ bundle exec rake clean test_cucumber
	```

3. Execute Tests on Sauce in Parallel using an environment variable:
	```
	$ TEST_RUNNER=rspec bundle exec rake
	```

View the results on your [Sauce Labs Dashboard](https://saucelabs.com/beta/dashboard/)


### Contributing

This project is open source! 
The maintainers welcome the community to [submit an issue](http://notimplementedyet.com/issues#new) with ideas or bug reports, 
and [making pull requests](http://notimplementedyet.com/pulls#new) with bug fixes and suggested code improvements


## License

This project is available under the terms of the [MIT License](http://opensource.org/licenses/MIT).


## Additional Resources
##### [Sauce Labs Documentation](https://wiki.saucelabs.com/)

##### [Watir Documentation](http://watir.github.io/docs/home)

##### [SeleniumHQ Documentation](http://www.seleniumhq.org/docs/)

##### [RSpec Documentation](http://rspec.info/documentation/)

##### [Cucumber Documentation](https://cucumber.io/docs/)

##### [Applitools Documentation](https://applitools.com/resources/#Documentation/)

#### [Watir Drops Documentation](https://github.com/titusfortner/watir_drops#readme)

#### [Watir Model Documentation](https://github.com/titusfortner/watir_model#readme)

#### [Page Object Documentation](https://github.com/cheezy/page-object#readme)

#### [Data Magic Documentation](https://github.com/cheezy/data_magic#readme)

##### [Ruby Documentation](http://ruby-doc.org/)

##### [Stack Overflow](http://stackoverflow.com/)
* A great resource to search for issues not explicitly covered by documentation.

#### [Alternate Example Project](https://github.com/djangofan/watir-cuke-starter)


