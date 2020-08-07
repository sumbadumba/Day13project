# Day13project

https://www.cplusplus.com/

#pragma once
#include"stdafx.h"

class Character
{
public:
	Character();
	Character(string name, int hp);
	~Character();

	//정적 메소드
	void Function();
	static void StaticFunction();

	//정적 멤버 변수
	static int count;
	static int score;

protected:
	string name;
	int hp;
	float kt;
};


#include "Character.h"
#include "stdafx.h"

//정적 멤버 변수의 초기화
int Character::count = 0;
int Character::score = 0;

Character::Character()
{
	count++;
	Function();

}
Character::Character(string name, int hp)
	:name(name),hp(hp)
{

}
Character::~Character()
{
}
void Character::Function()
{
	cout << count << endl;

	StaticFunction();

}
void Character::StaticFunction()
{
	cout << count << endl;

}


#pragma once

#ifndef Day16
#define Day16
#endif // !1

#include<iostream>
#include<string>
#include<stdio.h>
#include<Windows.h>
#include<vector>
#include<time.h>
#include<conio.h>
#include<stdlib.h>

using namespace std;


//#include"stdafx.h"
//#include"Character.h"
//
//// STL (Standard Templeate Library)
//// STL container 
//
//int main()
//{
//	vector<int> vec;//int를 담을수 있는 벡터 저장소이다.
//	/*vector<float> vec2;
//	vector<Character> vec3;*/
//	//vector<Character*> vec4;
//
//	//vec.push_back(30);//
//	//vec.push_back(40);
//	//vec.push_back(50);
//	//int result = vec[0];
//	//int result2 = vec[1];
//	//int result3 = vec[2];
//	//int result4 = vec.at(1);
//
//	vec.push_back(10);
//	vec.push_back(20);
//
//	//cout << vec[0] << endl;
//	//cout << vec.size() << endl;//크기를 알려줌
//	//cout << vec.empty() << endl;//0이 아닌 모든 값은 true이다.
//	//cout << vec.size() << endl;//크기를 알려줌
//	//vec.clear();//0이 됨..
//	//cout << vec.size() << endl;//크기를 알려줌
//
//	vec.assign(30, 4);//이전의 내용을 날리고 새로운 녀석을 만듬
//	//cout << vec.size() << endl;
//	//cout << vec[0] << endl;//벡터는 계속 배열이 생성된다.
//
//	//for (int i = 0; i < 30; i++)
//	//{
//	//	vec.push_back(i);//뒤로 더 0~29까지 넣어준다.
//	//}
//	//cout << vec.size() << endl;
//
//	vector<Character> vec2;
//	vec2.assign(10, Character("Character", 10));
//
//	Character front = vec2.front();
//	Character back = vec2.back();
//
//	vector<Character>::iterator it = vec2.begin();//이터레이터를 반환하는 녀석
//	//이터레이터? (반복자?)
//	//이터레이터로 벡터를(포인터는 아님)포인터느낌의 접근자.
//	vector<Character>::iterator it2 = vec2.end();//마지막을 반환함.
//
//	while (it != it2)
//	{
//		it->Function();
//		it++;
//	}//while문은 한번비교를 하고(빠름)
//
//
//	for (vector<Character>::iterator iter = vec2.begin();
//		iter != vec2.end; iter++)//iter가 ++을 하면 다음 놈을 가리킨다.(포인터는 아닌데 포인터같은 느낌으로 쓰는 놈이다.)
//	{
//		iter->Function();
//	}//for문은 두번비교를 한다.(느림)
//
//
//
//	return 0;
//}
//백터는 늘어나는 배열이다.
//정해지지 않음.
//push_back()하면 계속 들어감
//벡터는 중간의 값을 지울 수 있다.(eraser)index로 접근 가능 가운데꺼 지우면 밑에 있는 애가 올라온다.
//while(){
//iter++
//continue;}//
  
  
  #include"stdafx.h"
#include<map>// ?
#include"Character.h"

int main()
{
	map<int, Character*>charRepo;//학번과 이름을 찾을 때?
	Character c;

	//charRepo.insert(make_pair(1,c));//STL에 있는 애 //키과 값으로 된 것을 만듬
	charRepo[101] = new Character("Character 1",10);//index처럼 쓰지만 index가 아니다. [0]번부터 시작하지 않음...
	charRepo[201] = new Character("Character 2",20);
	charRepo[301] = new Character("Character 3", 30);

	map<int, Character*>::iterator it = charRepo.find(300);//있냐 없냐? 찾음.
	//int는 first, Character*는 second로 구분한다.

	if (it == charRepo.end())
	{
		cout << "못 찾음" << endl;
	}
	else
	{//it는 이터레이터여서 화살표//second는 포인트여서 화살표
		it->second->Function();
	}//게임회사에서 vector와 map을 많이 쓴다.


	/*charRepo.erase(301);
	charRepo[300];//에러가 뜸.
*/
	Character * charPtr = nullptr;

	int key = -1;
	//map을 잘 쓰려면 iterator를 잘 다뤄야 한다.
	for (map<int, Character*>::iterator iter = charRepo.begin();
		iter != charRepo.end(); iter++)
	{

		key = iter->first;
		charPtr = iter->second;
		//
		cout << "인덱스" << key << " 가 지워짐. " << endl;
		//
		iter->second = nullptr;
		delete charPtr;
	}
	return 0;
}

#pragma once

#ifndef Day17
#define Day17

#include<iostream>
#include<string>
#include<stdio.h>
#include<Windows.h>
#include<vector>
#include<time.h>
#include<conio.h>
#include<stdlib.h>

using namespace std;


#endif // !1

#pragma once

#include"stdafx.h"

class String
{
public:
	String();
	String(const char * str);

	~String();


	//연산자 오버로딩
	String& operator = (const String& other);


	//String a;
	//String b = a;//기본적으로 된다.(캐릭터(class)에다가 캐릭터(class)를 넣을 때 연산자 오버로딩을 쓴다)
	//+,-,연산자 가능..

	char At(UINT index);

	char operator [] (UINT index);

	static UINT Length(const char * str);


private:
	char * str = nullptr;

	static const UINT additionalBuffer;
	UINT capacity = 15;
	UINT length = 0;


};


#include "String.h"
#include"stdafx.h"


String::String()
{
	str = (char*)malloc(sizeof(char)*capacity);
}

String::String(const char * str)
{
	length = Length(str);
	while (length > capacity)
	{
		capacity += additionalBuffer;
	}
	this->str = (char*)malloc(sizeof(char)*capacity);
	memset(this->str, '\0', sizeof(char)*capacity);
	memcpy(this->str, str, length);


}
String::~String()
{
	free(str);//말록해제
}
String& String::operator = (const String& other)
{

}
char String::At(UINT index)
{

}

//char * str = nullptr;
//
//static const UINT additionalBuffer;
//


#숙제
STL콘테이너를 사용한 캐릭터 정보 입력기를 만들자
1.몇개의 캐릭터를 생성할지 입력
직업: 전사,궁수,성직자
HP
MP
AP
DP
2.모두 입력되면 전체 출력
3.프로그램 종료할지 선택
4.종료하지 않을 경우 인덱스를 선택해서 해당 캐릭터 정보를  출력
5.3에서부터 반복
STL사용 코드가 보이게 해서 실행되는 스크린샷을 찍을 것



