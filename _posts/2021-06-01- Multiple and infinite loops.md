---
layout: single
tttle: Multiple and infinite loops  
---


this is my 12th posts.  


[문제 상황1]  
DAUM에서는 주기적으로 비밀번호를 변경하여 개인정보를 안전하게 보호하고 있습니다. ID는 ‘알파벳+숫자’ 의 조합으로, ‘kyunghee8323’과 같이 만들 수 있습니다. 새로 변경하려는 비밀번호에서 연속된 3글자가 ID에들어 있다면 그것은 사용이 허락되지 않습니다. 위에서 설명한 것과 같이 비밀번호 변경 가능 여부를 체크한 후에 비밀번호를 변경하는 프로그램을 작성하시오.  

~~~python  
id = 'kyunghee8323'
pw = input("비밀번호 입력:  ")

check = True
for i in range(len(pw)-2):
  if pw[i:i+3] in id:
    check = False
    break

if check: print('사용가능')
else: print('사용불가')
~~~  
[실행 결과1]  
비밀번호 입력:  asdfghjkl04  
사용가능  
[설멸1]  
먼저 id를 저장하고 사용자에게 pw를 입력 받은 후, pw를 3개씩 나누어서 id와 일치하는 것이 없는지 확인하였다.  



[문제상황2]  
365 자원봉사포털에서는 4월 3주 도서관에서의 주말 봉사활동지원을 받고 있습니다. 지원자의 이름과 전화 번호를 저장하여 조건에 따라 처리한 후 결과를 출력하는 프로그램을 작성하시오. 
>>> 처리조건   
① 신청기한은 정해져 있다.   
② 신청순서대로 3순위까지만 봉사활동이 확정되며 나머지는 대기자가 된다. ③ 확정자 중에 취소가 발생하면 대기자 명단의 1순위를 확장자로 대체한다. ④ 취소는 확정자 중에서만 발생한다고 가정한다.   
⑤ 다음 데이터를 이용하시오.   


~~~python
comfirm=[]
wait=[]
while True:
  val=input('(신청:1, 취소:2, 종료:3) ==> ')
  if val=='3': break

  phone=input('phone: ')
  if val=='1':
    name=input('name: ')
    if len(comfirm)<3: comfirm.append([name, phone])
    else: wait.append([name, phone])
  else:
   for i in range(len(comfirm)):
     if comfirm[i][1]==phone:
       print('{}님의 신청을 취소하였습니다.'.format(comfirm[i][0]))
       del comfirm[i]
       comfirm.append(wait[0])
       del wait[0]
     print('{}님이 신청되었습니다.'.format(comfirm[-1][0]))

print('신청자: ', comfirm)
print('대기자: ', wait)
~~~  


[실행 결과2]  
(신청:1, 취소:2, 종료:3) ==> 1  
phone: 01011112222  
name: 김형진  
신청자:  [['김형진', '01011112222']]  
대기자:  []  
(신청:1, 취소:2, 종료:3) ==> 1  
phone: 01033334444  
name: 한유림  
신청자:  [['김형진', '01011112222'], ['한유림', '01033334444']]  
대기자:  []  
(신청:1, 취소:2, 종료:3) ==> 1  
phone: 01055556666  
name: 양정식  
신청자:  [['김형진', '01011112222'], ['한유림', '01033334444'], ['양정식', '01055556666']]  
대기자:  []  
(신청:1, 취소:2, 종료:3) ==> 1  
phone: 01077778888  
name: 조재웅  
신청자:  [['김형진', '01011112222'], ['한유림', '01033334444'], ['양정식', '01055556666']]  
대기자:  [['조재웅', '01077778888']]  
(신청:1, 취소:2, 종료:3) ==> 1  
phone: 01099991234  
name: 강수진  
신청자:  [['김형진', '01011112222'], ['한유림', '01033334444'], ['양정식', '01055556666']]  
대기자:  [['조재웅', '01077778888'], ['강수진', '01099991234']]  
(신청:1, 취소:2, 종료:3) ==> 2  
phone: 01055556666  
양정식님이 신청되었습니다.  
양정식님이 신청되었습니다.  
양정식님의 신청을 취소하였습니다.  
조재웅님이 신청되었습니다.  
신청자:  [['김형진', '01011112222'], ['한유림', '01033334444'], ['조재웅', '01077778888']]  
대기자:  [['강수진', '01099991234']]  
(신청:1, 취소:2, 종료:3) ==> 3  


[설명3]  
먼저 사용자가 어던 행동을 할려고 하는지 입력받고, 전화번호와 이름을 입력 받는다. 신청자에 3명 이상이 되면 대기자로 옮기게 되고, 신청자에서 취소하는 사람이 나온다면 그 사람을 명단에ㅔ서 지우고, 대기자 중 가장 앞에있는 사람을 신청자 명단에 집어넣는다.
