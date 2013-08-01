require 'rake'
require 'rubygems'
require 'watchr'
require 'yaml'
require 'uglifier'

task :watch do
	system 'watchr watchr_script'
end

task :compilejs do
	tmp_file_path = '_assets/js/tmp_app.js'
	output_file_path = "_assets/js/app.js"
	File.delete(tmp_file_path) if File.exist?(tmp_file_path)
	File.delete(output_file_path) if File.exist?(output_file_path)

	tmp_file = File.new(tmp_file_path, 'w')
	File.open('jsfiles').each do |js_file_path|
		file = File.join(File.dirname(File.expand_path(__FILE__)), js_file_path).gsub(/\n/,'')
		tmp_file.write(File.read(file))
		tmp_file.write("\n")
	end
	tmp_file.close

	uglified_file = File.new(output_file_path, 'w')
	uglified_file.write(Uglifier.new.compile(File.read(tmp_file_path)))

	File.delete(tmp_file_path)
end
