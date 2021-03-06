# IntervalTree
An implementation of the augmented interval tree algorithm in Ruby

# See also
* description in Wikipedia http://en.wikipedia.org/wiki/Interval_tree
* an implementation in Python by Tyler Kahn http://forrst.com/posts/Interval_Tree_implementation_in_python-e0K    

# ChanegLog
### 2013-04-06, contribution by ssimenov ( https://github.com/ssimeonov )
* **Range factory**: The current design allows for Range-compatible elements to be added except for the case where `Tree#ensure_exclusive_end` constructs a Range in a private method. In keeping with good design practices of containers such as Hash, this pull requests allows for a custom range factory to be provided to `Tree#initialize` while maintaining perfect backward compatibility.
Search in empty trees failing
* Adds a nil guard in `Tree#search` to protect against empty tree searches failing.
* **Cosmetic improvements**: Language & whitespace in specs, Gemfile addition, and .gitignore update

# Usage
See spec/interval_tree_spec.rb for details.
```ruby
require "interval_tree"

itv = [(0...3), (1...4), (3...5),]
t = IntervalTree::Tree.new(itv)
p t.search(2) => [0...3, 1...4]
p t.search(1...3) => [0...3, 1...4, 3...5]
```

# Note
Result intervals are always returned
in the "left-closed and right-open" style that can be expressed
by three-dotted Range object literals (first...last)

Full-closed intervals "(first..last)" for tree are internally
converted to half-closed intervals.

# Copyright
**Author**: MISHIMA, Hiroyuki ( https://github.com/misshie )  
**Copyright**: (c) 2011,2013 MISHIMA, Hiroyuki  
**License**: The MIT/X11 license  
