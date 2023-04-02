# some-important-coding-problems


1. First unique character of a string
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
2. second smallest element in the array 
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

3. second minimum element in sorted rotated array



4. minimum element in sorted array

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

5 .Print matrix in spiral form e.g. {{1,2,3},{4,5,6},{7,8,9}} Output . 1,2,3,6,9,8,7,4,5
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

6. Add two fractions
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

7. Find out the number of pair from given integer array whose sum isequal to a given number.

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

8. Missing characters to make a string Pangram
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

9. Check if a number is a power of another number
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

10. Given Input,print the following input: “SSSSSTTPPQ” Output:“5S2T2P1Q”
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

11. Given an array of Employees with name,marks. Find out the maximum average marks from the list
const arr = [
  ["Alia","-678"],["Bobby","100"],["Alex","223"],
  ["Alex","-23"],["Bobby","723"]];
let map = new Map()
for(let i=0;i<arr.length;i++){
    if(map.has(arr[i][0])){
      map.set(arr[i][0],[map.get(arr[i][0])[0]+1,map.get(arr[i][0])[1]+Number(arr[i][1])])
    }else{
      map.set(arr[i][0],[1,Number(arr[i][1])])
    }
}
let ans = []
for(let [key, value] of map.entries()){
  ans.push(Math.floor(value[1]/value[0]))
}
console.log("ans>>>",Math.max(...ans))

12. Possible to make a divisible by 3 number using all digits in an array

let arr = [ 50, 90 ];

let sum=0;
for(let i=0;i<arr.length;i++){
  sum+=arr[i]
}
if(sum%3==0)
    console.log(true);
else 
    console.log(false)

13. Print words of a string in reverse order. Let there be a string say “I AM A TESTER So, the output should be TESTER A AM I”
str.split(' ').reverse().join(' ')

14. Find the first repeated word in a string. Input : "Ravi had been saying that he had been there" .Output : had
let str = 'been Ravi had been saying that he had been there';
let arr = str.split(' ');
let map = new Map();

for(let i=0;i<arr.length;i++){
    if(map.has(arr[i])){
        map.set(arr[i],map.get(arr[i])+1)
    }else{
      map.set(arr[i],1)
    }
}
for(let i=0;i<arr.length;i++){
    if(map.get(arr[i]) > 1){
      console.log("word>>>",arr[i]);
      break;
    }
}

15. Program to find Smallest and Largest Word in a String.Input :This is a test string Output : Minimum length word: is Maximum length word: string

let str = 'GeeksforGeeks A Computer Science portal for Geeks'
let arr = str.split(' ');
let max = Number.MIN_SAFE_INTEGER;
let min = Number.MAX_SAFE_INTEGER;
let maw='';
let miw=''
for(let i=0;i<arr.length;i++){
 
  if(arr[i].length > max){
    max = arr[i].length
    maw=arr[i]
  }
  if(arr[i].length < min){
    min = arr[i].length
    miw=arr[i]
  }

}
console.log(maw,"  ",miw)

16. Given a string str and a character x, find last index of x in str.
traverse string from right to left

17. Given a string and a delimiter character. 
Split the string based on the delimiter 
and print the list of resulting sub strings.

//Given a sentence, task is to remove spaces from the sentence
//and rewrite in Camel case.
//It is a style of writing where we don’t have spaces 
//and all words begin with capital letters.
//Input  : I got intern at geeksforgeeks
//Output : IGotInternAtGeeksforgeeks

let input  = 'I got intern at geeksforgeeks';
let str="";
let ans=[];
for(var i=0;i<input.length;i++){
        if (input[i] == ' ')
        {
            // conversion into upper case
            str+= input[i+1].toUpperCase();
            i++;
             
        }
        else{
         
            str+= input[i];
            }
}
console.log("str>>>>",str)

// Given a string, sort it in descending order. Input : mupursingh Output : uusrpnmihg

/*
18. Given an array A[] of integers find sum of product of all pairs of array elements
Input : A[] = {1, 3, 4}
Output : 19
Possible Pairs : (1,3), (1,4), (3,4)
Sum of Product : 1*3 + 1*4 + 3*4 = 19

based on (a+b+c)^2 = a2+b2+c2 + 2(ab+bc+ca)
*/


19. //2nd smallest element of an unsorted array.

const arr = [3,2,4,5,8,11,9,24,13];
let fmax=arr[0];
let smax=arr[0];
for(let i=0;i<arr.length;i++){
    if(arr[i]<fmax){
        smax=fmax;
        fmax=arr[i];
    }else if(smax > arr[i]){
        smax=arr[i]
    }
}

console.log(fmax,"  ",smax)

20. /*Largest substring with unique characters 
e.g. aaabcbdeaf Output : cbdeaf*/
let str = 'a';
let map = new Map();
let st=0;
let currlen;
let maxlen=0;
let start;
map.set(str[0],0)
for(var i=1;i<str.length;i++){
  
  if(!map.has(str[i])){
    map.set(str[i],i)
  }else{
    if(map.get(str[i]) >= st){
      
      currlen = i-st;
      if(maxlen < currlen){
        maxlen = currlen;
        start = st;
      }
      
      st = map.get(str[i])+1
    }
    map.set(str[i],i)
  }
  
}
if(maxlen < i-st){
  maxlen = i-st;
  start = st;
}
   
console.log(str.substr(start,maxlen))
/*
  Arrange given numbers to form the biggest number
*/
let arr = [1, 34, 3, 98, 9, 76, 45, 4];

