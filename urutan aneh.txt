#include <iostream>

using namespace std;
int partition(int *a,int start,int end)
{
    int pivot=a[end];
    //P-index indicates the pivot value index
    
    int P_index=start;
    int i,t; //t is temporary variable
    
    //Here we will check if array value is 
    //less than pivot
    //then we will place it at left side
    //by swapping 
    
    for(i=start;i<end;i++)
    {
    	if(a[i]%10<=pivot%10)
        {
            t=a[i];
            a[i]=a[P_index];
            a[P_index]=t;
            P_index++;
        }
     }
     //Now exchanging value of
     //pivot and P-index
      t=a[end];
      a[end]=a[P_index];
      a[P_index]=t;
    
     //at last returning the pivot value index
     return P_index;
 }
 
 void Quicksort(int *a,int start,int end)
 {
    if(start<end)
    {
         int P_index=partition(a,start,end);
             Quicksort(a,start,P_index-1);
             Quicksort(a,P_index+1,end);
    }
}


int main()
{
    int N;
    cin >> N;
    int a[N];
    for(int i=0;i<N;i++){
        cin >> a[i];
    }
    
    Quicksort(a,0,N-1);
    
    for(int i=0;i<N;i++){
        cout << a[i] << endl;
    }
    
    

    return 0;
}
