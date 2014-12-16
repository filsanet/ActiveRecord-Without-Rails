# Install this bundle with the --without [windows|unix] option to avoid loading unnecessary gems

source "https://rubygems.org"

# Accommodate different AR versions - 3.2 for Windows/Java 6, and 4.1 for *nix
gem "activerecord", ">=3.2.13", "<=4.1"

# Use this set of gems for MS SQL
# BEGIN MS SQL gems
platforms :jruby do 
  gem 'activerecord-jdbc-adapter', '1.2.2.1'
  gem 'activerecord-jdbcmssql-adapter', '1.2.2.1'
  gem 'jdbc-jtds', '1.2.5'
end
# END MS SQL gems

# Use this set of gems for *NIX based RDBMSes
# BEGIN *NIX SQL gems
platforms :ruby do
  gem 'sqlite3'

  # Or you can use Postgres
  # gem "pg"
  # END *NIX SQL gems
end

gem "rspec"

