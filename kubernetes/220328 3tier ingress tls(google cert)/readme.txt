각 벤더의 nfs와 db는 사설 ip로만 이루어져 외부접속시 bastion host로만 접속해야하며

3tier환경에서 web,was는 gcp vpc환경에 구축하고 DB는 EC2의 DB에 구축한다(VPN으로 연결되어 있으니 사설ip로 연결 가능)

또, web접속시 http 접속시 https로 리다이렉션 하도록 구성하여라

tls인증서는 google cert를 사용한다