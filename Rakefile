require 'watchr'
require 'yaml'
require 'uglifier'
require 'yaml'

def yml_load
	YAML.load(File.read('asset-master.yml'))
end

def join_files out_file_path, file_paths
	File.delete(out_file_path) if File.exist?(out_file_path)

	out_file = File.new(out_file_path, 'w')
	file_paths.each do |file_path|
		out_file.write(File.read(file_path))
		out_file.write("\n")
	end
	out_file.close
end

def uglify source_file, dest_file, delete_source = true
		uglified_file = File.new(dest_file, 'w')
		uglified_file.write(Uglifier.new.compile(File.read(source_file)))
		File.delete(source_file) if delete_source
end

task :watch do
	system 'watchr watchr_script'
end

task :compile_js do
	puts "Compiling js files...."
	yml = yml_load

	yml['js'].each do |file_group, files|
		output_file_path = "_assets/js/#{file_group}"
		tmp_file_path = "#{output_file_path}.tmp"

		file_names = files.collect do |file|
			File.join(File.dirname(File.expand_path(__FILE__)), "javascript/#{file}")
		end

		join_files tmp_file_path, file_names
		uglify tmp_file_path, output_file_path
		puts "#{output_file_path} compiled."
	end
end

task :compile_scss do
	puts "Compiling scss files...."
	system 'compass compile'
end