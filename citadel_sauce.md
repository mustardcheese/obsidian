
### Thomas Marshall, QD

"Suppose we're on a space mission and your job is to create a machine that helps distributes food to all the astronauts on the ship. What would you consider when making that machine? How would you program it out?"  (*ask ricky for more up to date details*)

Very open ended, ask lots of questions and be open with how you think, then code out an mvp in any language.

**AI Not allowed**

Ricky and I's answer:
- Expiration date
- Food allergies
- Preferences
- Number of meals distributed over time


### Yichi Zhang, QR

"Imagine we have a large stream of data we cannot load all at once into memory. We want to calculate the covariance matrix of the entire dataset. How would we calculate the matrix?Write out the function to do so."

Follow Up: time and space complexity

**AI Allowed, Covariance Formula Given**

**Solution:**
- Covariance matrix is symmetric along the diagonal, Cov(X,Y) == Cov(Y,X)
- Create a helper function to calculate the covariance of two values, run element-wise across every element above the diagonal
- Cache previously calculated values (hashmap) to avoid extra calculations

nxd matrix, dxd used to calculate covariance, O(n d^2) time, O(d^2) space



### Karl Condron, QD

"We have a collection of stocks, exchanges, and brokers and we need to design a system to stop allowing trades for certain combinations of each. Ex. if the system takes in AAPL, NYSE, Charles Schwab. Any request for buying apple on the nyse via schwab should be blocked. Choose a data structure for the implementation and then code the implementation out."

**No AI, no testcases just looking for syntax correctness**

Follow Up:
"For a hashmap, how would we avoid hash collisions? Is it possible to avoid hash collisions? Assume hash collisions are inevitable, how would we account for this?"

**Solution**:
- Hashmap of lists, anytime we hash the value we append onto the list. If there's a hash collision we still just append to the list and search through it if there's multiple members.