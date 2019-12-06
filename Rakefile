# frozen_string_literal: true

require "rake/testtask"

task :default => :test

Rake::TestTask.new do |t|
  t.libs << "test"
  t.test_files = FileList["test/*_test.rb"]
end

namespace :db do
  desc %(Generate Emoji data files needed for development)
  task :generate => [
      "vendor/unicode-negarmoji-test.txt"
  ]

  desc %(Dump a list of supported Emoji with Unicode descriptions and aliases)
  task :dump => :generate do
    system "ruby", "-Ilib", "db/dump.rb"
  end
end

file "vendor/unicode-emoji-test.txt" do |t|
  system "curl", "-fsSL", "http://unicode.org/Public/emoji/12.1/emoji-test.txt", "-o", t.name
end
