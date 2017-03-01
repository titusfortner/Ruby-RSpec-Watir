require 'rspec/core/rake_task'
require 'parallel_cucumber'
require 'rake/clean'

@success = true
CLEAN.include("reports/**/junit*")
CLEAN.include("reports/**/TEST*.xml")
CLEAN.include("reports/**/*.html")
CLEAN.include("*.log")

# Cucumber and RSpec can not be run at the same time
# The default task uses the runner based on the setting of ENV['TEST_RUNNER']
task :default do
	ENV['BUILD_TAG'] += "-#{ENV['TEST_RUNNER']}" if ENV['BUILD_TAG']
	Rake::MultiTask[:test_all].invoke
end

task :test_rspec do
	ENV['TEST_RUNNER'] = 'rspec'
	Rake::MultiTask[:test_all].invoke
end

task :test_cucumber do
	ENV['TEST_RUNNER'] = 'cucumber'
	Rake::MultiTask[:test_all].invoke
end

task :run_rspec do
	FileUtils.mkpath(ENV['JUNIT_DIR'])
	Rake::Task["grid_global_vars"].execute
	begin
		@result = system "parallel_split_test spec --format d --out #{ENV['JUNIT_DIR']}.xml"
	ensure
		@success &= @result
	end
end

task :run_cucumber do
	FileUtils.mkpath(ENV['JUNIT_DIR'])
	Rake::Task["grid_global_vars"].execute
	begin
		@result = system "parallel_cucumber features -o \"--format pretty --profile parallel_reports\" -n 20"
	ensure
		@success &= @result
	end
end

multitask :test_all => [
		:windows_10_edge_14,
		:windows_10_firefox_49,
		:windows_7_ie_11,
		:os_x_10_11_safari_10,
		:os_x_10_10_chrome_54,
] do
	raise StandardError, "Tests failed!" unless @success
end

task :windows_10_edge_14 do
	ENV['platform'] = 'Windows 10'
	ENV['browserName'] = 'MicrosoftEdge'
	ENV['version'] = '14.14393'
	ENV['JUNIT_DIR'] = 'junit_reports/windows_10_edge_14'

	Rake::Task["run_#{ENV['TEST_RUNNER']}"].execute
end

task :windows_10_firefox_49 do
	ENV['platform'] = 'Windows 10'
	ENV['browserName'] = 'firefox'
	ENV['version'] = '49.0'
	ENV['JUNIT_DIR'] = 'junit_reports/windows_10_firefox_49'

	Rake::Task["run_#{ENV['TEST_RUNNER']}"].execute
end

task :windows_7_ie_11 do
	ENV['platform'] = 'Windows 7'
	ENV['browserName'] = 'internet Explorer'
	ENV['version'] = '11.0'
	ENV['JUNIT_DIR'] = 'junit_reports/windows_7_ie_11'

	Rake::Task["run_#{ENV['TEST_RUNNER']}"].execute
end

task :os_x_10_11_safari_10 do
	ENV['platform'] = 'OS X 10.11'
	ENV['browserName'] = 'safari'
	ENV['version'] = '10.0'
	ENV['JUNIT_DIR'] = 'junit_reports/os_x_10_11_safari_10'

	Rake::Task["run_#{ENV['TEST_RUNNER']}"].execute
end

task :os_x_10_10_chrome_54 do
	ENV['platform'] = 'OS X 10.10'
	ENV['browserName'] = 'chrome'
	ENV['version'] = '54.0'
	ENV['JUNIT_DIR'] = 'junit_reports/os_x_10_10_chrome_54'

	Rake::Task["run_#{ENV['TEST_RUNNER']}"].execute
end

task :grid_global_vars do
  #ENV['APPLITOOLS_ACCESS_KEY'] = 'key'
  #ENV['SAUCE_THREAD_COUNT'] = '10'
  #ENV['SAUCE_PARENT_ACCOUNT'] = 'sauce_acct_name'
  #ENV['SAUCE_TUNNEL_ID'] = 'foo-tunnel'
  #ENV['SAUCE_USERNAME'] = 'bar-user'
  #ENV['SAUCE_ACCESS_KEY'] = 'key'
  Rake::Task["check_missing_vars"].execute
end

task :check_missing_vars do
  variables = %w{SAUCE_USERNAME SAUCE_ACCESS_KEY}
  missing = variables.find_all { |v| ENV[v] == nil }
  unless missing.empty?
    raise "\n  The following variables are missing and are needed to run this script: #{missing.join(', ')}.\n\n"
  end
end
