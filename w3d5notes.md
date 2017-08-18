# W3D5

Metaprogramming/Reflection

-Reflection: the ability for a program to examine itself (aka introspection)

-Object#methods returns an array of symbols compatible w/ the object

**Send**

[].send(:count) # =&gt; 0

-Call a method by name

-Can also use send like this:

 defdo\_three\_times(object, method\_name)
  3.times { object.send(method\_name) }
end
classDog
  defbark
    puts &quot;Woof&quot;
  end
end
dog =Dog.new
do\_three\_times(dog, :bark)

**Define\_method:** defines new methods dynamically, eg

classDog
  # defines a class method that will define more methods; this is
  # called a \*\*macro\*\*.
  defself.makes\_sound(name)
    define\_method(name) { puts &quot;#{name}!&quot; }
  end
  makes\_sound(:woof)
  makes\_sound(:bark)
  makes\_sound(:grr)
end
dog =Dog.new
dog.woof
dog.bark
dog.grr

-The code inside the Dog class runs when Ruby defines the Dog class. Makes\_sound gets called when classes are defined, not when a new Dog object is made

-makes\_sound sets up an instance method shared by all Dog objects, not instance specific

Other Macros:

**Attr\_accessor:** defines getter/setter methods for a given instance var name

**belongs\_to/has\_many:** defines a method to get SQL query to get associated objects

**Object#method\_missing**

-Ruby calls this if it can&#39;t find a given method.

-Passes method name as a symbol and arguments

-default version raises exception about missing method, but you can change it, eg

classT
  defmethod\_missing(\*args)
    p args
  end
End

Method\_missing can change it so any method w. A prefix will run:

classCat
  defsay(anything)
    puts anything
  end
  defmethod\_missing(method\_name)
    method\_name = method\_name.to\_s
    if method\_name.start\_with?(&quot;say\_&quot;)
      text = method\_name[(&quot;say\_&quot;.length)..-1]
      say(text)
    else
      # do the usual thing when a method is missing (i.e., raise an
      # error)
      super
    end
  end
end

**Dynamic finders:**

-Can be verbose/not preferable, You can override #method\_missing in ActiveRecord::Base to work for #find\_by\* methods: parse the column names w/ given args., eg:

classActiveRecord::Base
  defmethod\_missing(method\_name, \*args)
    method\_name = method\_name.to\_s
    if method\_name.start\_with?(&quot;find\_by\_&quot;)
      # attributes\_string is, e.g., &quot;first\_name\_and\_last\_name&quot;
      attributes\_string = method\_name[(&quot;find\_by\_&quot;.length)..-1]
      # attribute\_names is, e.g., [&quot;first\_name&quot;, &quot;last\_name&quot;]
      attribute\_names = attributes\_string.split(&quot;\_and\_&quot;)
      unless attribute\_names.length == args.length
        raise&quot;unexpected # of arguments&quot;
      end
      search\_conditions = {}
      attribute\_names.length.times do |i|
        search\_conditions[attribute\_names[i]] = args[i]
      end
      # Imagine search takes a hash of search conditions and finds
      # objects with the given properties.
      self.search(search\_conditions)
    else
      # complain about the missing method
      super
    end
  end
end

**Object#class:**

-Can find class information at runtime (introspection): &quot;who am i&quot;.class # =&gt; String
&quot;who am i&quot;.is\_a?(String) # =&gt; true

-using Object#class helps make code more flexible, eg run a different way if an argument is a hash instead of an array, etc

# Class Instance Variables - self.all

-Can make an instance variable of the whole class object instead of just an instance of it

classDog
  defself.all
    @dogs ||= []
  end
  definitialize(name)
    @name = name
    self.class.all &lt;&lt;self
  end
End

# Inheritance @@

-Class instance variables don&#39;t work well with inheritance, the all method would look in parent class of a class instance variable for an instance variable and be unable to use it b/c the two are different objects

-Can fix this with **@@var\_name - class variable**

-Shared between super and sub classes

-Most classes we write won&#39;t be inherited from; usually stick with @

# Global Variables - $

-Global variables are top-level variables that live outside any class, accessible from anywhere

-prefix w/ $

-Global variables are not very common, they are not very object oriented since they live outside any class

-Rare exception: when a piece of data needs to be used throughout, eg $stdin and $stdout

-Not very common in Ruby
