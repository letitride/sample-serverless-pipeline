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

codepipeline用role & policy
```
$ aws iam create-role --role-name code-pipeline-role --assume-role-policy-document file://codepipeline-role.json
```
```
$ aws iam put-role-policy \
--role-name code-pipeline-role \
--policy-name pipeline-service \
--policy-document file://codepipeline-permission.json
```

codebuilf用role & policy
```
$ aws iam create-role --role-name codebuild-role --assume-role-policy-document file://codebuild-role.json
```
```
$ aws iam put-role-policy \
--role-name codebuild-role \
--policy-name codebuild-service \
--policy-document file://codebuild-permission.json
```

codebuild projectの作成
```
$ aws codebuild create-project --cli-input-json file://project.json
```

codepipelineの作成
```
$ aws codepipeline create-pipeline --cli-input-json file://pipeline.json
```

pipelineの実行
```
$ aws codepipeline start-pipeline-execution --name serverless-pipeline

$ aws codepipeline get-pipeline-state --name serverless-pipeline
```