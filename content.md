# Ruby Gym: Twofer

Twofer or 2-fer is short for two for one. One for you and one for me.

The program should print: 

```
"One for X, one for me."
```

where `X` is a name or "you".

If the given name is "alice", the result should be 

```
"One for Alice, one for me." 
```

(with "Alice" capitalized)

If no name is given, the program should print: 

```
"One for you, one for me."
```

Use the randomly `sample`d `name` below to test your code. When you think you have it, get the tests to pass.

```ruby
name = ["raghu", "Bob", ""].sample
# write your program below
```
{: .repl #twofer title="Twofer" readonly_lines="[1,2]"}


```ruby
describe "Twofer" do
  it "prints 'One for Alice, one for me' if the name is 'Alice'" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return("Alice")
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/One for Alice, one for me/i), "Expected output to be 'One for Alice, one for me', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #twofer_test_1 for="twofer" title="Twofer prints 'One for Alice, one for me' if the name is 'Alice'" points="1"}


```ruby
describe "Twofer" do
  it "prints 'One for Shreya, one for me' if the name is 'shreya'" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return("shreya")
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/One for Shreya, one for me/i), "Expected output to be 'One for Shreya, one for me', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #twofer_test_2 for="twofer" title="Twofer prints 'One for Shreya, one for me' if the name is 'shreya'" points="1"}


```ruby
describe "Twofer" do
  it "prints 'One for you, one for me' if the name is empty" do
    path = "/tmp/code.rb"
    allow_any_instance_of(Array).to receive(:sample).and_return("")
    output = capture_stdout { require_relative(path) }
    expect(output).to match(/One for you, one for me/i), "Expected output to be 'One for you, one for me', but was '#{output}'."
  end

  def capture_stdout
    old_stdout = $stdout
    $stdout = StringIO.new
    yield
    $stdout.string
  ensure
    $stdout = old_stdout
  end
end
```
{: .repl-test #twofer_test_3 for="twofer" title="Twofer prints 'One for you, one for me' if the name is empty" points="1"}
