## Lambda

### 이슈

1. 람다가 실행 안되어 cloudwatch를 살펴보면 `memory` 문제 혹은 `timeout`이 나는 경우가 있다.
    - 구성에서 `메모리`와 `제한 시간`을 설정하여 해결 가능

## Lambda@edge

### IAM

1. IAM 정책 설정

```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "VisualEditor0",
            "Effect": "Allow",
            "Action": [
                "iam:CreateServiceLinkedRole",
                "lambda:GetFunction",
                "lambda:EnableReplication",
                "cloudfront:UpdateDistribution",
                "s3:GetObject",
                "logs:CreateLogGroup",
                "logs:CreateLogStream",
                "logs:PutLogEvents",
                "logs:DescribeLogStreams"
            ],
            "Resource": "*"
        }
    ]
}
```

2. IAM 역할 생성 및 정책 연결

- 1에서 만든 정책 연결

3. IAM 역할 신뢰관계 설정

```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "Service": [
          "edgelambda.amazonaws.com",
          "lambda.amazonaws.com"
        ]
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```

### Lambda 생성

- cloudfront는 **버지니아 북부(us-east-1)** 에서만 지원.
