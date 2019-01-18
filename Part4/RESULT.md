### Results
The results are a bit disappointing. After incrementing and decrementing 1000000 times, we would expect to be back at 0, but this was not the case for any of the three languages. This shows that we have to be careful with how we handle several threads trying to operate on the same objects in memory.
