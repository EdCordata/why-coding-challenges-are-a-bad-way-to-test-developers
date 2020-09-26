# Why coding challenges are a bad way to test developers
This is a repo to showcase why coding challenges are a very
dumb way to look for good developers. I made it so i can send
it to any company that contacts me and dares to send me one of
these aforementioned challenges.

Lets start with a *fact* - these coding challenges
almost never show real life examples.

So, lets see some example.


### [BinaryGap](codility/Lesson-1-Iterations/BinaryGap.md)
Challenge is to convert integer to binary and find longest
sequence of consecutive zeros.

So if passed `9` -> `1001` -> `2`

Now, these are some examples i have found of other people
doing this challenge:

```ruby
def solution(n)
  bin = n.to_s(2)
  binary_gap = 0
  one = bin.index('1')
  
  for i in 1..(bin.size-1)
    current_string = bin[one..i].to_s
    if bin[i] == '1'
      one = i
      count_zeros = current_string.count('0')
      if binary_gap < count_zeros
        binary_gap = count_zeros
      end
    end
  end
  return binary_gap
end
```

```ruby
def solution(n)
  bin = n.to_s(2)
  return 0 unless bin =~ /0/i
  max = 0
  count = 0

  bin.each_char do |c|
  	if c == '1'
	  max = count if count > max
	  count = 0
  	else
  	  count = count + 1
  	end
  end
  max
end
```

```ruby
def solution(n)
  bin = n.to_s(2)
  temp = []
  gaps = []

  bin.each_char do |char|
    if char == "1"
      unless temp.empty?
        gaps << temp.length
        temp = []
      end
    else
      temp << char
    end
  end

  return 0 if gaps.empty?
  gaps.max
end
```

And here is my solution:
```ruby
def solution(n)
  res = n
          .to_s(2)
          .scan(/(?=(10+1))/)
          .flatten
          .map { |x| x.length - 2 }
          .max

  res || 0
end
```

Note that all of the examples above received the perfect 100% score.

I will NEVER write complicated algorithms myself. I will use a fully 
tested plugin or code from someone who knows what he is doing.

So you tell me, what you want in your company? Someone who can write
mathematical challenges and algorithms to pass some arbitrary scoring
system or you want someone who will actually write good looking, instantly
understandable, easy to edit code in your repo?

I think another parody repo, to hammer my point is this one:
https://github.com/EnterpriseQualityCoding/FizzBuzzEnterpriseEdition
