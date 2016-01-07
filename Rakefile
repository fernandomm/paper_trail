require 'bundler'
Bundler::GemHelper.install_tasks

desc 'Set a relevant database.yml for testing'
task :prepare do
  ENV["DB"] ||= "sqlite"
  FileUtils.cp "test/dummy/config/database.#{ENV["DB"]}.yml", "test/dummy/config/database.yml"
end


require 'rake/testtask'
desc 'Run tests on PaperTrail with Test::Unit.'
Rake::TestTask.new(:test) do |t|
  t.libs << 'lib'
  t.libs << 'test'
  t.pattern = 'test/**/*_test.rb'
  t.verbose = false
end

require 'rspec/core/rake_task'
desc 'Run tests on PaperTrail with RSpec'
RSpec::Core::RakeTask.new(:spec)

require 'rubocop/rake_task'
RuboCop::RakeTask.new

desc 'Default: run all available test suites'
task :default => [:rubocop, :prepare, :test, :spec]
