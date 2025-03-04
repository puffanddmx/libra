# Facebook Blockchain Libra
- client 파일 : client.tar.gz 로 변환한다음 tar 압축 풀면 client 실행파일 추출 된다.
- libra language : RUST (grpc, proto buf 사용)
- RPC PORT : 8000
- trusted_peers.config.toml 파일 : facebook node testnet node 접속을 위해서는 해당 인증 키가 있어야 facebook node 에 접속 가능
- 코인 자릿수 : 1 Libra == 10^6 (transaction 조회시 6자리로 raw로 조회되며 단순 잔액 조회시 Libra로 조회됨)
- client.mnemonic 파일 : client testnet 실행시 같은 경로에 mnemonic 파일 생성. (기존 child index 사용(즉 기존에 만들어 놓은 주소를 다시 복원 하기 위해서는)을 위해서는 client 실행시마다 account create 하게 되면 다시 사용 가능(밸런스 저장됨)). 이 파일 분실 주의 필요
- facebook foundation testnet dns : ac.testnet.libra.org (3.218.209.205, 18.204.110.176, 52.55.128.16, 3.218.35.111, 34.225.209.173)
- id (child index) : 각 주소 해당 하는 index, sequence number : 각 주소 (id) 해당하는 transaction index 정보
- client testnet 실행 (CLI) : ./client --host ac.testnet.libra.org --port 8000 -s ./trusted_peers.config.toml (해당 시간에 접속을 못하면       Deadline Exceeded 메시지가 뜬다)
- 주소 생성 : $ account create
- 주소 리스트 조회 :$ account list
- 잔액 추가 발행 : $ account mint 0 10 (id : 0, amount : 10  (10 Libra= 10^7)을 추가 발행한다)
- 전송 : $ transfer 0 1 10 ( id : 0, id : 1, amount : 10을 보낸다 (10 Libra= 10^7))
- 잔액 조회 : $ query balance 0 (이 예제에서는 index가 0인 주소 잔액 조회),$ query balance affa6462fa7b3d18f4e45eedc04112d8ad8e2b0c46f88850ad02c4fb4c370ba7 (주소로 조회시 0x를 넣지 않는다)
- 특정 계정 최신 tx 조회 : $ query account_state 0 (이 예제에서는 index가 0인 주소 잔액 조회)
- 특정 계정 특정 tx 조회 : $ query txn_acc_seq 0 1 true (id : 0, tx sequence number : 1을 조회. true를 조회하게 되면 event상세 조회 가능)

- libra 참고 사이트 : https://developers.libra.org/docs/welcome-to-libra
- rust 참고 사이트 : https://doc.rust-lang.org/std/
