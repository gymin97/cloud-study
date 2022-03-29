작업 내용

- GKE에서 3tier를 구성하며 nfs-server(Web log DB)는 다른 VPC를 만들어 그곳에 프라이빗 인스턴스로 구성한다
- nfs-server와 nginx는 vpc peering 을 맺어 ig 통신을 할때보다 저렴하고 안전하게 통신하도록 한다
- nfs server를 PV, PVC를 이용하여 연결한다
- 사용자가 http로 접속했을때 https로 redirection 가능하도록 한다 (보안)
- 이때 인증서는 google cert를 사용하지 않고 사설인증서를 사용한다
- nginx log를 5분 간격으로 backup file로 저장한다
- backup file은 object storage와 연동하여 자동으로 이곳에 저장되도록한다 (linux crontab 사용)