# DB2 Project
**2021 2학기 DB 설계 및 구현 2** Oracle DBMS Wedding Company Database 설계와 구현

<br>

## Happy Wedding 가상 회사 소개
회사명은 ‘Happy Wedding Plan(HWP)’으로, 웨딩 관련 서비스업의 회사이다. 신혼부부들이 직접 모든 결혼 계획을 하기에는 많은 시간과 노력이 필요하기 때문에, HWP는 고객 대신 완벽한 계획을 정하여 웨딩 플랜을 제공하고자 한다.
HWP는 고객 대신 스튜디오, 드레스, 메이크업 등의 협력업체와 컨택하고 결혼식을 진행할 웨딩 홀, 추후에 갈 신혼여행을 위한 여행 패키지를 예약해준다. 고객의 결혼에 관련된 전반적인 것들을 계획해주는 것이다.
모든 업체와 서비스들이 만족스러운 구성을 가지고 있는 것은 아니다. 고객들은 어느 업체가 만족스러운 서비스를 제공하는지 알지 못한다. 
HWP는 고객이 최상의 선택을 할 수 있도록 도와주며 평생 잊지 못할 추억을 선물해주는 business goal을 수행한다. 
추가로, HWP는 수집된 자료를 기반으로 온라인 서비스를 구축하여 사업을 확장하고 매출의 상승을 목표로 한다.

<br>

## ERD(Entity Relationship Diagram)
![Happy Wedding Planner ERD](https://github.com/user-attachments/assets/37e0d5f0-c952-4d60-99c3-bf14c0719d57)

<br>

## Logical Modeling
```
Employee (Employee_ID, Employee_Name, Salary, Email, E_Phone_Num)

Travel_Agency (Travel_Agency_ID, Travel_Agency_Name, commission)

TA_Phone (Travel_Agency_ID, T_Phone_Num)
Foreign key (Travel_Agency_ID) references Travel_Agency(Travel_Agency_ID)

TA_Target (Travel_Agency_ID, Target)
Foreign key (Travel_Agency_ID) references Travel_Agency(Travel_Agency_ID)

Package (Package_id, Price, Country, City, Travel_Agency_ID)
Foreign key (Travel_Agency_ID) references Travel_Agency(Travel_Agency_ID)

Wedding_Company(Wedding_Company_Id, WCompany_name, address, commission)

WC_Phone(Wedding_Company_Id, W_Phone_Num)
Foreign key (Wedding_Company_Id) references Wedding_Company(Wedding_Company_Id)

Wedding_Hall(Hall_Id, Wedding_Company_Id, Acceptable_num, Hall_Name, Price)
Foreign key (Wedding_Company_Id) references Wedding_Company(Wedding_Company_Id)

Rental_Company(Rental_Company_Id, Rental_Company_Name, Price, Commission, Address)

RC_Phone(Rental_Company_Id, R_Phone_Num)
Foreign key (Rental_Company_Id) references Rental_Company(Rental_Company_Id)

Studio(Rc_Id, Theme)
Foreign key (Rc_Id) references Rental_Company(Rental_Company_Id)

Dress(Rc_Id, Dress_Id, Suit_Id)
Foreign key (Rc_Id) references Rental_Company(Rental_Company_Id)

MakeUp(Rc_Id, Makeup_Designer, Hair_Designer)
Foreign key (Rc_Id) references Rental_Company(Rental_Company_Id)

Customer (Customer_Id, FName, LName, Gender, Age, Budget, C_Phone_Num, Employee_Id, Package_Id, Hall_Id, Date_Of_Wedding)
Foreign key (Employee_Id) references Employee(Employee_Id)
Foreign key (Package_Id) references Package(Package_Id)
Foreign key (Hall_Id) references Wedding_Hall(Wedding_Hall_Id)

Review (Customer_Id, Review_Num, Rating)
Foreign key (Customer_Id) references Customer(Customer_Id)

Rental_Customer(Customer_Id, Rental_Company_Id)
Foreign key (Customer_Id) references Customer(Customer_Id)
Foreign key (Rental_Company_Id) references Rental_Company(Rental_Company_Id)
```
