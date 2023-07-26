---
title: RabbitMQ 사용법
date: 2023-07-06 16:00
categories: [project, messenger]
tags: [rabbitmq]
# 기타 더 사용하는거 있으면 추가해놓기
---

# RabbitMQ?

메세지 큐 시스템?을 구현한 메세지 브로커?이다. 메신저 기능을 구현하려면 어떤 기술을 써야할까 찾아보다 소켓통신보다
메시지 큐같은 방식이면 더 수월하지 않을까 해서 시도해보려 찾아보았다.
그중 많이 사용하는 message broker가 RabbitMQ.
Queue 같은 형식이 분산 처리에 사용하는 경우가 많았는데 pub - sub 방식으로도 사용할 수 있고 여러 기능 및 언어를 지원해서
사용해보기로 했다.

# AMQP

Advanced Message Queuing Protocol로 MQ시스템에서 사용하는 프로토콜 정로도만... 이해를 했습니다.
이 프로토콜 기반으로 만들었다면 RabbitMQ외 다른 message broker를 사용해도 작동을 하는것일까요?... 그건 잘 모르겠습니다.

이 Queue시스템 구조는 대략 아래와 같습니다.

![hello-world-example-image](/assets/img/message_project/hello-world-example-routing.png)
출처[RabbitMQ홈페이지 문서](https://www.rabbitmq.com/img/tutorials/intro/hello-world-example-routing.png)

## Exchange

publisher가 메세지를 publish하면 중간에 exchange에 따라 queue에 분배?하는 작업을 합니다.(routing?)

### Exchange Type

이 routing은 타입에 따라 여러방식으로 동작합니다. 간단하게만 적으면

- direct : routing key 와 정확히 일치하는 queue에만 message routing
- fanout : routung key를 무시하고 message routing
- topic : routing key를 topic 형식으로? 패턴일 일치하면 message routing
- header : rounting key를 무시하고 header에 key-value 형식으로 패턴일치시 message routing

이 외에 속성으로는

- durable : 재시작시에도 남아있는지 여부
- autoDelete : 마지막 큐와 연결이 끊어질떄 삭제 여부
- internal : exchange에 publish 받지 않음

번역기 힘이라 사용하면서 다른 점이 있거나 하는것을 찾아봐야겠다.

### Binding

Queue가 이 Exchange에 규칙에 따르려면 만들어 놓고 연결해주어야 한다. 이를 Binding이라 하는거 같다.
예를 들면 fanout 타입이라고 선언해놓은 Exchange로 publish해도 binding된 아무리 다른 queue가 있어도 바인딩된 큐가 아니면
메시지를 보내지 않는다.

### Queue

메세지가 consumer에게 가기전 저장되는 곳이다. queue의 동작 방식데로 FIFO 방식으로 동작한다.

속성

- Name : 큐이름으로 header타임 exchange를 제외한 라우팅 키로 사용한다.
- Durable : broker 서버 재시작시 삭제 유무
- Exclisue : 하나의 연결만 사용하고 연결이 닫혔을때 삭제여부
- Auto-Delete : 마지막 남은 consumer 구독이 끊길때 삭제 여부

---

튜토리얼 작동시에 접해보는 옵션들을 위주로 간단히 정리 해보았습니다. RabbitMQ라기 보단 AMQP요약?정도 이지만... 아무튼 필요한 옵션들은 다시 찾아봐야 하겠습니다. 가야할 길이 멀다.
