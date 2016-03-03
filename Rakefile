task :default => [:stats]


def today_in_dirs
  today = Time.now.strftime("%Y.%b.%d").split('.').map(&:downcase)
  "#{today[0]}/#{today[1]}/#{today[2]}"
end

def ensure_todays_directory
  `mkdir -p writing/#{today_in_dirs}`
  puts "* Ensure directory writing/#{today_in_dirs} exists"
end

def accept_arguments
  ARGV.each { |a| task a.to_sym do ; end }
end

def create_file(filename)
  ensure_todays_directory
  `touch writing/#{today_in_dirs}/#{filename}.markdown`
  puts "* Created writing/#{today_in_dirs}/#{filename}.markdown"
end

desc "make a new notes file for today"
task :today do
  create_file("notes")
end

desc "make a new file in today's folder. Usage: `rake newfile filename` #=> creates filename.markdown in today's directory"
task :newfile do
  accept_arguments
  filename = ARGV[1]

  create_file(filename)
end


desc "count words each day, get an average"
task :stats do
  words = {}
  list = Dir["writing/*/*/*"]
  list.each{|d| print "Words for #{d}: "; n = `cat #{d}/* | wc -w`.split.map(&:to_i).inject(:+); puts n; words[d] = n}
  puts '', "Average words/day: #{words.values.inject(:+) / words.values.count}"
end


