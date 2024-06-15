## Count of posotives / sum of negatives
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
