cloudformation labda実行用ロールの作成
```
$ aws iam create-role --role-name cloudformation-lambda-execution-role \
--assume-role-policy-document file://trustpolicy.json
```

```
$ aws s3 mb s3://codepipeline-letitride--region ap-northeast-1
```
```
$ aws iam put-role-policy \
--role-name cloudformation-lambda-execution-role \
--policy-name cloudformation-execution \
--policy-document file://permission.json
```


```
$ aws iam create-role --role-name code-pipeline-role --assume-role-policy-document file://codepipeline-role.json
```
```
$ aws iam put-role-policy \
--role-name code-pipeline-role \
--policy-name pipeline-service \
--policy-document file://codepipeline-permission.json
```

```
$ aws iam create-role --role-name codebuild-role --assume-role-policy-document file://codebuild-role.json
```
```
$ aws iam put-role-policy \
--role-name codebuild-role \
--policy-name codebuild-service \
--policy-document file://codebuild-permission.json
```
