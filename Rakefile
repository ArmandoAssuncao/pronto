#!/usr/bin/env rake
require 'bundler'
require 'pronto/rake/travis_pull_request'

Bundler::GemHelper.install_tasks

desc 'Bundle the gem'
task :bundle do
  sh 'bundle install'
  sh 'gem build *.gemspec'
  sh 'gem install *.gem'
  sh 'rm *.gem'
end

task :spec do
  sh 'bundle exec rspec'
end

travis_pull_request = Pronto::Rake::TravisPullRequest.new

task(:default).clear
task default: [:bundle, :spec, travis_pull_request]
