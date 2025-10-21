### My Parser

My parser for educational purposes

![Alt text](image.png)

### Example

```rust
peg::parser!{
    grammar list_parser() for str {
      rule number() -> u32
        = n:$(['0'..='9']+) {? n.parse().or(Err("u32")) }
  
      pub rule list() -> Vec<u32>
        = "[" l:(number() ** ",") "]" { l }
    }
}
  
pub fn main() {
    println!("{:?}", list_parser::list("[1,1,2,3,5,8]"));
}