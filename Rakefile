require 'rake'
require 'rake/testtask'
require 'rake/clean'

begin
	require 'jeweler'
	Jeweler::Tasks.new do |gemspec|
		gemspec.name = "fluent"
		gemspec.summary = "Fluent event collector"
		gemspec.author = "Sadayuki Furuhashi"
		gemspec.email = "frsyuki@gmail.com"
		gemspec.homepage = "http://github.com/fluent"
		gemspec.has_rdoc = false
		gemspec.require_paths = ["lib"]
		gemspec.add_dependency "msgpack", ">= 0.4.4"
		gemspec.add_dependency "json", ">= 1.4.3"
		gemspec.add_dependency "rack", ">= 1.2.1"
		#gemspec.test_files = Dir["test/**/*.rb"]
		gemspec.files = Dir["lib/**/*", "test/**/*.rb"]
		gemspec.executables = ['fluentd', 'fluent-cat']
	end
	Jeweler::GemcutterTasks.new
rescue LoadError
	puts "Jeweler not available. Install it with: gem install jeweler"
end

VERSION_FILE = "lib/fluent/version.rb"

file VERSION_FILE => ["VERSION"] do |t|
	version = File.read("VERSION").strip
	File.open(VERSION_FILE, "w") {|f|
		f.write <<EOF
module Fluent

VERSION = '#{version}'

end
EOF
	}
end

task :default => [VERSION_FILE, :build]
