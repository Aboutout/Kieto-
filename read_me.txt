import sys
import numpy as np
INT_MAX = sys.maxsize

ii=0
N=int(input())
M=int(input())
A=[ [ 0 for i in range(M) ] for j in range(N) ]
cost=[ [ INT_MAX for i in range(M) ] for j in range(N) ]

entries = list(map(int, input().split()))
A = np.array(entries).reshape(N, M)

fl=int(input())
flat=int(input())
destnfl=int(input())
destnflat=int(input())

if A[fl][flat]==0:
    for i in range(M):
        if A[fl][i]==1:
            cost[fl][i]=abs(flat-i)+1
else :
    for i in range(M):
        if A[fl][i]==1:
            cost[fl+1][i]=1
        else:
            cost[fl+1][i]=INT_MAX

for i in range(1,N):
    if ii +1 < N:
        ii=ii+1
    for k in range(M):
        if cost[i][k]==min(cost[i]):
            for kk in range(M):
                if A[ii][kk] == 1 and ii < N:
                    if cost[ii+1][kk]>abs(k-kk)+1+cost[i][k]:
                        cost[ii+1][kk]=abs(k-kk)+1+cost[i][k]
    print(cost[destnfl][destnflat])
