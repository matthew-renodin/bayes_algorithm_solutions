# bayes algorithm introduction

Bayes theorem works using conditional probability. My introduction to statistics book desribes this in the first chapter as the probability(P) of an event (B) occurring given evidence (A) or written as P(B|A). Bayes theorem is the probability of an event B occurring when we already know that event A has occurred.

Bayes theorem is applied by measuring probability for many problems virus detection, cancer, and defects. I am using it for Bayesian interpretation to measure degree of belief and frequentist interpretation to measure the proportion of outcomes given A.


I start by first understanding the algorithm and breaking it up using a spreadsheet. This will help me understand the algorithm and help me code it. It will also help me write the tests for evaluating the probability.

(P(n1┤|n3)×P(n3))/(P(n1┤|n3)×P(n3)+P(n1│common)×(1-P(n3)))  ×P(n1┤|n3)

P(B|A) * Bayes Factor = postier odds or posterior probability

![image](https://user-images.githubusercontent.com/5507643/150643691-8471a580-6c96-42c6-8c04-6f4b65acbd1d.png)



Below is an example of using Bayes Algorithm. The data will come from a list and will have repeats. If you want to have it update the list would need to be updated and reprocessed. 

```javascript
function mr_bayes(total_size, B_num, A_num, B_in_common)
{
  const p_B_A = B_num/A_num;
  const p_A = A_num/total_size;
  const numerator = p_B_A * p_A;
  const common_num =  total_size - A_num;
  const p_B_common = B_in_common/common_num;
  const p_common = 1-p_A;
  const denominator = numerator+(p_B_common * p_common);
  const bayes_factor = numerator/denominator;
  const pp = p_B_A * bayes_factor;
  return pp;
}
```




