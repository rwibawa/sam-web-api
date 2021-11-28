```sh
$ sam init \
--location gh:aws-samples/cookiecutter-aws-sam-dynamodb-python \
--no-input

$ sam init \
--location https://github.com/aws-samples/cookiecutter-aws-sam-s3-rekognition-dynamodb-python \
--no-input
```

sam init --location gh:aws-samples/cookiecutter-aws-sam-dynamodb-python --no-input

sam init --location https://github.com/aws-samples/cookiecutter-aws-sam-s3-rekognition-dynamodb-python --no-input

sam package --template-file template.yaml --output-template-file packaged.yaml --s3-bucket sam.hello
sam deploy --template-file packaged.yaml --stack-name aws-sam-ocr --capabilities CAPABILITY_IAM --region us-west-1