#include<bits/stdc++.h>
using namespace std;

struct edge{
	int src,dest,weight;
};

bool cmp(edge x,edge y){
	return(x.weight<y.weight);
}

struct subset{
	int parent,rank;
};

int find(subset s[],int i){
	if(s[i].parent!=i){
		s[i].parent=find(s,s[i].parent);
	}
	return s[i].parent;
}

void union1(subset s[],int x,int y){
	int x1=find(s,x);  
    int y1=find(s,y); 
	if(s[x1].rank==s[y1].rank){
		s[y1].parent=x1;
		s[x1].rank++;
	}
	else if(s[x1].rank>s[y1].rank){
		s[y1].parent=x1;
	}
	else{
		s[x1].parent=y1;
	}
}

int main(){
	int n,v;
	cout<<"Enter number of edges: ";
	cin>>n;
	edge arr[n];
	for(int i=0;i<n;i++){
		cout<<"Enter source point of "<<i+1<<" edge:";
		cin>>arr[i].src;
		cout<<"Enter end point of "<<i+1<<" edge:";
		cin>>arr[i].dest;
		cout<<"Enter weight point of "<<i+1<<" edge:";
		cin>>arr[i].weight;
	}
	sort(arr,arr+n,cmp);
	cout<<"Enter number of vertices: ";
	cin>>v;
	subset s[v];
	for(int i=0;i<v;i++){
		s[i].parent=i;
		s[i].rank=0;
	}
	edge result[v];
	int k=0,x,y;
	edge nextstage;
	for(int i=0;i<n && k<v-1;i++){
		nextstage=arr[i];
		x=find(s,arr[i].src);
		y=find(s,arr[i].dest);
		if(x!=y){
			result[k++]=nextstage;
			union1(s,x,y);
		}
	} 
	cout<<"Minimum Cost Spanning Tree:"<<endl;  
    for(int i=0;i<n-2;i++)  
        cout<<result[i].src<<" -- "<<result[i].dest<<" == "<<result[i].weight<<endl;    
	return 0;
}
