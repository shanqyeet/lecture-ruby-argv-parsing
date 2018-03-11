
# ARGV

+++

### What is it?

* ARGV is a convention in programming that goes back to the C language

* it refers to "Argument Vector"

* it's basically a variable that contains arguments that are passed into a program through CLI

+++

### How to use ARGV

* ARGV typically manifests  as an array

**Setup some function to use ARGV**

```ruby 
def print
	puts "I'm gonna say this once"
	puts "The third item is '#{ARGV[2]}'"
end

p print
```

+++

### Then...
**In Command Line**

```
$ ruby 'test.rb' What is ARGV #=> ["What", "is", "ARGV"]
```

**And this is what you get**

```
I'm gonna say this once
The third item is 'ARGV'
```

---

# Parsing Data

+++

### Why we need to parse data?

It's simple, Think about how can you transfer data between programs

+++

### Parsing with plain ruby

```ruby
File.open('test.csv').each do |row|
	puts row.inspect
end 

```

+++

### Parsing with built-in CSV library

```
data = CSV.read('test.csv')

p data #=> see what you get here
```

#### OR

```ruby
require 'csv'

data = []
CSV.foreach('test.csv', headers: true) do |row|
  puts row.inspect
  data << row
end

p data #=> see what you get

```
See what happens when you add 'headers: true' into the CSV parameter

---

# Writing to File

+++

### Writing to file with plain Ruby

```
random = ["one plus one", "three minus one", "four times 2"]
n = 0
until n == 6
	File.open('data.txt','a') do |line|
		line.puts random.sample
	end 
n += 1
end 

```

+++

### Now how can you write to your csv file?

+++

### Here you go

```
require 'csv'

staff = [["name", "age"],["shanq", "30"],["liren","28"],["Nick","young"],["Sheng","old"],["sophie","mystery"]]


CSV.open('test.csv','w') do |x|
	staff.each do |member|
		x << member
	end 
end 
```




