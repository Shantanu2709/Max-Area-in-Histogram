# Max-Area-in-Histogram
Find the largest rectangle Area in Histogram...

//# Code
import java.util.*;
class HelloWorld {
    static int maxArea(int [] arr)
    {
        int max=0;
        Stack<Integer> s = new Stack<>();
        // find next right
        int nr[] = new int[arr.length];
        for(int i=arr.length-1; i>=0; i--)
        {
            while(!s.isEmpty() && arr[s.peek()]>=arr[i])
            {
                s.pop();
            }
            if(s.isEmpty())
            {
                nr[i] =arr.length;
            }
            else
            {
                nr[i]=s.peek();
            }
            s.push(i);
        }
        s=new Stack<>();
        //find next left
        int nl[] = new int [arr.length];
        for(int i=0; i<arr.length; i++)
        {
            while(!s.isEmpty() && arr[s.peek()]>=arr[i])
            {
                s.pop();
            }
            if(s.isEmpty())
            {
                nl[i] =-1;
            }
            else
            {
                nl[i]=s.peek();
            }
            s.push(i);
        }
        
        //count area and return max Area
        for(int i=0; i<arr.length; i++)
        {
           int height = arr[i];
           int width=nr[i]-nl[i]-1;
           int currArea = height*width;
           max= Math.max(max,currArea);
            
        }
             return max;
            }
    public static void main(String[] args) {
       int arr[] ={2,1,5,6,2,3};
       System.out.print("Max rectangle area is:- "+maxArea(arr));
    }
}
