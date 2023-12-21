# AWS Cheat Sheet
By Christopher M. Judd (javajudd@gmail.com)

## Resources
* https://awscli.amazonaws.com/v2/documentation/api/latest/reference/index.html

## IAM

### List Users
```
aws iam list-users
aws iam list-access-keys --user-name <user name>
```
### Delete Users
```
aws iam delete-login-profile --user-name <user name>
aws iam delete-access-key --user-name <user name> --access-key-id <access key id>
aws iam remove-user-from-group --group-name <groups name> --user-name <user name>
aws iam delete-user --user-name <user name>
```

## S3

### Remove/Remove Bucket
```
aws s3 rb <S3 URI>
```

## CodeBuild

## List CodeBuilds
```
 aws codebuild list-builds
```

## Delete CodeBuilds
```
aws codebuild batch-delete-builds --ids "build name" "build name"
```

## List CodeBuild Projects
```
aws codebuild list-projects
```

## Delete CodeBuild Projects
```
aws codebuild delete-projects --name "project name"
```