#include"stdafx.h"
#include<iostream>
#include<string>
#include<queue>
#include<string>
#include <vector>
using namespace std;
queue <char> q1;
queue <string> q2;
int konggeshu=0;
int zhimushuzi=0;
int yingwenzimu=0;
int zifushu=0;
struct link
{
	char ch0;
	struct link *next;
};
struct WORD
{
    string word;
    int num;
	struct WORD *next;
};
int panduan(const vector<WORD>&arr,string s)
{
	int i=1;
	for(i=0;i<arr.size();i++)
	{
		if(arr[i].word==s)return 0;
	}
	return 1;
}
int dayin(vector<WORD>&arr)
{
	int max,i=0,a=0,counter=0;
	string word;
	max=arr[0].num;
	word=arr[0].word;
	while(counter!=10)
	{
		for(i=0;i<arr.size();i++)
		{
			if(arr[i].num>max)
			{
				max=arr[i].num;
				word=arr[i].word;
				a=i;
			}
		}
		cout<<word<<"出现次数"<<max<<endl;
		max=0;
		arr[a].num=0;
		counter++;
	}
	return 0;
}
int counter(string zichuan,string muchuan)
{
	string s = muchuan;
	string ss = zichuan;
	int k = 0;
	int q = 0;
	int count = 0;
	int j;
	for(int i = 0; i<s.length(); i++)
	{
		q =  i;
		for (j = 0; j<ss.length()&&q<s.length();q++,j++)
		{
			if (ss[j] != s[q])
				break;
		}
		if(j==ss.length())
			count++;
	}
	return count;
}
int chuxiancishu(string muchuan)
{
	int a=0,n=q2.size();
	string zichuan;
	vector<WORD> arr(0);
	while(q2.size()!=0)
	{
		WORD p;
		zichuan=q2.front();
		q2.pop();
		p.num=counter(zichuan,muchuan);
		p.word=zichuan;
		if(panduan(arr,zichuan))
		{
			arr.push_back(p);
		}	
	}
	dayin(arr);	
	return 0;
}
string shu(link *a)
{
	char c;
	string ss="",muchuan="";
	while(a)
	{
		cout<<a->ch0;
		if(a->ch0>31&&a->ch0<127){zifushu++;}
		if(a->ch0==32)
			konggeshu++;
		if((a->ch0<58&&a->ch0>46)||(a->ch0<91&&a->ch0>64)||(a->ch0<123&&a->ch0>96))
			zhimushuzi++;
		if((a->ch0<91&&a->ch0>64)||(a->ch0<123&&a->ch0>96))
		{
			yingwenzimu++;
			if(a->ch0<91&&a->ch0>64){c=a->ch0+32;muchuan=muchuan+c;}
			else{muchuan=muchuan+a->ch0;}
		}
		if((a->ch0<91&&a->ch0>64)||(a->ch0<123&&a->ch0>96)||a->ch0==32||a->ch0==33||a->ch0==44||a->ch0==46||a->ch0=='\n')
		{
			if(a->ch0<91&&a->ch0>64)
			{
				q1.push((a->ch0)+32);
			}
			else if(a->ch0<123&&a->ch0>96)
			{
				q1.push(a->ch0);
			}
			else
			{
				if(q1.size()>=4)
				{
					ss="";
					while(q1.size()!=0)
					{
						ss=ss+q1.front();
						q1.pop();
					}
					q2.push(ss);
				}
				else
					while(q1.size()!=0){q1.pop();}
			}
		}
		a=a->next;
	}
	return muchuan;
}
int main()
{
	FILE *fp;
	char ch;
	link *s,*p,*head;
	string ss="",muchuan="";
	s=(struct link *)malloc(sizeof(struct link));
	head=s;
	if((fp=fopen("D:\\input.txt","r"))==NULL)
	{
		cout<<"Failure to open imput.txt!"<<endl;
		exit(0);
	}
	while((ch=fgetc(fp))!=EOF)
	{
		if((ch>=32&&ch<=126)||ch=='\n')
		{
			p=(struct link *)malloc(sizeof(struct link));
			p->ch0=ch;
			p->next=NULL;
			s->next=p;
			s=s->next;
		}
	}
	muchuan=shu(head->next);
	cout<<endl<<"字符数="<<zifushu<<endl;
	cout<<"空格数="<<konggeshu<<endl;
	cout<<"字母数字数="<<zhimushuzi<<endl;
	cout<<"英文字母数="<<yingwenzimu<<endl;
	chuxiancishu(muchuan);
}
