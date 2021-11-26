주의) 삭제후 다시 할때는 hostpath 의 디렉토리이름을
변경해서 해야 제대로 테스트할수 있습니다.
또는 persistent volume reclaim 정책을 변경해서
하는 방법도 있습니다.


* secret obeject 생성 명령어
-  kubectl create secret generic db-pw --from literal password=mypass --from-literal user_password=userpass


