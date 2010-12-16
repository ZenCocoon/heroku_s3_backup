require 'rubygems'
require 'rake'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "heroku_s3_backup"
    gem.summary = %Q{Gem to backup your database from Heroku to S3. Fork uses the fog gem}
    gem.description = %Q{http://trevorturk.com/2010/04/14/automated-heroku-backups/ My fork replaces right_aws/aws-s3 with the fog gem}
    gem.email = "jack@jackchu.com"
    gem.homepage = "http://github.com/kamui/heroku_s3_backup"
    gem.authors = ["Eric Davis", "Trevor Turk", "Jesse Storimer", "Jack Chu"]
    gem.add_development_dependency "thoughtbot-shoulda", ">= 0"
    gem.add_dependency('fog', '~> 0.3')
    gem.files =  FileList[
                          "[A-Z]*",
                          "init.rb",
                          "rails/init.rb",
                          "{bin,generators,lib,test,app}/**/*",
                          'lib/jeweler/templates/.gitignore'
                         ]
    # gem is a Gem::Specification... see http://www.rubygems.org/read/chapter/20 for additional settings
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end

require 'rake/testtask'
Rake::TestTask.new(:test) do |test|
  test.libs << 'lib' << 'test'
  test.pattern = 'test/**/test_*.rb'
  test.verbose = true
end

begin
  require 'rcov/rcovtask'
  Rcov::RcovTask.new do |test|
    test.libs << 'test'
    test.pattern = 'test/**/test_*.rb'
    test.verbose = true
  end
rescue LoadError
  task :rcov do
    abort "RCov is not available. In order to run rcov, you must: sudo gem install spicycode-rcov"
  end
end

task :test => :check_dependencies

task :default => :test

require 'rake/rdoctask'
Rake::RDocTask.new do |rdoc|
  version = File.exist?('VERSION') ? File.read('VERSION') : ""

  rdoc.rdoc_dir = 'rdoc'
  rdoc.title = "heroku_s3_backup #{version}"
  rdoc.rdoc_files.include('README*')
  rdoc.rdoc_files.include('lib/**/*.rb')
end
