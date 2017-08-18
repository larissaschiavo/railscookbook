# W3D2

**Creating a New Rails Project**

**Step 1:** confirm Rails is installed: gem install rails -v &#39;5.1.2&#39;

**Step 2:** Generate a new Rails project (this makes new folder, uses Postgres) rails new demo\_project --database=postgresql

**Step 3:** Add these to Gemfile (under development group) group :developmentdo
  # Run &#39;bundle exec annotate&#39; in Terminal to add helpful comments to models.
  gem&#39;annotate&#39;
  # These two give you a great error handling page.
  # But make sure to never use them in production!
  gem&#39;better\_errors&#39;
  gem&#39;binding\_of\_caller&#39;
  gem&#39;byebug&#39;
  gem&#39;pry-rails&#39;
end

**Step 4:** In Terminal, navigate to the project folder, run bundle install

**Switch from SQLite to Postgres:**

**Step 1:** Delete .sqlite3 files in db/

**Step 2:** In Gemfile, replace gem &#39;sqlite3&#39; with gem &#39;pg&#39;

**Step 3:** run bundle install in terminal

**Step 4:** go to config/database.yml , change default environment to

default: &amp;default
  adapter: postgresql
  pool: 5
  timeout: 5000

**Step 5:**  Make a new database, name it like this:

development:
  &lt;&lt;: \*default
  database: project\_name\_development

**Step 6:**  ** **** bundle exec rails db:create**

**Step 7:** if there are migrations: bundle exec rails db:migrate

**Step 8:** if there are seeds: bundle exec rails db:seed

**Migrations:**

Migration: a file of Ruby code that describes changes applied to a database.

-Can create or drop tables

- Can add/remove columns from a table

-Each new batch of changes to a DB is written to a new migration file, which goes to repository

-ActiveRecord can handle migrations

-A migration is an extension of ActiveRecord::Migration class

**Generate Migrations**

        1.        In Terminal: $ rails generate migration AddPartNumberToProducts

        2.        Go into db/migrate directory in the project folder; each migration class has its own file

        3.        The name of the migration file (not in CamelCase) should match the second half of the filename

        4.        This makes a migration like this:

        5.        classAddPartNumberToProducts &lt; ActiveRecord::Migration[5.1]
  defchange
  end
end

**Use the change method**

        1.        Usually, will be one of the first things you add to a class, so set it up early:

        2.        classCreateProducts &lt; ActiveRecord::Migration[5.1]
  defchange
    create\_table :productsdo |t|
      t.string :name
      t.text :description
      t.timestamps
    end
  end
End

**Create\_table Migration Method**
