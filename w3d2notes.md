p.p1 {margin: 0.0px 0.0px 0.0px 0.0px; line-height: 33.0px; font: 24.0px Arial; color: #000000; -webkit-text-stroke: #000000; background-color: #ffffff}
p.p2 {margin: 0.0px 0.0px 0.0px 0.0px; line-height: 14.0px; font: 12.0px Times; color: #000000; -webkit-text-stroke: #000000; background-color: #ffffff; min-height: 14.0px}
p.p3 {margin: 0.0px 0.0px 0.0px 0.0px; line-height: 20.0px; font: 14.7px Arial; color: #000000; -webkit-text-stroke: #000000; background-color: #ffffff}
p.p4 {margin: 0.0px 0.0px 0.0px 0.0px; line-height: 18.0px; font: 13.3px Times; color: #6a737d; -webkit-text-stroke: #6a737d; background-color: #f6f8fa}
p.p5 {margin: 0.0px 0.0px 0.0px 0.0px; line-height: 20.0px; font: 14.7px Arial; color: #24292e; -webkit-text-stroke: #24292e; background-color: #ffffff}
p.p6 {margin: 0.0px 0.0px 0.0px 0.0px; line-height: 22.0px; font: 16.0px Arial; color: #24292e; -webkit-text-stroke: #24292e; background-color: #ffffff}
p.p7 {margin: 0.0px 0.0px 0.0px 0.0px; line-height: 18.0px; font: 13.3px Times; color: #22863a; -webkit-text-stroke: #22863a; background-color: #f6f8fa}
p.p8 {margin: 0.0px 0.0px 0.0px 0.0px; line-height: 18.0px; font: 13.3px Times; color: #032f62; -webkit-text-stroke: #032f62; background-color: #f6f8fa}
p.p9 {margin: 0.0px 0.0px 0.0px 0.0px; line-height: 18.0px; font: 13.3px Times; color: #24292e; -webkit-text-stroke: #24292e; background-color: #ffffff}
p.p10 {margin: 0.0px 0.0px 0.0px 36.0px; text-indent: -36.0px; line-height: 20.0px; font: 13.3px Times; color: #24292e; -webkit-text-stroke: #24292e; background-color: #f6f8fa}
p.p11 {margin: 0.0px 0.0px 0.0px 36.0px; text-indent: -36.0px; line-height: 20.0px; font: 14.7px Arial; color: #24292e; -webkit-text-stroke: #24292e; background-color: #ffffff}
p.p12 {margin: 0.0px 0.0px 0.0px 36.0px; text-indent: -36.0px; line-height: 20.0px; font: 13.3px Times; color: #6f42c1; -webkit-text-stroke: #6f42c1; background-color: #f6f8fa}
p.p13 {margin: 0.0px 0.0px 0.0px 36.0px; text-indent: -36.0px; line-height: 23.0px; font: 13.3px Times; color: #24292e; -webkit-text-stroke: #24292e; background-color: #f6f8fa}
p.p14 {margin: 0.0px 0.0px 0.0px 0.0px; line-height: 25.0px; font: 14.7px Arial; color: #000000; -webkit-text-stroke: #000000; background-color: #ffffff}
span.s1 {text-decoration: underline ; font-kerning: none}
span.s2 {font-kerning: none}
span.s3 {font: 13.3px Times; font-kerning: none; color: #24292e; background-color: #f6f8fa; -webkit-text-stroke: 0px #24292e}
span.s4 {font: 13.3px Times; font-kerning: none; color: #032f62; background-color: #f6f8fa; -webkit-text-stroke: 0px #032f62}
span.s5 {font: 14.7px Arial; font-kerning: none; color: #000000; background-color: #ffffff; -webkit-text-stroke: 0px #000000}
span.s6 {font-kerning: none; color: #24292e; -webkit-text-stroke: 0px #24292e}
span.s7 {font-kerning: none; color: #005cc5; -webkit-text-stroke: 0px #005cc5}
span.s8 {font-kerning: none; color: #d73a49; -webkit-text-stroke: 0px #d73a49}
span.s9 {font-kerning: none; color: #24292e; background-color: #ffffff; -webkit-text-stroke: 0px #24292e}
span.s10 {font-kerning: none; color: #032f62; -webkit-text-stroke: 0px #032f62}
span.s11 {font: 13.3px Times; font-kerning: none; color: #24292e; -webkit-text-stroke: 0px #24292e}
span.s12 {font: 13.3px Times; font-kerning: none}
span.s13 {font: 14.7px Arial; font-kerning: none}
span.s14 {font-kerning: none; color: #22863a; -webkit-text-stroke: 0px #22863a}
span.s15 {font: 16.0px Arial; font-kerning: none}
span.s16 {font: 14.7px Arial; font-kerning: none; background-color: #ffffff}
span.s17 {font: 14.7px Arial; font-kerning: none; color: #24292e; background-color: #ffffff}
span.s18 {font: 14.7px Arial; font-kerning: none; color: #24292e; background-color: #ffffff; -webkit-text-stroke: 0px #24292e}
span.s19 {font-kerning: none; color: #d73a49; -webkit-text-stroke: 0px #6f42c1}
span.s20 {font-kerning: none; color: #6f42c1; -webkit-text-stroke: 0px #6f42c1}
span.s21 {font-kerning: none; background-color: #ffffff}
span.Apple-tab-span {white-space:pre}

**W3D2**

**Creating a New Rails Project**

**Step 1: **confirm Rails is installed: gem install rails -v '5.1.2'

**Step 2: **Generate a new Rails project (this makes new folder, uses Postgres) rails new demo_project --database=postgresql

**Step 3: **Add these to Gemfile (under development group) group :developmentdo  # Run 'bundle exec annotate' in Terminal to add helpful comments to models.  gem'annotate'  # These two give you a great error handling page.  # But make sure to never use them in production!  gem'better_errors'  gem'binding_of_caller'  gem'byebug'  gem'pry-rails'end

**Step 4: **In Terminal, navigate to the project folder, run bundle install

**Switch from SQLite to Postgres: **

**Step 1: **Delete .sqlite3 files in db/

**Step 2: **In Gemfile, replace gem 'sqlite3' with gem 'pg'

**Step 3: **run bundle install in terminal 

**Step 4: **go to config/database.yml , change default environment to 

default: &default  adapter: postgresql  pool: 5  timeout: 5000

**Step 5: ** Make a new database, name it like this: 

development:  &lt;&lt;: *default  database: project_name_development

**Step 6:  ****bundle exec rails db:create**

**Step 7: **if there are migrations: bundle exec rails db:migrate

**Step 8: **if there are seeds: bundle exec rails db:seed

**Migrations: **

Migration: a file of Ruby code that describes changes applied to a database. 

-Can create or drop tables 

- Can add/remove columns from a table

-Each new batch of changes to a DB is written to a new migration file, which goes to repository

-ActiveRecord can handle migrations 

-A migration is an extension of ActiveRecord::Migration class 

**Generate Migrations**

1.In Terminal: $ rails generate migration AddPartNumberToProducts

2.Go into db/migrate directory in the project folder; each migration class has its own file  

3.The name of the migration file (not in CamelCase) should match the second half of the filename  

4.This makes a migration like this:  

5.classAddPartNumberToProducts &lt; ActiveRecord::Migration[5.1]  defchange  endend

**Use the change method **

1.Usually, will be one of the first things you add to a class, so set it up early:  

2.classCreateProducts &lt; ActiveRecord::Migration[5.1]  defchange    create_table :productsdo |t|      t.string :name      t.text :description      t.timestamps    end  endEnd

**Create_table Migration Method**
