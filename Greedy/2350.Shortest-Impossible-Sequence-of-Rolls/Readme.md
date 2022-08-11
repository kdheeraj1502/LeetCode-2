### 2350.Shortest-Impossible-Sequence-of-Rolls

我们考虑长度为1是否满足。我们势必会想找到一个最短的区间[0:m]，使得rolls[0:m]里面必然包括了1到k。这意味着仅在这个前缀里，我们可以构造任意的、长度为1的序列。如果找不到这样的m，自然本题就终止了。此时我们关注m这个位置，不难得知，rolls[m]一定是在这个区间里唯一出现的一个元素，不妨记做x。

此时我们考虑长度为2的情况。因为x是[0:m]中最“稀有”的元素（最晚出现、仅出现了一次），这意味着在所有的长度为2的序列中，以x打头的序列最不容易找到。根据前述，我们必须舍弃掉前m-1个元素，直到第m个元素我们才找到了x。于是我们就只需要考虑构造“x*”这种序列，为了能让`*`可以是任意元素，我们必须在m之后再找一段区间，记做[m+1,n]，使得其中包含了1到k。如果能找到这样的n，那么意味着我们在[0:n]的前缀里可以构造任意的、长度为2的序列。类似地，我们需要注意到rolls[n]一定是[m+1:n]这个区间里唯一出现的一个元素，不妨记做y。

同理，我们在考虑长度为3的情况时，`xy*`是最难构造的。因为最短只有在[0:n]的前缀里才出现`xy`。所以接下来的任务就是从n+1开始找一段区间，需要包含1到k的所有元素...

依次类推，我们发现本题的本质就是从rolls的起点，不停地寻找一段区间，使其恰好包含了1到k所有的元素。能连续找到多少个这样的区间，就意味着我们可以构造多长的序列，使得序列里的每一个元素都有可能是1到k。