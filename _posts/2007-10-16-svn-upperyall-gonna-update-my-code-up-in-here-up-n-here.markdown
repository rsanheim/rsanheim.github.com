--- 
wordpress_id: 341
layout: post
title: Yall gonna go update some code, up in here, up 'n here!"
wordpress_url: http://robsanheim.com/2007/10/16/svn-upperyall-gonna-update-my-code-up-in-here-up-n-here/
---
A stupid script to update all projects within a directory.  This could be massively improved.

[ruby]
#!/usr/bin/env ruby

# Simple script to svn up all directories within the current directory, or the
# specified directory.  Does not recurse, assumes we only need to go to the 
# immediate directories.
# ex: > cd my_projects; upper    # svn up all projects w/i my_projects
# ex: > upper ~/src/work/        # svn up all projects inside ~/src/work
class Upper
  
  def self.svn_up(top_level_dir)
    puts "Svn upping all projects within '#{top_level_dir}'"
    full_path = File.expand_path(top_level_dir)
    directories = []
    Dir.open(full_path).each do |dir|
      if (dir == "." || dir == ".." || dir == ".DS_store") then next end
      full_dir = File.join(full_path, dir)
      directories << dir if File.directory?(full_dir)
    end
    puts "No directories found." if directories.empty?
    directories.each do |dir|
      command = "svn up #{dir}"
      puts command
      puts `#{command}`
    end
  end
  
end

dir = ARGV[0] || Dir.pwd

unless File.directory?(dir.to_s)
  puts "Error - No directory exists with name: '#{dir}'" and exit 
end

Upper.svn_up(dir)
[/ruby]
