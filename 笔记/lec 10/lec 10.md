![](images\1.png)
- Always remeber that when you write programs, they should be written for someone else to read, and only incidently for a computer to excute them.So the fisrt form is better than the second as it's easy to read and understand(follow the common rules of a recursive function)

Tree-shaped processes arise whenever executing the body of a recursive function makes more than one call to that function
![](images\2.png)

![](images\3.png)

![](images\3.png)
- dp[n][m] = dp[n - m][m] + dp[n][m - 1]