# test_5_28
#include <stdio.h>
//图的应用
//最短路径问题
//BFS求无权图单源最短路径
void BFS_MTN_Distance(Graph G,int u){
	for(int i=0;i<G.vexnum;++i)
	{
		d[i] = &;
		path[i] = -1;
	}
d[u] = 0;
visited[u] = TRUE;
EnQueue(Q,u);
while(!IsEmpty(Q))
{
	DeQueue(Q,u);
	for(w=FirstNeighbor(G,u);w>=0;w=NextNeighbor(G,u,w)){
		if(!visited[w])
		{
			d[w] = d[u] + 1;
			path[w] = u;
			visited[w] = TRUE;
			EnQueue(Q,w);
		}
	}
}
}
//Floyd算法
for(int k=0;k<n;k++){
	for(int i=0;i<n;i++){
		for(int j=0;j<n;j++){
			if(A[i][j] > A[i][k] + A[k][j]){
				A[i][j] = A[i][k] + A[k][j];
				path[i][j] = k;
			}
		}
	}
}
//拓扑排序
#define MaxVertexNum 100
typedef struct{
	AdjList vertices;
	int Vexnum,Arcnum;
}Graph;
typedef struct ArcNode{
	int adjvex;
	struct ArcNode* nextarc;
}ArcNode;
typedef struct VNode{
	VextexType data;
	ArcNode* firstarc;
}VNode,*AdjList[MaxVertexNum];
//逆拓扑排序（DFS算法）
void DFSTraverse(Graph G){
	for(int v=0;v<G.vexnum;++v)
		visited[v] = FLASE;
	for(int v=0;v<G.vexnum;++v){
		if(!visited[v])
			DFS(G,v);
	}
}
void DFS(Graph G,int v){
	visited[v] = TRUE;
	for(w=FirstNeighbor(G,v);w<=0;w=NextNeighbor(G,v,w)){
		if(!visited[w])
			DFS(G,w);
	}
	print(v);
}
//查找
//顺序查找
typedef struct{
	ElemType *elem;
	int TableLen;
}SSTable;
int Search_Seq(SSTable ST,ElemType key){
	for(int i=0;i<ST.TableLen && key != ST.elem[i];++i)
		return i == ST.TableLen ? -1 : i;
}
int Search_Seq(SSTable ST,ElemType key){
	ST.elem[0] = key;
	for(int i=ST.TableLen;ST.elem[i] != key;--i){
		return i;
	}
}
//折半查找
int Binary_Search(SeqList L,ElemType key){
	int low=0,high = L.TableLen-1,mid;
	while(low<=high){
		mid = (low + high)/2;
		if(L.elem[mid] == key)
			return mid;
		else if(L.elem[mid] < key)
			low = mid + 1;
		else (L.elem[mid] > key)
			high = mid - 1;
	}
	return -1;
}
//二叉排序树
typedef struct BSTNode{
	int key;
	struct BSTNode* lchild,*rchild;
}BSTNode,*BSTree;
//查找(非递归实现）
BSTNode* BST_Search(BSTree T,ElemType key){
	while(T != NULL && T->key != key){
		if(T->key > key)
			T = T->rchild;
		else
			T = T->lchild;
	}
	return T;
}
//递归实现
BSTNode* BST_Search(BSTree T,ElemType key){
	if(T == NULL)
		return NULL;
	if(T->key == key)
		return T;
	else if(T->key < key)
		return BST_Search(T->lchild,key);
	else
		return BST_Search(T->rchild,key);
}
