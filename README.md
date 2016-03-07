# ci-sts
assume roles in CI server

## staging (develop branch)

IAM user

Exec Policy
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:Get*",
        "s3:List*"
      ],
      "Resource": "*"
    }
  ]
}
```

Assume Policy
```
{
    "Version": "2012-10-17",
    "Statement": [
        {
            "Sid": "Stmt1457362449000",
            "Effect": "Allow",
            "Action": [
                "sts:AssumeRole"
            ],
            "Resource": [
                "arn:aws:iam::908699337798:role/role-to-be-assumed"
            ]
        }
    ]
}
```

## production account (develop branch)

IAM role

Exec Policy
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Action": [
        "s3:Get*",
        "s3:List*"
      ],
      "Resource": "*"
    }
  ]
}
```

Trust Relationship
```
{
  "Version": "2012-10-17",
  "Statement": [
    {
      "Effect": "Allow",
      "Principal": {
        "AWS": "arn:aws:iam::713403314913:root"
      },
      "Action": "sts:AssumeRole"
    }
  ]
}
```
```
