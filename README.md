# some-important-coding-problems


First unique character of a string
let atr = 'qcaabdce';
let map = new Map();

for(let i=0;i<atr.length;i++){
  if(map.has(atr[i])){
    map.set(atr[i],map.get(atr[i])+1)
  }else{
    map.set(atr[i],1)
  }
}
for(let i=0;i<atr.length;i++){
  if(map.get(atr[i])==1)
     {
       console.log(atr[i]);
       break;
     }
}
second smallest element in the array 
const arr = [5,6,1,2,4,3];
let fmin=arr[0];
let smin=arr[0];
for(let i=0;i<arr.length;i++){
  if(arr[i]  > fmin){
    smin = fmin;
    fmin = arr[i];
  }
  else if(arr[i]>smin){
    smin = arr[i];
  }
}
console.log("fmin>>>",fmin," smin>>>",smin);

second minimum element in sorted rotated array



minimum element in sorted array

const brr = [5,6,1,2,4,3];
let l = 0;
let r = brr.length-1;

  while(l<=r){
    let mid = l+Math.floor((r-l)/2);
    if(brr[mid] < brr[mid-1] && brr[mid] < brr[mid+1]){
         console.log(brr[mid])
         break;
    }else if(brr[mid] > brr[mid-1] && brr[mid] < brr[mid+1]){
          r = mid-1;
    }else if(brr[mid] > brr[mid-1] && brr[mid] > brr[mid+1]){
      l=mid+1
    }
  }

Print matrix in spiral form e.g. {{1,2,3},{4,5,6},{7,8,9}} Output . 1,2,3,6,9,8,7,4,5
See again
 
let arr = [[1,2,3],[4,5,6],[7,8,9]]
  let ans = [];
  let k=0;
  let m=arr.length;
  let l=0;
  let n=arr[0].length;
/*
        k - starting row index
        m - ending row index
        l - starting column index
        n - ending column index
        i - iterator 
    */
  while(k < m && l<n){
    
    for(let i=l;i<n;i++){
      ans.push(arr[k][i])
    }
    k++;
    for(let i=k;i<m;i++){
      ans.push(arr[i][n-1])
    }
    n--;
   
    if(k<m){
      for(let i=n-1;i>=l;i--){
        
       ans.push(arr[m-1][i])
    }
      m--
    }
   
    
    if(l<n){
      for(let i=m-1;i>=k;i--){
      ans.push(arr[i][l])
    }
      l++;
    }
  }

Add two fractions
Input:  1/5 + 3/15
Output: 2/5

function gcd(a,b){
  if(a==0){
      return b
  }else{
    return gcd(b%a,a)
  }
}

function AddFraction(num1,den1,num2,den2){
  
     
  //gcd
    let den3 = gcd(den1,den2);
   //lcm
  den3 = Math.floor((den1*den2)/den3);
  
  //covert fractions 
  let num3 = (num1*(den3/den1) + num2*(den3/den2))
  
  let common_factor = gcd(den3,num3);
  
  num3 = Math.floor(num3/common_factor)
  den3 = Math.floor(den3/common_factor)
    
  console.log(num3+"/"+den3)
  
}

  AddFraction(1,5,3,15)

Find out the number of pair from given integer array whose sum isequal to a given number.

const arr = [1, 5, 7, -1, 5 ]
const sum = 6;
let map = new Map()

for(let i=0;i<arr.length;i++){
  map.set(arr[i],i)
}
let ans = [];
for(let i=0;i<arr.length;i++){
  let elem = sum-arr[i]
  if(map.has(elem) && map.get(elem) > map.get(arr[i])){
    ans.push([arr[i],elem])
  }
}
console.log("amns>>>",ans)

Missing characters to make a string Pangram
let str = 'The quick brown fox jumps'.toLowerCase()
let map = new Map()
let ans=''
let k = 97;
for(let i=0;i<str.length;i++){
      map.set(str[i],i)
  }

for(let i=97;i<=122;i++){
  if(!map.has(String.fromCharCode(i))){
    ans+=String.fromCharCode(i);
  }
}
console.log("ans>>>",ans)

Check if a number is a power of another number
let m=8;
let n=2;
let p=n;
while(p < m){
   p = p * n;
}
if(p==m)
  console.log(true);
else 
  console.log(false);

Given Input,print the following input: “SSSSSTTPPQ” Output:“5S2T2P1Q”
let str = "SSSSSTTPPQ"
let map = new Map()

for(let i=0;i<str.length;i++){
      if(map.has(str[i])){
        map.set(str[i],map.get(str[i])+1)
      }else{
        map.set(str[i],1)
      }
}
let ans=''
for(let [key,value] of map.entries()){
  ans+=value+key
}
console.log("ans>>>",ans)








