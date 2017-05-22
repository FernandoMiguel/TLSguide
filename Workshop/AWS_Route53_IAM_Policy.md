## Allow Changes to Resource Record Sets in a Specified Hosted Zone

- http://docs.aws.amazon.com/Route53/latest/DeveloperGuide/access-control-managing-permissions.html
```json
{
   "Version": "2012-10-17",
   "Statement": [
      {
         "Effect": "Allow",
         "Action": [
            "route53:ListHostedZones"
         ],
         "Resource": "*"
      },
      {
         "Effect": "Allow",
         "Action": [
            "route53:GetHostedZone"
         ],
         "Resource": "arn:aws:route53:::hostedzone/hosted zone id"
      },
      {
         "Effect": "Allow",
         "Action": [
            "route53:ListResourceRecordSets"
         ],
         "Resource": "arn:aws:route53:::hostedzone/hosted zone id"
      },
      {
         "Effect": "Allow",
         "Action": [
            "route53:ChangeResourceRecordSets"
         ],
         "Resource": "arn:aws:route53:::hostedzone/hosted zone id"
      }
   ]
}
```
