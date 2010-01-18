require 'rubygems'
require 'rake'
require 'fileutils'

begin
  require 'jeweler'
  Jeweler::Tasks.new do |gem|
    gem.name = "zmack-ultraviolet"
    gem.summary = %Q{Ultraviolet is a syntax highlighting library and engine}
    gem.description = <<-DESC
      Ultraviolet is a syntax highlighting library and engine. It
      uses TextMate[http://macromates.com/] syntax files and parses
      them using the Textpow[http://textpow.rubyforge.org] library. It 
      supports more than 60 programming languages out of the box.
    DESC

    gem.email = "dichodaemon@gmail.com"
    gem.homepage = 'http://ultraviolet.rubyforge.org'
    gem.authors = ["Dizan Vasquez"]

    gem.add_dependency "oniguruma", ">= 0"
    gem.add_dependency "textpow", ">= 0.10.0"
  end
  Jeweler::GemcutterTasks.new
rescue LoadError
  puts "Jeweler (or a dependency) not available. Install it with: gem install jeweler"
end

begin
   desc 'Create MaMa documentation'
   task :mama => :clean do
      system "mm -c -t refresh -o manual mm/manual.mm"
   end
   
   desc 'Publish MaMa documentation to RubyForge'
      task :mama_publish => [:clean, :mama] do
      config = YAML.load(File.read(File.expand_path("~/.rubyforge/user-config.yml")))
      host = "#{config["username"]}@rubyforge.org"
      remote_dir = "/var/www/gforge-projects/#{h.rubyforge_name}"
      local_dir = 'manual'
      system "rsync -av --delete #{local_dir}/ #{host}:#{remote_dir}"
   end

rescue LoadError => e
   desc 'Run the test suite.'
   task :test do
      system "ruby -Ibin:lib:test test_#{rubyforge_name}.rb"
   end
end
