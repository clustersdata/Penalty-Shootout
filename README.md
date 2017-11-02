# Penalty-Shootout

Penalty Shootout

Problem Description

在足球比赛中，有不少赛事，例如世界杯淘汰赛和欧洲冠军联赛淘汰赛中，当比赛双方经过正规比赛和加时赛之后仍然不分胜负时，需要进行点球大战来决定谁能够获得最终的胜利。点球大战的规则非常简单，两方轮流派出球员罚点球，每方各罚5个。当5轮点球结束以后如果仍然不分胜负，则进入一轮定胜负的阶段。两方各派一名球员罚点球，直到有一方罚进而另一方没有进为止。
在北美职业冰球联赛中，也有点球大战。与足球的规则不同的是，它只先罚3轮点球，随后就进入一轮定胜负的阶段，而其他的规则完全一样。
在本题中，输入将给出每次点球是否罚进，而你的任务则是输出一个“比分板”。


Input

输入包含多组数据。每组数据的第一行包含一个整数N(1<=N<=18)，表示双方总共罚了多少个点球，N=0表示输入结束。随后有N行，每行是一个如下形式的字符串：
XXXX good：表示这个点球罚进
或者XXXX no good：表示这个点球没有罚进
其中XXXX表示球员名字（全部由字母和空格组成，保证不会出现歧义）
每一行保证不超过100个字符。
XXXX和good以及XXXX和no、no和good之间保证有且只有1个空格。
good、no good都是小写。本题是大小写相关的。
数据不保证点球大战一定结束，也不保证在结束以后立即结束这组数据（即：不用判断点球大战是否结束，只用把罚进的点球往比分上加即可）。

Output

对每组数据，输出一个比分板。一个点球如果罚进，则在对应的地方标上’O’，如果没有进则标上’X’。先罚球的队伍的信息在上面，后罚的在下面。最右边标上两队的比分。具体格式参考样例输出。注意如果一轮点球只罚了一个，则后面那个点球对应的地方写上’-’。

Sample Input

6 Riise good Ballack good Gerrard no good Lampard no good Fernando Torres good Malouda good 9 Christiano Ronaldo no good Messi no good Giggs good Abidal no good Carrick good Ronaldinho good Rooney good Henry no good Tevez good 0

Sample Output

1 2 3 Score O X O 2 O X O 2 1 2 3 4 5 Score X O O O O 4 X X O X - 1 提示： 空格数要和样例输出一样，否则很可能会被判为“格式错误”(Presentation Error)。

代码：

#include<stdio.h>

#include<string.h>

int main()

{

int T,a[9],b[9],t,i,j,k,len,sum1,sum2;

char s[100];

while(scanf("%d",&T)!=EOF&&T)

      {
      
       getchar();
       
       j=k=0;
       
       for(t=0;t<T;t++)
       
           {
           
            gets(s);
            
            len=strlen(s);
            
            for(i=len-1;i>=0;i--)
            
                if(s[i]==' ')
                
                  {
                  
                   if(t%2==0)
                   
                   {
                   
                   
                    if(s[i-1]=='o'&&s[i-2]=='n'&&s[i-3]==' ')
                    
                       a[j]=0;
                       
                    else 
                    
                       a[j]=1;
                       
                    j++;     
                    
                   }
                   
                   else
                   
                   {
                   
                    if(s[i-1]=='o'&&s[i-2]=='n'&&s[i-3]==' ')
                    
                       b[k]=0;
                       
                    else
                    
                       b[k]=1;
                       
                    k++;    
                    
                   }
                   
                   break;
                   
                  }
                  
            }
            
       sum1=sum2=0;
       
       for(i=1;i<=j;i++)
       
           printf("%d ",i);  
           
       printf("Score\n");
       
       for(i=0;i<j;i++)
       
          {
          
           if(a[i]==0)
           
              printf("X ");
              
           else
           
              printf("O ");
              
           sum1+=a[i];
           
          }     
          
       printf("%d\n",sum1); 
       
      for(i=0;i<k;i++)
      
          {
          
           if(b[i]==0)
           
              printf("X ");
              
           else
           
              printf("O ");
              
           sum2+=b[i];
           
          }
          
       if(k<j)
       
          printf("- ");  
          
       printf("%d\n",sum2);  
       
       }    
       
}
