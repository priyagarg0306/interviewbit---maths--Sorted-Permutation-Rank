# interviewbit---maths--Sorted-Permutation-Rank


**-----> Question:**

Given a string, find the rank of the string amongst its permutations sorted lexicographically. 

Assume that no characters are repeated.

Example :

Input : 'acb'
Output : 2

The order permutations with letters 'a', 'c', and 'b' : 
abc
acb
bac
bca
cab
cba
The answer might not fit in an integer, so return your answer % 1000003



**----->code:**

int fact(int n){
    if(n==0||n==1){
        return 1;
    }

    return (n*fact(n-1))%1000003;
}

int Solution::findRank(string A) {
    int ans=0,x=0,n=A.length();
    string s=A;
    sort(s.begin(),s.end());
    vector<int> check(n,1);

    for(int i=0;i<n;i++){
        if(check[i]==-1){
            continue;
        }else if(s[i]!=A[x]){
            ans=(ans+fact(n-x-1))%1000003;
        }else{
            check[i]=-1;
            x++;
            i=-1;
        }
    }

    return (ans+1)%1000003;

}
