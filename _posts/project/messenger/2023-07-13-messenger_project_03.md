---
title: RabbitMQ 사용법
date: 2023-07-13 02:15
categories: [project, messenger]
tags: [rabbitmq]
# 기타 더 사용하는거 있으면 추가해놓기
---

# RabbitMQ Exchange 사용하기

이전 포스팅에서 각 속성값? 등을 살펴 봤는데 그중 Exchange가 동작에 필요한 요소를 조금 더 알아보려 합니다.

## 1. Direct

routing key 값과 정확히 일치하는 queue에 메세지를 보내는 타입.
![rabbitmq_direct_routing_image](/assets/img/message_project/rabbitmq_direct_routing_image.png){: border-radius="5px" }

해당 queue의 routing key가 일치하는 queue에 모두 보내게 된다.

추가로 exchange를 정의하지 않았을때는 (string 빈값으로 했을때) 기본적으로 routing key를 queue의 이름으로 사용하는 direct 타입이 된다.

## 2. Fanout

routing key와 상관없이 해당 exchange에 바인딩된 모든 queue에게 메세지를 보낸다.
예제 구동시에 모든 queue에 전해지지 않길레 당황 했는데 위에 언급한것 처럼 해당 exchange에 바인딩이 된
queue에 한에서 모두 보내지게 되는걸 주의하면 되겠다.

## 3. topic

routing key를 패턴으로 사용해서 메세지를 보내게 된다. 각 주제를 '.'으로 구분하여 사용 할 수 있고 특수키?로 아래를 사용할 수 있다.

- `*`로 정확히 한단어를 대체
- `#` 0개 이상의 단어를 대체

![rabbitmq_topic_routing_image](/assets/img/message_project/rabbitmq_topic_routing_image.png)

특수 키는 queue를 exchange에 바인딩시에 사용하면 된다. (반대로 publish때 routing key에 사용해보니 안되더군용...)

## 4. headers

headers에 있는 정보를 기반으로 메세지를 보낸다.
routing key는 무시하고 headers에 있는 정보만으로 보내게 된다.

header는 key value 값으로 되어있는 맵같은 구조로 되어있다. 이때 "x-match"라는 키값에 따라 "any"로 설정시에는 매칭되는 인수가 하나 이상시에 "all"로 설정시에는 모든 인수가 일치해야 해당 queue로 메세지가 보내지게 된다.
