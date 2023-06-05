The code is incomplete and has not undergone thorough testing yet. I will fix this when i have time.

I have uploaded this project for educational purposes because I believe it provides an intuitive approach to solving and understanding the approximate pattern matching problem. I haven't come across or seen this algorithm before, so I propose naming it PAM (Pigeonhole Approximative Matching).

The algorithm is built on the following principles:

By allowing up to 'd' mismatches, we apply the pigeonhole principle and divide our substring into 'd+1' pieces. We can find one of these pieces (if a match exists) using exact pattern matching, which is a relatively simpler problem to solve. These pieces are then searched using binary search in a suffix array constructed from the reference string. In this implementation, the suffix array is created through prefix doubling. Once we obtain an exact match of one of these pieces, we can backtrack to the position that corresponds to the beginning of our pattern (note that this position is in relation to the reference string but potential indels are in relation to the pattern thus we will have to do some additional steps if we want the exact position with respect to the reference string). These steps provide us with all candidate positions that warrant further investigation.
Next, we perform a series of local alignments using these intervals (-d in the beginning +d in the end to capture potential indels; not counting mismatches in the ends). Finally, we select the best alignment (within d edits) and return the matching position along with its corresponding cigar string.

Some of these steps have a worst-case running time that can be slow. However, the main idea here is that the algorithm incurs very little overheads and it is unlikely that we will need to perform a significant amount of extra work. For example, if we divide a pattern of size, say, 100 into four pieces of size 25 and obtain a match, it is very probable that this match represents a genuine position. This is because a match of size 25 is relatively unlikely to occur multiple times by chance alone, at least in a genome. Therefore, while the worst-case running time may not be ideal, we are somewhat protected as long as our pattern has a certain length. 

I am convinced that this algorithm has the potential to run quite efficiently with the right implementation. Please feel free to correct or optimize any parts and shoot me an email; antonhomilius@hotmail.com.







