was server를 tomcat으로 구성한 이미지를 사용하여 3tier를 구성한다
세션정보는 redis에 저장하도록한다


DB tier
image: hifrodo/msa-devops:mysql_1
DB name: boot_board

WAS tier
image: gymin97/msa-dev:redis-tomcat_v2

web tier
image: gymin97/msa-dev:nginx_v1
