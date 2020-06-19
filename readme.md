cloudformation labda実行用ロールの作成
```
$ aws iam create-role --role-name cloudformation-lambda-execution-role \
--assume-role-policy-document file://trustpolicy.json
```