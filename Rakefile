require 'html-proofer' # Ensures we have the html-proofer library available to use

def run_htmlproofer() # The function that will run the proofer, so that we can re-use it between our two rake tasks
  options = {
    assume_extension: true, # Assumes html file extensions
    :typhoeus => { # The options for the curl library that's used.
      :ssl_verifypeer => false # This will stop you from getting errors when certs can't be parsed, which doesn't matter in this case.
    },
    allow_hash_href: true, # Won't fail for local links
    url_ignore: [/edit\/gh-pages/] # This is because all my pages have a link to edit them, which will fail when generated locally.
  }
  HTMLProofer.check_directory("./_site", options).run # Calls html-proofer and uses the Jektll _site folder
end

task :test do
  sh "bundle exec jekyll build"
  run_htmlproofer()
end

task :testwithoutbuild do # For when I just built the site and I'm doing this a bunch of times
  run_htmlproofer()
end
