## Count of posotives / sum of negatives
my submission:
```
fn count_positives_sum_negatives(input: Vec<i32>) -> Vec<i32> {
    if input == []{
        return [].to_vec()
    }
    let mut num = Vec::new();
    let mut posotive = 0;
    num.push(posotive);
    num.push(0);
    for i in input.iter(){
        print!("{}", i);
        if i > &(0 as i32){
            posotive +=1;
            }
        else{
            num[1] += i;
            }
        }
    num[0] = posotive;
    return num
}
```
better submission:
```
fn count_positives_sum_negatives(input: Vec<i32>) -> Vec<i32> {
    if input.is_empty() {
        return Vec::new();
    }
    
    vec![
        input.iter().filter(|&&x| x > 0).count() as i32,
        input.iter().filter(|&&x| x < 0).sum()
    ]
}
```
lesson learned:
`.is_empty()` is a function that returns True if the item checked is empty. \
`Vec::new()` creates an empty vector. the `vec![]` is a macro to return an empty vector. \
`.count()` conducts += 1. \
`.filter(|&&variable|, expression)` allows what it sounds like.

## Return negative
my solution:
```
if n > 0{
    return -n
    }
else{
    return n
}
```
better submission:
```
fn make_negative(n: i32) -> i32 {
    -n.abs()
}
```
lesson learned: \
THINK ABOUT METHODS BEFORE DOING THIS SHIT BY HAND. Also basic math is useful.

## Basic Math
my submission:
```
if operator == '+'{
    return value1 + value2
}
esle if operator == '-'{
    return value1 - value2
}
else if operator == '*'{
    return value1 * value2
}
else{
    return value1 / value2
}
```
better submission:
```
fn basic_op(operator: char, value1: i32, value2: i32) -> i32 {
    match operator {
        '+' => value1 + value2,
        '-' => value1 - value2,
        '*' => value1 * value2,
        '/' => value1 / value2,
        _ => {
            panic!("wrong operator!");
        }
    }
}
```
lessons learned: \
`match` keyword does the if this then that bs. \
`panic!` is a macro for errors.

## ones and zeroes
converting binary to decimal:
my submission:
```
fn binary_slice_to_number(slice: &[u32]) -> u32 {
    let mut var = slice.len() as u32;
    let mut sum = 0;
    for i in slice {
        var -= 1;
        if i > &0 {
            sum += u32::pow(2, var);
            }
    }
    return sum;
}
``` rust
