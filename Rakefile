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