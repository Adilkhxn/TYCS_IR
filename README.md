# Pract1
def edit_distance(str1,str2):
m,n=len(str1),len(str2)
dp=[[0]*(n+1)
for
_
in range(m+1)]
for i in range(m+1):
for j in range(n+1):
if i==0:
dp[i][j]=j
elif j==0:
dp[i][j]=i
elif str1[i-1]==str2[j-1]:
dp[i][j]=dp[i-1][j-1]
else:
dp[i][j]=1+min(dp[i][j-1],dp[i-1][j-1])
return dp[m][n]
def correct_spelling(query,dictionary):
corrected_query=query.lower()
suggestions=[]
for word in dictionary:
distance=edit_distance(corrected_query,word.lower())
if distance<=2:
suggestions.append((word,distance))
suggestions.sort(key=lambda x:x[1])

return suggestions
dictionary=["information","retrieval","spelling","correction","system","Rajkamal"]
query=input("Enter your query:")
suggestions=correct_spelling(query,dictionary)
if suggestions:
print("Did you mean:")
for suggestion,distance in suggestions:
print(f"{suggestion}(Edit Distance:{distance})")
else:
print("No suggestion found")
