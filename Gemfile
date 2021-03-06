source "http://rubygems.org"

gemspec

if ENV['AREL']
  gem "arel", :path => ENV['AREL']
else
  gem "arel", :git => "git://github.com/rails/arel"
end

gem "bcrypt-ruby", "~> 3.0.0"
gem "jquery-rails"

if ENV['JOURNEY']
  gem "journey", :path => ENV['JOURNEY']
else
  gem "journey", :git => "git://github.com/rails/journey"
end

# This needs to be with require false to avoid
# it being automatically loaded by sprockets
gem "uglifier", ">= 1.0.3", :require => false

gem "rake", ">= 0.8.7"
gem "mocha", ">= 0.9.8"

group :doc do
  gem "rdoc",  "~> 3.4"
  gem "sdoc",  "~> 0.3"
  gem "RedCloth", "~> 4.2" if RUBY_VERSION < "1.9.3"
  gem "w3c_validators"
end

# AS
gem "memcache-client", ">= 1.8.5"

platforms :mri_18 do
  gem "system_timer"
  gem "json"
end

# Add your own local bundler stuff
instance_eval File.read ".Gemfile" if File.exists? ".Gemfile"

platforms :mri do
  group :test do
    gem "ruby-prof" if RUBY_VERSION < "1.9.3"
  end
end

platforms :ruby do
  if ENV["RB_FSEVENT"]
    gem "rb-fsevent"
  end
  gem "json"
  gem "yajl-ruby"
  gem "nokogiri", ">= 1.4.5"

  # AR
  gem "sqlite3", "~> 1.3.5"

  group :db do
    gem "pg", ">= 0.11.0"
    gem "mysql", ">= 2.8.1"
    gem "mysql2", ">= 0.3.10"
  end
end

platforms :jruby do
  gem "json"
  gem "activerecord-jdbcsqlite3-adapter", ">= 1.2.0"

  # This is needed by now to let tests work on JRuby
  # TODO: When the JRuby guys merge jruby-openssl in
  # jruby this will be removed
  gem "jruby-openssl"

  group :db do
    gem "activerecord-jdbcmysql-adapter", ">= 1.2.0"
    gem "activerecord-jdbcpostgresql-adapter", ">= 1.2.0"
  end
end

# gems that are necessary for ActiveRecord tests with Oracle database
if ENV['ORACLE_ENHANCED_PATH'] || ENV['ORACLE_ENHANCED']
  platforms :ruby do
    gem "ruby-oci8", ">= 2.0.4"
  end
  if ENV['ORACLE_ENHANCED_PATH']
    gem "activerecord-oracle_enhanced-adapter", :path => ENV['ORACLE_ENHANCED_PATH']
  else
    gem "activerecord-oracle_enhanced-adapter", :git => "git://github.com/rsim/oracle-enhanced.git"
  end
end

# A gem necessary for ActiveRecord tests with IBM DB
gem "ibm_db" if ENV['IBM_DB']
