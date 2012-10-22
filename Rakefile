class String
  # Strip leading whitespace from each line that is the same as the 
  # amount of whitespace on the first line of the string.
  # Leaves _additional_ indentation on later lines intact.
  # SEE: http://stackoverflow.com/a/5638187/504018
  def unindent
    gsub /^#{self[/\A\s*/]}/, ''
  end
end

desc "Prepare DevOps Base environment to spin up a project.

This runs librarian-chef to install cookbooks."
task :setup do
  p "Installing cookbooks using Librarian gem..."
  system "librarian-chef install"
end

desc "Prepare DevOps-Base key, value pairs using an encryped data bag key.

This creates a data-bags key, value pair for a specified context under encrypted data bags control. (For example: rake databags mysql"
task :databags do
  require 'rubygems'
  require 'chef/encrypted_data_bag_item'
  
  context = ARGV.last
  puts "A key, value pair has been assigned for the following context: #{context}."
  task context.to_sym do ; end

  secret = Chef::EncryptedDataBagItem.load_secret('data_bag_key')
  data = {"id" => "#{context}", "root" => "context_password"}
  encrypted_data = Chef::EncryptedDataBagItem.encrypt_data_bag_item(data, secret)

  FileUtils.mkpath('data_bags/passwords')
  File.open("data_bags/passwords/#{context}.json", 'w') do |f|
    f.print encrypted_data.to_json
  end
end