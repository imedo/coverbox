require 'FileUtils'

task :install do
  basedir = File.expand_path('~/.my_git/')
  FileUtils.mkdir_p(basedir)
  sources = ['coverbox.sh', 'coverbox_functions.sh', 'git-wtf.rb', 'bash_prompt.sh'].map{|file| File.expand_path(File.join(File.dirname(__FILE__), file))}
  FileUtils.cp(sources, basedir)

  orig = File.read(File.expand_path('~/.gitconfig')).split("\n")
  conf = File.read(File.expand_path(File.join(File.dirname(__FILE__), 'gitconfig'))).split("\n")
  File.open(File.expand_path('~/.gitconfig'), 'a') do |file|
    conf.each do |line|
      unless orig.include?(line)
        file.puts "[alias]"
        file.puts line
      end
    end
  end
end

task :default => :install
