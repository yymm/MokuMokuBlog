Title: Markdownも使えるPelican
Date: 2014-06-17 08:12:24
Tags: Markdown

# Markdown対応

GFM使えます。滅多に使えわないけどテーブル使えます。CSS書いてないから残念な感じだけど。

Codeはhighlight.jsを使って、いろんな言語使えます。

フロンドで処理してるから、Previewとかもできないことはない。

## table

| Left-Aligned  | Center Aligned  | Right Aligned |
| :------------ |:---------------:| -----:|
| col 3 is      | some wordy text | $1600 |
| col 2 is      | centered        |   $12 |
| zebra stripes | are neat        |    $1 |

## underscore

_ hoge
_ hige

## Strikethrough

~~ReSTはｵﾜｺﾝ~~

# Code

highlight.jsが対応している範囲は使える

## golang

```go
// You can edit this code!
// Click here and start typing.
package main

import "fmt"

func main() {
	fmt.Println("Hello, 世界")
}
```

## rustlang

```rust
// This code is editable and runnable!
fn main() {
    // A simple integer calculator:
    // `+` or `-` means add or subtract by 1
    // `*` or `/` means multiply or divide by 2

    let program = "+ + * - /";
    let mut accumulator = 0;

    for token in program.chars() {
        match token {
            '+' => accumulator += 1,
            '-' => accumulator -= 1,
            '*' => accumulator *= 2,
            '/' => accumulator /= 2,
            _ => { /* ignore everything else */ }
        }
    }

    println!("The program \"{}\" calculates the value {}",
              program, accumulator);
}
```

### Highlight

地味に違う

![](http://i.gyazo.com/701a7d069c4c4696794f9990b89f2b69.png)

```ruby
class AllButPattern
  Match = Struct.new(:captures)

  def initialize(except)
    @except   = except
    @captures = Match.new([])
  end

  def match(str)
    @captures unless @except === str
  end
end

def all_but(pattern)
  AllButPattern.new(pattern)
end

get all_but("/index") do
  # ...
end
```
