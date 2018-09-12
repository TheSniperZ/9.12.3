# 9.12.3
友元类
// 9.12.3友元类.cpp : 定义控制台应用程序的入口点。
//计算两点间的距离

#include "stdafx.h"
#include<iostream>
#include<math.h>
using namespace std;

class Point {
public:
	Point (int x =0,int y=0) :x(x),y(y){}
	int getX(){return x ;}
	int getY(){return y ;}
	friend float dist(Point &a,Point &b); //定义函数dist为Point类的友元
private:
	int x,y;

};
float dist(Point &a,Point &b)
{
	double x=a.x-b.x; //在友元函数dist中直接通过对象名访问类中的私有成员，而不需使用.getX()来进行函数调用
	double y=a.y-b.y;
	return static_cast<float>(sqrt(pow(x,2)+y*y));
}
int _tmain(int argc, _TCHAR* argv[])
{
	Point p1(1,2),p2(3,5);
	cout<<"the distance is:";
	cout<<dist(p1,p2)<<endl;
	return 0;
}
