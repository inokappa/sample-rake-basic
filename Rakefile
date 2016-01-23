require 'rake/clean'
LOGIN_FILE = "login.txt"
CLEAN << "#{LOGIN_FILE}"

verbose(false)

task "default" => "show_version"

namespace :aws do
  desc "Create repository"
  task :create_repo do
    sh "aws --region #{ENV['AWS_REGION']} ecr create-repository --repository-name #{ENV['REPO_NAME']}"
  end

  desc "Get login infomation"
  task :get_login do
    puts "Get login infomation"
    sh "aws --region #{ENV['AWS_REGION']} ecr get-login > #{LOGIN_FILE}" 
  end

  desc "Describe repositories"
  task :describe_repos do
    sh "aws --region #{ENV['AWS_REGION']} ecr describe-repositories"
  end

end

namespace :docker do
  desc "Build image"
  task :build do
    sh "docker build --no-cache=true -t #{ENV['IMAGE_NAME']} ."
  end

  desc "Login Repository"
  task :login => 'aws:get_login' do
    sh "sh #{LOGIN_FILE}"
    Rake::Task[:clean].execute
  end

  desc "Add tag"
  task :tag do
    sh "docker tag #{ENV['IMAGE_NAME']} #{ENV['REPO_NAME']}"
  end

  desc "Push image"
  task :push do
    sh "docker push #{ENV['REPO_NAME']}"
  end
end

namespace :compose do
  desc "Compose up with (-d) option."
  task :up do
    sh "/usr/local/bin/docker-compose up -d"
  end

  desc "Compose stop"
  task :stop do
    sh "/usr/local/bin/docker-compose stop"
  end

  desc "Compose remove"
  task :rm do
    sh "/usr/local/bin/docker-compose rm -f"
  end

  desc "Compose ps"
  task :ps do
    sh "/usr/local/bin/docker-compose ps"
  end

end
