## Count of posotives / sum of negatives
my submission:
```rust
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
```rust
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
```rust
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
```rust
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
```
lesson learned: double gators `>>` do somethin binary.
## String incrementer
My try 1:
NOTE: technically doesnt work, but I cant see what input they are giving me that causes it to fail. 
```rust
fn increment_string(s: &str) -> String {
    // beat the null string
    if s.to_string().len() == 0{
        return "1".to_string();
    }
    else{
    if ! s.chars().last().unwrap().is_numeric(){
        let mut newstr = s.to_string();
        newstr.push('1');
        return newstr;
    }
    else {
        let mut newstr = s.to_string();
// get the total number of numbers
        let mut counter = 0;
        for i in newstr.chars(){
            if i.is_numeric(){
                counter += 1;
            }
        }
//pop characters = to total number of numbers
        let mut counter2 = 0;
        let mut nums = "".to_string();
        while counter2 < counter{
            nums.push(newstr.chars().last().unwrap());
            newstr.pop().unwrap();
            counter2 += 1;
        }
        //format the numbers
        nums = nums.chars().rev().collect::<String>();
        //add the number
        let mut numbers = nums.to_string().trim().parse::<i32>().unwrap();
        numbers +=1;
        newstr.push_str(&numbers.to_string());
        //return value if the length is correct
        if newstr.chars().count() == s.chars().count(){
          //  print!("{}\n",newstr);
            return newstr;
        }
        //get difference between length of og and current string
        else if newstr.chars().count() < s.chars().count() {
            let mut counter3 = s.chars().count() - newstr.chars().count();
            // take numbers off string whether its just numbers or not
            if ! newstr.chars().nth(0).unwrap().is_numeric() {
                while  newstr.chars().last().unwrap().is_numeric(){
                    newstr.pop();
                }
            }
            else{
                newstr = "".to_string();
            }
            //pad 0s
            while counter3 >= 1{
                newstr.push('0');
                counter3 -=1;
            }
            //readd numbers
            newstr.push_str(&numbers.to_string());
            return newstr;
        }
        else {
            return newstr;
        }
    }
}
}
```
