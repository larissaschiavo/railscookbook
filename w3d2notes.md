W3D5
Metaprogramming/Reflection
-Reflection: the ability for a program to examine itself (aka introspection)
-Object#methods returns an array of symbols compatible w/ the object
Send
[].send(:count) # => 0
-Call a method by name
-Can also use send like this:
 def do_three_times(object, method_name)   3.times { object.send(method_name) } end class Dog   def bark     puts "Woof"   end end dog = Dog.new do_three_times(dog, :bark)

Define_method: defines new methods dynamically, eg
class Dog   # defines a class method that will define more methods; this is   # called a **macro**.   def self.makes_sound(name)     define_method(name) { puts "#{name}!" }   end   makes_sound(:woof)   makes_sound(:bark)   makes_sound(:grr) end dog = Dog.new dog.woof dog.bark dog.grr
-The code inside the Dog class runs when Ruby defines the Dog class. Makes_sound gets called when classes are defined, not when a new Dog object is made
-makes_sound sets up an instance method shared by all Dog objects, not instance specific

Other Macros:
Attr_accessor: defines getter/setter methods for a given instance var name
belongs_to/has_many: defines a method to get SQL query to get associated objects

Object#method_missing
-Ruby calls this if it can’t find a given method.
-Passes method name as a symbol and arguments
-default version raises exception about missing method, but you can change it, eg
class T   def method_missing(*args)     p args   end End

Method_missing can change it so any method w. A prefix will run:
class Cat   def say(anything)     puts anything   end   def method_missing(method_name)     method_name = method_name.to_s     if method_name.start_with?("say_")       text = method_name[("say_".length)..-1]       say(text)     else       # do the usual thing when a method is missing (i.e., raise an       # error)       super     end   end end
Dynamic finders:
-Can be verbose/not preferable, You can override #method_missing in ActiveRecord::Base to work for #find_by* methods: parse the column names w/ given args., eg:
class ActiveRecord::Base   def method_missing(method_name, *args)     method_name = method_name.to_s     if method_name.start_with?("find_by_")       # attributes_string is, e.g., "first_name_and_last_name"       attributes_string = method_name[("find_by_".length)..-1]       # attribute_names is, e.g., ["first_name", "last_name"]       attribute_names = attributes_string.split("_and_")       unless attribute_names.length == args.length         raise "unexpected # of arguments"       end       search_conditions = {}       attribute_names.length.times do |i|         search_conditions[attribute_names[i]] = args[i]       end       # Imagine search takes a hash of search conditions and finds       # objects with the given properties.       self.search(search_conditions)     else       # complain about the missing method       super     end   end end

Object#class:
-Can find class information at runtime (introspection): "who am i".class # => String "who am i".is_a?(String) # => true
-using Object#class helps make code more flexible, eg run a different way if an argument is a hash instead of an array, etc



Class Instance Variables - self.all
-Can make an instance variable of the whole class object instead of just an instance of it
class Dog   def self.all     @dogs ||= []   end   def initialize(name)     @name = name       self.class.all << self   end End

Inheritance @@
-Class instance variables don’t work well with inheritance, the all method would look in parent class of a class instance variable for an instance variable and be unable to use it b/c the two are different objects
-Can fix this with @@var_name - class variable
-Shared between super and sub classes
-Most classes we write won’t be inherited from; usually stick with @

Global Variables - $
-Global variables are top-level variables that live outside any class, accessible from anywhere
-prefix w/ $
-Global variables are not very common, they are not very object oriented since they live outside any class
-Rare exception: when a piece of data needs to be used throughout, eg $stdin and $stdout
-Not very common in Ruby
