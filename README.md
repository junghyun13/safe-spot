# safe-spot
# c
첫째 줄에는 어떤 지역을 나타내는 2차원 배열의 행과 열의 개수를 나타내는 수 N이 입력된다. 둘째 줄부터 N개의 각 줄에는 도시의 높이 정보가 입력된다. 높이의 평균값이하의 건물들은 모두 물의 잠기고 위아래왼쪽오른쪽을 기준으로 붙어있는 잠기지 않은 건물들중 제일낮은 건물1개가 잠기고 아무것도 붙어있지 않다면 무족건 잠긴다. 물에 잠기지 않은 안전한 영역은 몇개인지 프로그램을 작성해보자!

#include <stdio.h>
#include <stdlib.h>

int n,k,i,j,city[100][100],visit[100][100];
int dx[4]={0,0,1,-1},dy[4]={1,-1,0,0};
int answer=0,maxrain=0,re=0;
void dfs(int i,int j){
	visit[i][j]=0;
	for(k=0;k<4;k++){
		int x=i+dx[k];
		int y=j+dy[k];
		if(x>=0 && x<n && y>=0 && y<n){
			if(visit[x][y]!=0){
				dfs(x,y);}}} }
				
				
int safe(){
		for(i=0;i<n;i++){
			for(j=0;j<n;j++){
				visit[i][j]=city[i][j];
				if(visit[i][j]<=re){
					visit[i][j]=0;}}}
		int cnt;
		for(i=0;i<n;i++){
			for(j=0;j<n;j++){
				cnt=0;
				if(visit[i][j]!=0){
					cnt++;
					dfs(i,j);
					if(answer<cnt){
						answer=cnt;}}
				else{
					continue;}}}
		return answer; }
		
		
void main(){
	int total=0,count=0;
	scanf("%d",&n);
	for(i=0;i<n;i++){
		for(j=0;j<n;j++){
			scanf("%d",&city[i][j]);
			if(maxrain<city[i][j]){
				maxrain=city[i][j];
				count+=1;
				total+=city[i][j];}}}
	re=total/count; //평균값  
	safe();
	printf("장마철에 물에 잠기지 않은 안전한 영역의 최대 개수는: %d\n",answer); }