console.log(arr.sort((first,second)=>{
  return (''+first+second) > (''+second+first) ? -1:1
}).join(''))

/*
21. Find the smallest subarray whose sum is equal or greater than thetarget value
*/

const arr = [1,4,45,6,0,19];
function smallestSubWithSum(arr, n, x)
{

    // Initialize length of smallest subarray as n+1
    let min_len = n + 1;

    // Pick every element as starting point
    for (let start=0; start<n; start++)
    {
    
        // Initialize sum starting with current start
        let curr_sum = arr[start];

        // If first element itself is greater
        if (curr_sum > x) return 1;

        // Try different ending points for curremt start
        for (let end=start+1; end<n; end++)
        {
        
            // add last element to current sum
            curr_sum += arr[end];

            // If sum becomes more than x and length of
            // this subarray is smaller than current smallest
            // length, update the smallest length (or result)
            if (curr_sum > x && (end - start + 1) < min_len)
                min_len = (end - start + 1);
        }
    }
    return min_len;
}
console.log(">>>>",smallestSubWithSum(arr,arr.length,51));
/*convert in following format*/
let arr = [
        {cat: 2},
        {dog: 3},
        {cow: 5},
        {cat: 3},
        {cat: 2},
        {dog: 1},
        {cow: 3},
]

// output - {{cat:7},{dog:4}, {cow:8}}

console.log(arr.reduce((acc,curr) =>{
  
  console.log("acc>>",acc," curr>>",curr)
  if(acc[Object.keys(curr)[0]]){
    acc[Object.keys(curr)[0]]+=Object.values(curr)[0]
  }else{
    acc[Object.keys(curr)[0]] = Object.values(curr)[0]
  }
  return acc
  
},{}))

/*
22.   Shuffle 2n integers in format {a1, b1, a2, b2, a3, b3, ……, an, bn} 
  without using extra space
  Brute Force Approach
*/

let arr = [1,2,3,4,5,6];
//output - [1,4,2,5,3,6]

let n = arr.length/2;

for(let i=0, q=1, k=n;i<n;i++,q++,k++){
  for(let j=k;j>i+q;j--){
    swap(a[j-1],a[j])
  }
}

# Trees

1. Level order traversal (iterative)

solve : function(A){
        let ans = [];
        let curr = [];
        let queue = [];
        if(A == null)
            return; 
        queue.push(A);
        queue.push(null);
        // ans.push(A.data);
        while(queue.length !==0 ){
            let node = queue.shift();
            // console.log(node)
            if(node === null){
                // queue.shift()
                curr = [];
                if(queue.length !== 0){
                    queue.push(null);
                }
            }
            else{
            // console.log("node data>>",node.data)
                if(node.left !== null){
                    queue.push(node.left);
                    // ans.push(node.data)
                }
                if(node.right !== null){
                    queue.push(node.right);
                    // ans.push(node.data)
                }
                // console.log("ans>>>",ans)
                curr.push(node.data);
            }
            
        }       
        return ans;
	}


2. Left view of binary tree

# idea - The idea is to do a simple level order traversal, the only extra thing that needs to be done is to print the value of the first node at each level in the tree.

solve : function(A){
        let ans = [];
        let curr = [];
        let queue = [];
        if(A == null)
            return; 
        queue.push(A);
        queue.push(null);
        // ans.push(A.data);
        while(queue.length !==0 ){
            let node = queue.shift();
            // console.log(node)
            if(node === null){
                // queue.shift();
                ans.push(curr.shift());
                curr = [];
                if(queue.length !== 0){
                    queue.push(null);
                }
            }
            else{
            // console.log("node data>>",node.data)
                if(node.left !== null){
                    queue.push(node.left);
                    // ans.push(node.data)
                }
                if(node.right !== null){
                    queue.push(node.right);
                    // ans.push(node.data)
                }
                // console.log("ans>>>",ans)
                curr.push(node.data);
            }
            
        }       
        return ans;
	}

/* Sum all nonnegative intergers up to n */
function sum(num){
  if(num==0){
    return num;
  }else{
    return num + sum(num-1);
  }
}
// console.log(sum(3));

/*
Implement the built-in .length function in a recursive fashion
*/
function length(str){
  if(str === ''){
    return 0;
  }else{
    return length(str.substring(1))+1;
  }
}
console.log("length>>>",length("Mayank"));
/*
Implement findRange in a recursive fashion
*/
function findRange(a,b){
  if(a>=(b-1)){
      return[];
  }else{
   return [a+1].concat(findRange(a+1,b));
  }
}

console.log(findRange(2,9));

/*
Challenge 1: Implement flat() function using recursion
const arr1 = [0, 1, 2, [3, 4,[5,6,7]],8,9,10];
*/
// let result=[];
function Flat(arr,result=[]){
    for(let i=0 ; i<arr.length ; i++){
      if(!Array.isArray(arr[i])){
          result.push(arr[i])
        }else{
          Flat(arr[i],result);
      }
    }
  return result;
}
// console.log(Flat([0, 1, 2, [3, 4,[5,6,7]],8,9,10]))

/*
Challenge 2: Implement getElementByClassName() function using recursion
*/

// function getElementByClassName(className){
  
// }

/*
  Challenge 4: Implement Array.fill() function using recursion
*/
function fill(size,number){
  if(size<=0){
      return[];
  }
    return [number].concat(fill(size-1,number))
}
console.log(fill(5,9))

















