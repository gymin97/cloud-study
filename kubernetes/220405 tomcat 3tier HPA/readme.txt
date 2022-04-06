was server를 tomcat으로 구성한 이미지를 사용하여 3tier를 구성한다
세션정보는 redis에 저장하도록한다
HPA를 이용한 autoscale을 사용하도록 하며, 이때 서버 부하는 ngrinder를 이용한다


DB tier
- mysql 5.7 사용
- DB name : boot_board
- DB tables : 예시 DB에서 dump받아 새로 이미지 생성하여 사용
- image tag : gymin97/msa-dev:mysql5.7_v1
- statefulset 사용

============= 이미지 생성하기 =============
# 이미지 dump 
mysqldump -u root -p boot_board > /backup/Dump.sql
# pod dump 파일 받아오기
kubectl cp mysql:/backup/Dump.sql ./Dump.sql
===========================================

WAS tier
image: gymin97/msa-dev:redis-tomcat_v2
- 404 error 방지할것 (redis, DB 생성 후 pod 생성하기)

web tier
image: gymin97/msa-dev:nginx_v1
