# Sample Rails Project Template

This repo is to be used as a template for Rails projects. This includes gems and associated configurations commonly used in most Rails projects.

For additional information on the setup process that this repo was generated by, please see [this gist](https://gist.github.com/ryanflach/9fe657471bc9282a18d6904171645278).

## Usage
* Clone the project with your desired project name
```
git clone git@github.com:ryanflach/rails_project_template.git <your-project-name>
```
* `cd` into the project directory
```
cd <your-project-name>
```
* Create your project on GitHub
```
hub create
```
* Remove the original remote and add your own
```
git remote remove origin
git remote add origin git@github.com:YOUR-GITHUB-USERNAME/<your-project-name>
```
* Bundle
```
bundle
```
* Install Figaro
```
bundle exec figaro install
```
* Update this README

## Additional Common Configuration
Should your project need to work with an external API, you will want to add the following:
* In your `Gemfile`:
  * Available to all environments:
    * `gem 'faraday'` - for making http requests ([docs](https://github.com/lostisland/faraday))
  * Under `group :test`
    * `gem 'vcr'` - for stubbing ([docs](https://github.com/vcr/vcr))
    * `gem 'webmock'` - for mocking (used by VCR)([docs](https://github.com/bblimke/webmock))


* To make these gems available:
```
bundle
```
* Add configuration in `spec/rails_helper.rb`:
```
require 'vcr'
VCR.configure do |config|
  config.cassette_library_dir = "spec/vcr_cassettes"
  config.hook_into :webmock
end
```
* In `.gitignore`, ignore the cassettes that will be made:
```
# Ignore vcr cassettes
/spec/vcr_cassettes
```
