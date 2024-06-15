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
`.is_empty()` is a function that returns True if the item checked is empty.\ `Vec::new()` creates an empty vector. the `vec![]` is a macro to return an empty vector.\ `.count()` conducts += 1\ `.filter(|&&variable|, expression)` allows what it sounds like.
