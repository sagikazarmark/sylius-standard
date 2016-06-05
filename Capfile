# Override the path before running the setup
set :deploy_path, "etc/deploy"
set :deploy_config_path, fetch(:deploy_path) + "/deploy.rb"
set :stage_config_path, fetch(:deploy_path) + "/stages/"

# Add custom load path `etc/deploy/lib` for custom requirements
lib = File.expand_path(fetch(:deploy_path) + "/lib")
$LOAD_PATH.unshift(lib) unless $LOAD_PATH.include?(lib)

# Load DSL and set up stages
require "capistrano/setup"

# Include default deployment tasks
require "capistrano/deploy"

# Include Symfony specific tasks
require "capistrano/symfony"

# Include NPM tasks to install Node dependencies
require "capistrano/npm"

# Include Bower tasks to install frontend dependencies
require "capistrano/bower"

# Include Gulp tasks to build assets
require "capistrano/gulp"

# List stages
require "capistrano/list_stages"

# Invoke command
require "capistrano/invoke"

# Add custom banner
require "capistrano/banner"

# Load Dotenv-like files
require "capistrano/env-config"

# Help with SSH related problems
require "capistrano/ssh_doctor"

# Include Copy task to speed up dependency installation
require "capistrano/copy_files"

# Load custom tasks from `etc/deploy/tasks` if you have any defined
Dir.glob(fetch(:deploy_path) + "/tasks/**/*.rake").each { |r| import r }
